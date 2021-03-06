---
title: AddCalculatedMembers (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 982484b729b59a7106b6195e361110c1d4012653
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017186"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (MDX)


  Retourne un jeu généré par l'ajout de membres calculés à un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 Par défaut, MDX exclut les membres calculés lorsqu'il résout des fonctions Set. Le **AddCalculatedMembers** fonction examine l’expression de jeu spécifiée dans *Set_Expression,* et inclut des membres calculés qui sont des frères des membres contenus dans la portée de cet ensemble expression.  
  
> [!NOTE]  
>  Cette fonction ne peut être utilisée qu'avec des expressions d'ensemble unidimensionnelles.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cette fonction.  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 L’exemple suivant retourne le `Measures.[Unit Price]` membre, en plus de tous les membres calculés dans le **mesures** dimension, à partir de la **Adventure Works** cube.  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
