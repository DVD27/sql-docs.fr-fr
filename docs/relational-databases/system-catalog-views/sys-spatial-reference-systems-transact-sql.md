---
title: sys. spatial_reference_systems (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e6ffd36516fecba70618c79a7bbd0415f6bb2cb3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68073248"
---
# <a name="sysspatial_reference_systems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Répertorie les systèmes de référence spatiale (SRID) pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|SRID pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar(128)**|Autorité du SRID.|  
|authorized_spatial_reference_id|**int**|SRID donné par l’autorité nommée dans **authority_name**.|  
|well_known_text|**nvarchar(4000)**|Représentation WKT du SRID.|  
|unit_of_measure|**nvarchar(128)**|Nom de l'unité de mesure.|  
|unit_conversion_factor|**float**|Longueur de l'unité de mesure en mètres.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
