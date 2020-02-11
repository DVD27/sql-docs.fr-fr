---
title: Restrictions du modèle de programmation de l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: c019b50f896109a699869d748d8eef20b57d6edb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70212367"
---
# <a name="clr-integration-programming-model-restrictions"></a>Restrictions du modèle de programmation de l'intégration du CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Lorsque vous générez une procédure stockée managée ou un autre objet de base de données managé, vous [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] devez prendre en compte certaines vérifications de code effectuées. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]effectue des vérifications sur l’assembly de code managé lorsqu’il est inscrit pour la première fois dans la base de données, à l’aide de l’instruction **Create Assembly** et également au moment de l’exécution. Le code managé est également vérifié pendant l'exécution, car dans un assembly il peut y avoir des chemins d'accès de code qui peuvent ne jamais être atteints pendant l'exécution.  Cela fournit la souplesse nécessaire pour inscrire notamment des assemblys tiers, afin qu'un assembly ne soit pas bloqué là où il y a du code « potentiellement dangereux » conçu pour s'exécuter dans un environnement client, mais ne soit jamais exécuté dans le CLR hébergé. Les exigences que le code managé doit respecter varient selon que l’assembly est inscrit comme **sécurisé**, **EXTERNAL_ACCESS**ou **non sécurisé,** sûr étant le plus strict **possible** et est répertorié ci-dessous.  
  
 En plus des restrictions imposées sur les assemblys de code managé, des autorisations de sécurité du code sont également accordées. Le Common Language Runtime (CLR) prend en charge un modèle de sécurité appelé sécurité d'accès du code pour le code managé. Dans ce modèle, les autorisations sont accordées aux assemblys selon l'identité du code. Les assemblys **Safe**, **EXTERNAL_ACCESS**et **unsafe** ont des autorisations cas différentes. Pour plus d’informations, consultez [sécurité d’accès du code d’intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Contrôles CREATE ASSEMBLY  
 Lors de l’exécution de l’instruction **Create Assembly** , les vérifications suivantes sont effectuées pour chaque niveau de sécurité.  En cas d’échec de la vérification, l’opération **Create Assembly** échoue avec un message d’erreur.  
  
### <a name="global-any-security-level"></a>Global (tout niveau de sécurité)  
 Tous les assemblys référencés doivent satisfaire un ou plusieurs des critères suivants :  
  
-   L'assembly est déjà inscrit dans la base de données.  
  
-   L'assembly est l'un des assemblys pris en charge. Pour plus d’informations, consultez [.NET Framework les bibliothèques prises en charge](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Vous utilisez **créer un assembly à partir de**_\<l’emplacement>,_ et tous les assemblys référencés et leurs dépendances sont disponibles dans * \<emplacement>*.  
  
-   Vous utilisez **Create assembly à partir d'**_\<octets... >,_ et toutes les références sont spécifiées via des octets séparés par des espaces.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Tous les assemblys **EXTERNAL_ACCESS** doivent répondre aux critères suivants :  
  
-   Les champs statiques ne sont pas utilisés pour stocker des informations. Les champs statiques en lecture seule sont autorisés.  
  
-   Le test PEVerify est réussi. L'outil PEVerify (peverify.exe), qui vérifie que le code MSIL et les métadonnées associées satisfont les spécifications de sécurité de type, est fourni dans le Kit de développement SDK .NET Framework.  
  
-   La synchronisation, par exemple avec la classe **SynchronizationAttribute** , n’est pas utilisée.  
  
-   Les méthodes finaliseurs ne sont pas utilisées.  
  
 Les attributs personnalisés suivants ne sont pas autorisés dans les assemblys **EXTERNAL_ACCESS** :  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   Toutes les **EXTERNAL_ACCESS** conditions d’assembly sont vérifiées.  
  
## <a name="runtime-checks"></a>Contrôles d'exécution  
 Pendant l'exécution, les conditions suivantes sont vérifiées pour l'assembly de code. Si l'une de ces conditions est remplie, le code managé n'est pas autorisé à s'exécuter et une exception est levée.  
  
### <a name="unsafe"></a>UNSAFE  
 Le chargement d’un assembly, soit explicitement en appelant la méthode **System. Reflection. assembly. Load ()** à partir d’un tableau d’octets, soit implicitement à l’aide de l’espace de noms **Reflection. Emit** -n’est pas autorisé.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Toutes les conditions **non sûres** sont vérifiées.  
  
 Tous les types et méthodes annotés avec les valeurs d'attribut de protection de l'hôte suivantes dans la liste d'assemblys prise en charge sont interdits.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   Interface utilisateur  
  
 Pour plus d’informations sur hPa et pour obtenir la liste des types et des membres non autorisés dans les assemblys pris en charge, consultez attributs de protection de l' [hôte et programmation](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)de l’intégration du CLR.  
  
### <a name="safe"></a>SAFE  
 Toutes les conditions de **EXTERNAL_ACCESS** sont vérifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèques de .NET Framework prises en charge](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [Sécurité d’accès du code d’intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Attributs de protection de l’hôte et programmation de l’intégration du CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Création d'un assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
