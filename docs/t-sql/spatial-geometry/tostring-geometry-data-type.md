---
title: ToString (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ToString (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a6e5a0072db244835238c1b8623c667f03e653ec
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68127337"
---
# <a name="tostring-geometry-data-type"></a>ToString (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d'une instance geometry augmentée de valeurs Z (élévation) et M (mesure) apportées par l'instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **nvarchar(max)**  
  
 Type de retour CLR : **SqlString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne la chaîne « Null » quand elle est appelée sur des instances ayant une valeur Null.  
  
 Sur les instances non Null, cette méthode est équivalente à `AsTextZM().`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une instance `LineString` et utilise `ToString()` pour extraire la description textuelle de l’instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STAsText &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Méthodes étendues sur des instances geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

