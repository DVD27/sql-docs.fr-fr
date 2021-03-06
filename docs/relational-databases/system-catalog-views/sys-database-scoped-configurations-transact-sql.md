---
title: sys.database_scoped_configurations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3439419bd3877b8ab7a951df58585703f169ee4f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079452"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contient une ligne par configuration. 
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**Int**|ID de l’option de configuration.|  
|**name**|**nvarchar(60)**|Le nom de l’option de configuration. Pour plus d’informations sur les configurations possibles, consultez [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**value**|**sqlvariant**|La valeur définie pour cette option de configuration pour le réplica principal.|  
|**value_for_secondary**|**sqlvariant**|La valeur définie pour cette option de configuration pour les réplicas secondaires.|  
|**is_value_default**|**bit** |Spécifie si la valeur définie est la valeur par défaut.|
  
##  <a name="Permissions"></a> Autorisations  
Nécessite l'appartenance au rôle **public** .  
  
## <a name="remarks"></a>Notes  
Lorsque la valeur NULL est retournée comme valeur pour **value_for_secondary**, cela signifie que la base de données secondaire est défini dans la région primaire.  
 
Les paramètres configurés au niveau de la base de données sont reportés avec la base de données. Cela signifie que lorsqu’une base de données est restaurée ou jointe, les paramètres de configuration existants sont conservés.
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
