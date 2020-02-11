---
title: FLOOR (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9addd13deb4dcf3c81a4975e0ed33783799ae2a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62769165"
---
# <a name="floor-ssis-expression"></a>FLOOR (expression SSIS)
  Renvoie l'entier le plus élevé inférieur ou égal à une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types des résultats  
 Type de données numérique de l'expression de l'argument. Le résultat est la partie entière de la valeur calculée dans le même type de données que *numeric_expression.*  
  
## <a name="remarks"></a>Notes  
 La fonction FLOOR renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Les exemples suivants appliquent la fonction FLOOR à une valeur successivement positive, négative et nulle.  
  
```  
FLOOR(123.45)  
```  
  
 Retourne 123.00  
  
```  
FLOOR(-123.45)  
```  
  
 Retourne -124.00  
  
```  
FLOOR(0.00)  
```  
  
 Renvoie 0,00  
  
## <a name="see-also"></a>Voir aussi  
 [CEILING &#40;expression SSIS&#41;](ceiling-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
