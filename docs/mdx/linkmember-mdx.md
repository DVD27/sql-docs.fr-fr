---
title: LinkMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8a00388e067878d9c2165cbae6844f8020b7c63e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905604"
---
# <a name="linkmember-mdx"></a>LinkMember (MDX)


  Retourne le membre équivalent à un membre spécifié dans une hiérarchie spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Le **LinkMember** fonction retourne le membre de la hiérarchie spécifiée qui correspond aux valeurs de clé à chaque niveau du membre spécifié dans une hiérarchie associée. À chaque niveau, les attributs doivent présenter la même cardinalité de clé et le même type de données. Dans les hiérarchies non naturelles, s'il y a plus d'une correspondance pour la valeur de clé d'un attribut, le résultat sera une erreur ou sera indéterminé.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise le **LinkMember** fonction pour retourner la mesure par défaut dans le cube Adventure Works des ascendants du membre du 1er juillet 2002 de la hiérarchie d’attribut Date.Date dans la hiérarchie Calendar.  
  
```  
SELECT  Hierarchize  
   (Ascendants   
      (LinkMember   
         ([Date].[Date].[July 1, 2002], [Date].[Calendar]  
         )  
       )  
    ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [Ascendants &#40;MDX&#41;](../mdx/ascendants-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
