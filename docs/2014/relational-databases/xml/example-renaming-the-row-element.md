---
title: 'Exemple : attribution d’un nouveau nom à l’élément &lt;row&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01b835696c5e64182cffb72aea80d53b3c3bb776
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62704904"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Exemple : attribution d’un nouveau nom à l’élément &lt;row&gt;
  Pour chaque ligne du jeu de résultats, le mode RAW génère un élément `<row>`. Vous pouvez éventuellement spécifier un autre nom pour cet élément en spécifiant un argument facultatif pour le mode RAW, comme illustré dans cette requête. La requête retourne un élément <`ProductModel`> pour chaque ligne de l'ensemble de lignes.  
  
## <a name="example"></a>Exemple  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 Voici l'ensemble de résultats. La directive `ELEMENTS` étant ajoutée à la requête, le résultat est centré sur les éléments.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode RAW avec FOR XML](use-raw-mode-with-for-xml.md)  
  
  
