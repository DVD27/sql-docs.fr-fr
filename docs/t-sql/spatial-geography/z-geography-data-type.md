---
title: Z (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Z (geography Data Type)
- Z_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z method
ms.assetid: 9abc79c5-43c9-4cc2-b37f-d2ecdec7c234
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c4c798c431b2eb71354dd803bd5701df0b6f9cad
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68120658"
---
# <a name="z-geography-data-type"></a>Z (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Valeur Z (élévation) de l'instance. La sémantique de la valeur d'élévation est définie par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Types de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 La valeur de cette propriété est Null si l’instance **geography** n’est pas un point, ainsi que pour toute instance **Point** pour laquelle elle n’est pas définie.  
  
 Cette propriété est en lecture seule.  
  
 Les coordonnées Z ne sont utilisées dans aucun calcul effectué par la bibliothèque et ne sont reportées dans aucun calcul de bibliothèque.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` avec des valeurs Z (élévation) et M (mesure) et utilise `Z` pour extraire la valeur Z de l'instance.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40;type de données geography&#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [AsTextZM &#40;type de données geography&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
