---
title: Floor, fonction (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c27e432dc258b4d2b9d21bfe0ab28df8ee5b510
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946534"
---
# <a name="numeric-values-functions---floor"></a>Fonctions de valeurs numériques : floor
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Renvoie le nombre le plus élevé sans portion décimale qui ne dépasse pas la valeur de cet argument. Si l'argument est une séquence vide, la fonction renvoie la séquence vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:floor ($arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Nombre à laquelle s'applique la fonction.  
  
## <a name="remarks"></a>Notes  
 Si le type de *$arg* est un des trois types numériques de base, **xs : float**, **xs : double**, ou **xs : decimal**, le type de retour est identique à la *$arg* type. Si le type de *$arg* est un type qui est dérivé d’un des types numériques, le type de retour est le type de base numérique.  
  
 Si l’entrée pour les fonctions de valeur, fn : Ceiling ou fn : Round est **xdt : untypedAtomic**, données non typées, il est implicitement converti dans **xs : double**. Tout autre type génère une erreur statique.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
 Vous pouvez utiliser l’exemple fonctionnel de la [fonction ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) pour le **floor()** fonction XQuery. Il vous suffit de remplacer le **ceiling()** (fonction) dans la requête avec le **floor()** (fonction).  
  
## <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **floor()** fonction mappe toutes les valeurs entières à xs : decimal.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)   
 [Fonction Round &#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)   
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
