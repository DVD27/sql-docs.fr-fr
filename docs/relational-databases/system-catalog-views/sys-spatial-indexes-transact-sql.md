---
title: sys. spatial_indexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.spatial_indexes_TSQL
- spatial_indexes
- spatial_indexes_TSQL
- sys.spatial_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_indexes catalog view
ms.assetid: 40e967d5-2e8d-45af-bf5e-5251493cf7cb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a5264661a94b4802d6f06ab1af8ae74436b63b09
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833975"
---
# <a name="sysspatial_indexes-transact-sql"></a>sys.spatial_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Représente les informations d'index principal des index spatiaux.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|\<colonnes héritées>||Hérite des colonnes de [sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|spatial_index_type|**tinyint**|Type d'index spatial :<br /><br /> 1 = Index spatial géométrique<br /><br /> 2 = Index spatial géographique|  
|spatial_index_type_desc|**nvarchar(60)**|Description du type d'index spatial :<br /><br /> GEOMETRY = Index spatial géométrique<br /><br /> GEOGRAPHY = Index spatial géographique|  
|tessellation_scheme|**sysname**|Nom du schéma de pavage :<br /><br /> GEOMETRY_GRID, GEOMETRY_AUTO_GRID,<br /><br /> GEOGRAPHY_GRID, GEOGRAPHY_AUTO_GRID<br /><br /> Remarque : pour plus d’informations sur les schémas de pavage, consultez [vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md).|  
|\<colonnes héritées>||Hérite des colonnes de [sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).<br /><br /> Les colonnes héritées has_filter et filter_definition apparaissent après les colonnes qui sont spécifiques aux index spatiaux.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. spatial_index_tessellations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-index-tessellations-transact-sql.md)   
 [sys. Indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys. index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Vue d'ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)  
  
  
