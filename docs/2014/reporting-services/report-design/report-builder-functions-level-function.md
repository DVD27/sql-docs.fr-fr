---
title: Fonction Level (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35526e8928a98ccca2e2e61e88fb9361a6d00d6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105238"
---
# <a name="level-function-report-builder-and-ssrs"></a>Fonction Level (Générateur de rapports et SSRS)
  Retourne le niveau de profondeur actuel d'une hiérarchie récursive.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *scope*  
 (`String`) (Facultatif). Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
## <a name="return-type"></a>Type de retour  
 Retourne un `Integer`. Si *scope* spécifie un DataSet ou une région de données, ou spécifie un regroupement non `Parent` récursif (c’est-à-dire un regroupement sans élément) `Level` , retourne 0. Si vous omettez le paramètre *scope* , elle retourne le niveau de l'étendue actuelle.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par la fonction `Level` est une valeur de base zéro, c'est-à-dire que le premier niveau d'une hiérarchie est 0.  
  
 La fonction `Level` peut être utilisée pour appliquer un retrait dans une hiérarchie récursive, comme une liste d'employés.  
  
 Pour plus d’informations sur les hiérarchies récursives, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous indique le niveau de ligne dans le groupe Employees :  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
