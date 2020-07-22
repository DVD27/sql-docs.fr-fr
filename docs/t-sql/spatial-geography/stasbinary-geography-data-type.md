---
title: STAsBinary (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STAsBinary_TSQL
- STAsBinary (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STAsBinary method
ms.assetid: 99602a62-265d-4aa4-a8dc-92992ca55ba4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f2b110b4ee7abafc2c38ebc774d3d1673f0586c7
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552892"
---
# <a name="stasbinary-geography-data-type"></a>STAsBinary (type de données geography)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Retourne la représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary) d’une instance **geography**.  
  
 Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STAsBinary ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **varbinary(max)**  
  
 Type de retour CLR : **SqlBytes**  
  
## <a name="remarks"></a>Notes  
 Vous pouvez déterminer le type OGC d’une instance **geography** en appelant [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STAsBinary()` pour créer une instance `LineString``geography` de (-122.360, 47.656) à (-122.343, 47.656) à partir d’un texte. Elle retourne ensuite le résultat sous la représentation WKB.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING( -122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsBinary();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
