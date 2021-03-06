---
title: Fonction Level (Générateur de rapports et SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9dbecce71d9464267da63dcebb7388cd947a168f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65579502"
---
# <a name="report-builder-functions---level-function"></a>Fonctions du Générateur de rapports - Level
  Retourne le niveau de profondeur actuel d'une hiérarchie récursive.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *portée*  
 (**Chaîne**) (Facultatif). Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
## <a name="return-type"></a>Type de retour  
 Retourne un **Integer**. Si le paramètre *scope* spécifie un dataset ou une région de données, ou encore un regroupement non récursif (c’est-à-dire sans élément **Parent** ), la fonction **Level** retourne 0. Si vous omettez le paramètre *scope* , elle retourne le niveau de l'étendue actuelle.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par la fonction **Level** est une valeur de base zéro, c'est-à-dire que le premier niveau d'une hiérarchie est 0.  
  
 La fonction **Level** peut être utilisée pour appliquer un retrait dans une hiérarchie récursive, comme une liste d'employés.  
  
 Pour plus d’informations sur les hiérarchies récursives, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous indique le niveau de ligne dans le groupe Employees :  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
