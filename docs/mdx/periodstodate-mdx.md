---
title: PeriodsToDate (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 812cd16a7d6b7a17d4f2f12098f22e32cf0d3363
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055632"
---
# <a name="periodstodate-mdx"></a>PeriodsToDate (MDX)


  Retourne un jeu des membres frères de même niveau qu'un membre donné, commençant par le premier frère et se terminant par le membre donné, conformément à la contrainte du niveau spécifié de la dimension Time.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PeriodsToDate( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Dans l’étendue du niveau spécifié, la fonction **PeriodsToDate** retourne le jeu de périodes au même niveau que le membre spécifié, en commençant par la première période et en terminant par le membre spécifié.  
  
-   Si un niveau est spécifié, le membre actuel de la hiérarchie est une *hiérarchie*déduite. **CurrentMember**, où *Hierarchy*est la hiérarchie du niveau spécifié.  
  
-   Si ni un niveau ni un membre n'est spécifié, le niveau est le niveau parent du membre actuel de la première hiérarchie sur la première dimension de type Time dans le groupe de mesures.  
  
 
  `PeriodsToDate( Level_Expression, Member_Expression )` est fonctionnellement équivalent à l'expression MDX suivante :  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne la somme du `Measures.[Order Quantity]` membre, agrégée sur les huit premiers mois de l’année civile 2003 qui sont contenus dans la `Date` dimension, à partir du cube **Adventure Works** .  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 L'exemple ci-après est agrégé sur les deux premiers mois du deuxième semestre de l'annéé civile 2003.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;&#41;MDX](../mdx/topcount-mdx.md)   
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
