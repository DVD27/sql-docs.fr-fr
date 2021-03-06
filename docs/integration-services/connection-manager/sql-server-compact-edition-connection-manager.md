---
title: Gestionnaire de connexions de SQL Server Compact Edition | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sqlmobileconnection.connection.f1
- sql13.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 1b723984f03c67d7468c7531a8c67c9f46cb2116
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904231"
---
# <a name="sql-server-compact-edition-connection-manager"></a>Gestionnaire de connexions de SQL Server Compact Edition

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact permet à un package de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise ce gestionnaire de connexions pour charger des données dans une table d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, vous devez exécuter les packages qui se connectent à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact en mode 32 bits. Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact utilisé par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour se connecter à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact n’est disponible qu’en version 32 bits.  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>Configuration du gestionnaire de connexions SQL Server Compact Edition  
 Quand vous ajoutez un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui est résolu en connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connexions** du package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a la valeur **SQLMOBILE**.  
  
 Vous pouvez configurer le gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion qui indique l’emplacement de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
-   Spécifiez un mot de passe pour une base de données protégée par mot de passe.  
  
-   Spécifiez le serveur où est stockée la base de données.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="sql-server-compact-edition-connection-manager-editor-connection-page"></a>Éditeur du gestionnaire de connexions SQL Server Compact Edition (page Connexion)
  La boîte de dialogue **Éditeur du gestionnaire de connexions SQL Server Compact Edition** permet de spécifier les propriétés permettant de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Pour en savoir plus sur le gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Edition, consultez [Éditeur du gestionnaire de connexions SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
### <a name="options"></a>Options  
 **Nom et chemin d'accès au fichier de la base de données**  
 Entrez le chemin et le nom de fichier de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Parcourir**  
 Recherchez le fichier de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact souhaité à l’aide de la boîte de dialogue **Sélectionner la base de données SQL Server Compact Edition** .  
  
 **Mot de passe de la base de données**  
 Entrez le mot de passe pour la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
## <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>Éditeur du gestionnaire de connexions SQL Server Compact Edition (page Tout)
  La boîte de dialogue **Éditeur du gestionnaire de connexions SQL Server Compact Edition** permet de spécifier les propriétés permettant de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Pour en savoir plus sur le gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Edition, consultez [Éditeur du gestionnaire de connexions SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
### <a name="options"></a>Options  
 **AutoShrink Threshold**  
 Spécifiez le pourcentage d’espace libre autorisé dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact avant que le processus de réduction automatique soit lancé.  
  
 **Escalade de verrous par défaut**  
 Spécifiez le nombre de verrous de base de données acquis par la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact avant qu’elle tente de promouvoir les verrous.  
  
 **Default Lock Timeout**  
 Spécifiez l'intervalle par défaut, en millisecondes, d'attente d'un verrou par une instruction.  
  
 **Flush Interval**  
 Spécifiez l'intervalle, en secondes, s'écoulant entre les vidages de données de transactions validées sur le disque.  
  
 **Identificateur de paramètres régionaux**  
 Spécifiez l’identificateur de paramètres régionaux (LCID) de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Max Buffer Size**  
 Spécifiez la quantité maximale de mémoire (en Ko) utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact avant d’effectuer un vidage des données sur le disque.  
  
 **Max Database Size**  
 Spécifiez la taille maximale (en Mo) de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Mode**  
 Spécifiez le mode de fichier dans lequel ouvrir la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. La valeur par défaut de cette propriété est **Read Write**.  
  
 L'option Mode comporte quatre valeurs, qui sont décrites dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Lecture seule**|Offre un accès en lecture seule à la base de données.|  
|**Read Write**|Autorise l'accès en lecture et écriture à la base de données.|  
|**Exclusive**|Offre un accès exclusif à la base de données.|  
|**Shared Read**|Indique que plusieurs utilisateurs peuvent lire la base de données simultanément.|  
  
 **Persist Security Info**  
 Indique si des informations de sécurité sont retournées dans la chaîne de connexion. La valeur par défaut de cette option est **False**.  
  
 **Temp File Directory**  
 Spécifiez l’emplacement du fichier de base de données temporaire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Source de données**  
 Spécifiez le nom de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Mot de passe**  
 Entrez le mot de passe pour la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
