---
title: Sys.dm_xe_object_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_object_columns
- sys.dm_xe_object_columns_TSQL
- dm_xe_object_columns_TSQL
- dm_xe_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_object_columns dynamic management view
- extended events [SQL Server], views
ms.assetid: d96a14f3-4284-45ff-b1fe-4858e540a013
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b44824310637b279388ea367cd4ab1d07401d1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090286"
---
# <a name="sysdmxeobjectcolumns-transact-sql"></a>sys.dm_xe_object_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les informations de schéma pour tous les objets.  
  
> [!NOTE]  
>  Les objets événement exposent des schémas fixes pour les données en lecture seule et les données en lecture-écriture.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar (256)**|Nom de la colonne. nom est unique au sein de l’objet. N'accepte pas la valeur NULL.|  
|column_id|**Int**|Identificateur de la colonne. column_id est unique au sein de l’objet en cas d’utilisation avec column_type. N'accepte pas la valeur NULL.|  
|object_name|**nvarchar (256)**|Nom de l'objet auquel appartient cette colonne. Il existe une relation plusieurs-à-un avec sys.dm_xe_objects.id. N'accepte pas la valeur NULL.|  
|object_package_guid|**uniqueidentifier**|GUID du package qui contient l'objet. N'accepte pas la valeur NULL.|  
|type_name|**nvarchar (256)**|Nom du type pour cette colonne. N'accepte pas la valeur NULL.|  
|type_package_guid|**uniqueidentifier**|GUID du package qui contient le type de données de la colonne. N'accepte pas la valeur NULL.|  
|column_type|**nvarchar(60)**|Indique comment cette colonne est utilisée. N'accepte pas la valeur NULL. COLUMN_TYPE peut être une des opérations suivantes :<br /><br /> readonly. La colonne contient une valeur statique qui ne peut pas être modifiée.<br /><br /> data. La colonne contient des données d'exécution exposées par l'objet.<br /><br /> customizable. La colonne contient une valeur qui peut être modifiée.<br /><br /> Remarque : Modification de cette valeur peut modifier le comportement de l’objet.|  
|column_value|**nvarchar (256)**|Affiche des valeurs statiques associées à la colonne d'objets. Autorise la valeur NULL.|  
|Fonctionnalités|**Int**|Bitmap décrivant les fonctionnalités de la colonne. Autorise la valeur NULL.|  
|capabilities_desc|**nvarchar (256)**|Description des fonctionnalités de cette colonne d'objets. Cette valeur peut être une des opérations suivantes :<br /><br /> Obligatoire. La valeur doit être affectée lors de la liaison de l'objet parent à une session d'événements.<br /><br /> Autorise la valeur NULL.|  
|description|**nvarchar(3072)**|Description de cette colonne d'objets. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|From|Pour|Relation|  
|----------|--------|------------------|  
|sys.dm_xe_object_columns.object_name, sys.dm_xe_object_columns.object_package_guid|sys.dm_xe_objects.name,<br /><br /> sys.dm_xe_objects.package_guid|Plusieurs-à-un|  
|sys.dm_xe_object_columns.type_name<br /><br /> sys.dm_xe_object_columns.type_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

