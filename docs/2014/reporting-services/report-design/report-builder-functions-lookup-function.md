---
title: Fonction Lookup (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e60e5bab-b286-4897-9685-9ff12703517d
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 41a75e8559738294986bc5fb203b1b0469305f57
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222909"
---
# <a name="lookup-function-report-builder-and-ssrs"></a>Fonction Lookup (Générateur de rapports et SSRS)
  Retourne la première valeur correspondante pour le nom spécifié d'un dataset contenant des paires nom/valeur.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Lookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *source_expression*  
 (`Variant`) Expression évaluée dans l'étendue actuelle et qui spécifie le nom ou la clé à rechercher. Par exemple, `=Fields!ProdID.Value`.  
  
 *destination_expression*  
 (`Variant`) Expression évaluée pour chaque ligne d'un dataset et qui spécifie le nom ou la clé de correspondance. Par exemple, `=Fields!ProductID.Value`.  
  
 *result_expression*  
 (`Variant`) Une expression qui est évaluée pour la ligne dans le jeu de données où *source_expression* = *destination_expression*, et qui spécifie la valeur à récupérer. Par exemple, `=Fields!ProductName.Value`.  
  
 *dataset*  
 Constante qui spécifie le nom d'un dataset dans le rapport. Par exemple, « Products ».  
  
## <a name="return"></a>Return  
 Retourne un `Variant`, ou `Nothing` s’il n’existe aucune correspondance.  
  
## <a name="remarks"></a>Notes  
 Utilisez `Lookup` pour récupérer la valeur à partir du dataset spécifié pour une paire nom/valeur où il existe une relation 1 à 1. Par exemple, pour un champ d'ID dans une table, vous pouvez utiliser `Lookup` pour récupérer le champ Nom correspondant d'un dataset qui n'est pas lié à la région de données.  
  
 `Lookup` effectue les opérations suivantes :  
  
-   Évalue l'expression source dans l'étendue actuelle.  
  
-   Évalue l'expression de destination pour chaque ligne du dataset spécifié après avoir appliqué les filtres, en fonction du classement du dataset spécifié.  
  
-   Pour la première correspondance des expressions source et de destination, évalue l'expression de résultat pour cette ligne dans le dataset.  
  
-   Renvoie la valeur d'expression de résultat.  
  
 Pour récupérer plusieurs valeurs pour un seul champ de nom ou de clé dans lequel une relation un-à-plusieurs existe, utilisez [Fonction LookupSet &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-lookupset-function.md). Pour appeler `Lookup` pour un ensemble de valeurs, utilisez [fonction Multilookup &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-lookup-function.md).  
  
 Les restrictions suivantes s'appliquent :  
  
-   `Lookup` est évaluée une fois que toutes les expressions de filtre sont appliquées.  
  
-   Un seul niveau de recherche est pris en charge. Une expression source, destination ou de résultat ne peut pas inclure de référence à une fonction de recherche.  
  
-   Les expressions source et de destination doivent correspondre au même type de données. Le type retourné est identique au type de données de l'expression de résultat évaluée.  
  
-   Les expressions source, de destination et de résultat ne peuvent pas inclure de références à des variables de groupe ou de rapport.  
  
-   `Lookup` ne peut pas être utilisé comme expression pour les éléments de rapport suivants :  
  
    -   des chaînes de connexion dynamiques pour une source de données ;  
  
    -   des champs calculés dans un dataset ;  
  
    -   des paramètres de requête dans un dataset ;  
  
    -   des filtres dans un dataset ;  
  
    -   des paramètres de rapport ;  
  
    -   la propriété Report.Language.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, supposez qu'une table est liée à un dataset qui inclut un champ pour l'identificateur de produit ProductID. Un dataset distinct nommé « Product » contient l'identificateur de produit correspondant ID et le nom de produit Name.  
  
 Dans l'expression suivante, `Lookup` compare la valeur de ProductID à ID sur chaque ligne du dataset nommé « Product » et, lorsqu'une correspondance est trouvée, renvoie la valeur du champ Name pour cette ligne.  
  
```  
=Lookup(Fields!ProductID.Value, Fields!ID.Value, Fields!Name.Value, "Product")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapports et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  