---
title: CALCULATE, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a873c2a6a60e3e6283c3c24fa4b9d28757e57ffb
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893356"
---
# <a name="mdx-scripting---calculate"></a>Écriture de scripts MDX - CALCULATE


  Remplit chaque cellule d'un cube d'une valeur d'agrégation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Arguments  
 Aucun  
  
## <a name="remarks"></a>Notes  
 L'instruction CALCULATE est automatiquement incluse en tant que première instruction d'un script MDX d'un cube lorsque vous créez un cube à l'aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Elle indique à chaque cellule au sein du cube de s'agréger à partir de cellules de granularité plus faible. Après avoir agrégé une cellule, si vous remplissez par la suite les cellules à plus faible granularité à l'aide d'expressions, cette opération aura une incidence sur la valeur agrégée des cellules à plus forte granularité. Cette agrégation est quasiment toujours souhaitable mais vous pouvez la supprimer ou forcer l'exécution d'autres instructions avant cette instruction.  
  
 L'instruction CALCULATE ne peut être intégrée à un sous-cube imbriqué au sein du script MDX. Un sous-cube imbriqué se définit à l'aide de l'instruction SCOPE. Pour plus d’informations sur l’instruction SCOPE, consultez [Scope &#40;,&#41;instruction MDX](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Les membres calculés ne sont pas agrégés.  
  
## <a name="see-also"></a>Voir aussi  
 [MDX (instructions &#40;de script MDX)&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Principes de base des scripts MDX &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services)   
 [Définir des attributions et d’autres commandes de script](https://docs.microsoft.com/analysis-services/multidimensional-models/define-assignments-and-other-script-commands)  
  
  
