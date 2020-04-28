---
title: NameToSet (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 77731495eb058da05f6c61be391591a40725e579
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088391"
---
# <a name="nametoset-mdx"></a>NameToSet (MDX)


  Retourne un jeu qui contient le membre spécifié par une chaîne au format MDX (Multidimensional Expressions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Name*  
 Expression de chaîne valide qui représente le nom d'un membre.  
  
## <a name="remarks"></a>Notes  
 Si le nom du membre spécifié existe, la fonction **NameToSet** retourne un jeu contenant ce membre. Sinon, elle retourne un jeu vide.  
  
> [!NOTE]  
>  Le nom de membre spécifié doit uniquement être un nom de membre ; il ne peut s'agir d'une expression de membre. Pour utiliser une expression de membre, consultez [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md).  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la valeur de mesure par défaut du nom de membre spécifié.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
