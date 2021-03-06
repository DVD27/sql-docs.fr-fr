---
title: Instruction CREATe SUBCUBE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f137e8c377c94a60fdcfd8f1534069cef4b28f66
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68887434"
---
# <a name="mdx-data-definition---create-subcube"></a>Définition de données MDX - CREATE SUBCUBE


  Redéfinit l'espace du cube d'un cube ou d'un sous-cube spécifié en un sous-cube spécifié. Cette instruction modifie l'espace apparent du cube pour les opérations suivantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE SUBCUBE Cube_Name AS Select_Statement  
                                                  | NON VISUAL ( Select_Statement )  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Expression de chaîne valide qui fournit le nom d'un cube ou d'une perspective soumise à des restrictions, ce qui devient le nom du sous-cube.  
  
 *Select_Statement*  
 Expression MDX (Multidimensional Expressions) SELECT valide qui ne contient pas de clauses WITH, NON EMPTY ou HAVING et ne nécessite pas de propriétés de dimension ou de cellule.  
  
 Consultez l' [instruction &#40;Select&#41; MDX](../mdx/mdx-data-manipulation-select.md) pour obtenir une explication détaillée de la syntaxe sur les instructions SELECT et la clause **non visuelle** .  
  
## <a name="remarks"></a>Notes  
 Lorsque les membres par défaut sont exclus de la définition d'un sous-cube, les coordonnées changent de façon correspondante. Pour les attributs qui peuvent être agrégés, le membre par défaut est déplacé vers le membre [All]. Pour les attributs qui ne peuvent pas être agrégés, le membre par défaut est déplacé vers un membre existant dans le sous-cube. Le tableau ci-dessous donne des exemples de combinaisons de sous-cubes et de membres par défaut.  
  
|Membre par défaut d'origine|Peut être agrégé|Sous-sélection|Membre par défaut révisé|  
|-----------------------------|-----------------------|---------------|----------------------------|  
|Time.Year.All|Oui|{Time.Year.2003}|Aucune modification|  
|Heure. année. [1997]|Oui|{Time.Year.2003}|Time.Year.All|  
|Heure. année. [1997]|Non|{Time.Year.2003}|Heure. année. [2003]|  
|Heure. année. [1997]|Oui|{Time.Year.2003, Time.Year.2004}|Time.Year.All|  
|Heure. année. [1997]|Non|{Time.Year.2003, Time.Year.2004}|Soit Time.Year.[2003] soit<br /><br /> Time.Year.[2004]|  
  
 Les membres [All] existeront toujours dans un sous-cube.  
  
 Les objets de session créés dans le contexte d'un sous-cube sont supprimés lorsque le sous-cube est supprimé.  
  
 Pour plus d’informations sur les sous-cubes, consultez [création de sous &#40;-&#41;cubes dans MDX MDX](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx).  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous crée un sous-cube qui limite l'espace apparent du cube aux membres existants pour le Canada. Il utilise ensuite la fonction Members pour retourner tous les membres du niveau Country de la hiérarchie définie par l’utilisateur Geography, en retournant uniquement le pays du Canada.  
  
```  
CREATE SUBCUBE [Adventure Works] AS  
   SELECT [Geography].[Country].&[Canada] ON 0  
   FROM [Adventure Works]  
  
SELECT [Geography].[Country].[Country].MEMBERS ON 0  
   FROM [Adventure Works]  
  
```  
  
 L'exemple suivant crée un sous-cube qui limite l'espace apparent du cube aux membres {Accessories, Clothing} dans Products.Category et {[Value Added Reseller], [Warehouse]} dans Resellers.[Business Type].  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works]`  
  
 Interrogation du sous-cube pour tous les membres de Products.Category et Resellers.[Business Type] avec le MDX suivant :  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Donne les résultats suivants :  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$2,031,079.39|506 172,45 $|1 524 906,93 $|  
|Value Added Reseller|$767,388.52|175 002,81 $|592 385,71 $|  
|Warehouse|$1,263,690.86|331 169,64 $|932 521,23 $|  
  
 La suppression et la recréation du sous-cube à l'aide de la clause NON VISUAL créera un sous-cube conservant les totaux réels pour tous les membres de Products.Category et Resellers.[Business Type], qu'ils soient visibles ou pas dans le sous-cube.  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 Émission de la même requête MDX à partir des éléments indiqués précédemment :  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Donne les différents résultats suivants :  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|80 450 596,98 $|571 297,93 $|1 777 840,84 $|  
|Value Added Reseller|34 967 517,33 $|175 002,81 $|592 385,71 $|  
|Warehouse|38 726 913,48 $|331 169,64 $|932 521,23 $|  
  
 Les parties [All Products] et [All Resellers], colonne et ligne respectivement, contiennent des totaux pour tous les membres et pas seulement pour ceux qui sont visibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés de MDX &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)   
 [MDX (instructions &#40;de script MDX)&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [DROP (instruction &#40;de sous-cube MDX)&#41;](../mdx/mdx-data-definition-drop-subcube.md)   
 [Instruction SELECT &#40;MDX&#41;](../mdx/mdx-data-manipulation-select.md)  
  
  
