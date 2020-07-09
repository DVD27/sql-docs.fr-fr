---
title: catalog.clear_object_parameter_value (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: dcbbb714-a051-4805-9e2b-2c2fb647c890
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b980121d808fc51a251af802314f3ad719fe16b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749724"
---
# <a name="catalogclear_object_parameter_value-ssisdb-database"></a>catalog.clear_object_parameter_value (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Efface la valeur d'un paramètre pour un projet ou un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] existant stocké sur le serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.clear_object_parameter [ @folder_name = ] folder_name   
    , [ @project_name = ] project_name   
    , [ @object_type = ] object_type   
    , [ @object_name = ] object_name   
    , [ @parameter_ name = ] parameter_name  
```  
  
## <a name="arguments"></a>Arguments  
 [ \@folder_name = ] *folder_name*  
 Nom du dossier qui contient le projet. *folder_name* est de type **nvarchar(128)** .  
  
 [ \@project_name = ] *project_name*  
 Nom de projet. *project_name* est de type **nvarchar(128)** .  
  
 [ \@object_type = ] *object_type*  
 Type de l'objet. Les valeurs valides incluent `20` pour un projet et `30` pour un package. *object_type* est de type **smallInt**.  
  
 [ \@ object _name = ] *object _name*  
 Nom du package. *object _name* est de type **nvarchar(260)** .  
  
 [ \@parameter_ name = ] *parameter_name*  
 Le nom du paramètre. *parameter_ name* est de type **nvarchar(128)** .  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur le projet  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur de procédure stockée clear_object_parameter :  
  
-   Un type d'objet non valide est spécifié ou le nom d'objet est introuvable dans le projet.  
  
-   Le projet n'existe pas, n'est pas accessible ou n'est pas valide.  
  
-   Un nom de paramètre non valide est spécifié.  
  
-   L’utilisateur n’a pas les autorisations appropriées.  
  
  
