---
title: catalog.object_parameters (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: d7b04903-2d61-4159-9456-475942d1f732
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 907678a77620f432411b1714ec7a1603e147129e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104817"
---
# <a name="catalogobjectparameters-ssisdb-database"></a>catalog.object_parameters (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les paramètres de tous les packages et projets dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|parameter_id|**bigint**|Identificateur (ID) unique du paramètre.|  
|project_id|**bigint**|ID unique du projet.|  
|object_type|**smallint**|Type de paramètre. La valeur est `20` pour un paramètre du projet et `30` pour un paramètre du package.|  
|object_name|**sysname**|Nom du projet ou package correspondant.|  
|parameter_name|**sysname(nvarchar(128))**|Nom du paramètre.|  
|data_type|**nvarchar(128)**|Type de données du paramètre.|  
|required|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est obligatoire pour démarrer l'exécution. Lorsque la valeur est `0`, la valeur de paramètre n'est pas obligatoire pour démarrer l'exécution.|  
|sensible|**bit**|Lorsque la valeur est `1`, la valeur de paramètre est sensible. Lorsque la valeur est `0`, la valeur de paramètre n'est pas sensible.|  
|description|**nvarchar(1024)**|Description facultative du package.|  
|design_default_value|**sql_variant**|Valeur par défaut du paramètre qui a été affecté pendant la conception du projet ou du package.|  
|default_value|**sql_variant**|Valeur par défaut utilisée actuellement sur le serveur.|  
|value_type|**char(1)**|Indique la valeur de type de paramètre. Ce champ affiche `V` quand parameter_value est une valeur littérale et `R` quand la valeur est affectée en référençant une variable d’environnement.|  
|value_set|**bit**|Lorsque la valeur est `1`, la valeur de paramètre a été affectée. Lorsque la valeur est `0`, la valeur de paramètre n'a pas été affectée.|  
|referenced_variable_name|**nvarchar(128)**|Nom de la variable d'environnement affectée à la valeur du paramètre. La valeur par défaut est **NULL**.|  
|validation_status|**char(1)**|Identifié à titre d'information uniquement. Inutilisé dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|last_validation_time|**datetimeoffset(7)**|Identifié à titre d'information uniquement. Inutilisé dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Autorisations  
 Pour consulter des lignes dans cette vue, vous devez avoir l'une des autorisations suivantes :  
  
-   Autorisation READ sur le projet  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
 La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
