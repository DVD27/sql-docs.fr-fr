---
title: Commentaire (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6eb4b54df98cfbf297e6347dac336aa7405d1347
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006291"
---
# <a name="comment-mdx-double-slash"></a>Commentaire MDX double barre oblique


  Indique un texte défini par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Il est possible d'insérer des commentaires sur une ligne distincte, à la fin d'une ligne de script MDX (Multidimensional Expressions), ou à l'intérieur d'une instruction MDX. Le serveur n'évalue pas ces commentaires.  
  
 Utilisez // pour un commentaire d'une seule ligne uniquement. Les commentaires insérés à l'aide de // sont délimités par le caractère de fin de paragraphe.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
// This member returns the gross profit margin for product types  
// and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM // Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaire &#40;&#41;MDX](../mdx/comment-mdx.md)   
 [--&#40;comment&#41; &#40;&#41;MDX](../mdx/comment-mdx-operator-reference.md)   
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
