---
title: Filter (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 701110865f4cda286c647ef887dba2e29cc5fb42
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68081166"
---
# <a name="filter-geometry-data-type"></a>Filter (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Méthode rapide d’intersection d’index uniquement, qui permet de déterminer si une instance **geometry** entre en intersection avec une autre instance **geometry**, en supposant qu’un index soit disponible.
  
Retourne 1 si une instance **geometry** entre potentiellement en intersection avec une autre instance **geometry**. Cette méthode peut produire un retour de faux positif, et le résultat exact peut être dépendant du plan. Retourne une valeur 0 précise (retour négatif vrai) si aucune intersection d’instances **geometry** n’est détectée.
  
Dans les cas où un index n’est pas disponible ou n’est pas utilisé, la méthode retourne les mêmes valeurs que **STIntersects()** quand elle est appelée avec les mêmes paramètres.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Filter ( other_geometry )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geometry*  
 Autre instance **geometry** à comparer à l’instance sur laquelle Filter() est appelé.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Cette méthode n'est pas déterministe et n'est pas précise.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `Filter()` pour déterminer si deux instances `geometry` entrent en intersection.  
  
```  
CREATE TABLE sample (id int primary key, g geometry);  
GO  
INSERT INTO sample VALUES  
   (0, geometry::Point(0, 0, 0)),  
   (1, geometry::Point(0, 1, 0)),  
   (2, geometry::Point(0, 2, 0)),  
   (3, geometry::Point(0, 3, 0)),  
   (4, geometry::Point(0, 4, 0));  
  
CREATE SPATIAL INDEX sample_idx ON sample(g)  
WITH (bounding_box = (-8000, -8000, 8000, 8000));  
GO  
SELECT id  
FROM sample   
WHERE g.Filter(geometry::Parse('POLYGON((-1 -1, 1 -1, 1 1, -1 1, -1 -1))')) = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [STIntersects &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
  

