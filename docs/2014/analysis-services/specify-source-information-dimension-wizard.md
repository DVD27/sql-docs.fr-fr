---
title: Spécifier les informations sur la source (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionmaintable.f1
ms.assetid: 0538b490-5185-49e1-a783-4ce3539a0de5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5015589854780f334dfa3b82b4f4ab544a4b7145
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940347"
---
# <a name="specify-source-information-dimension-wizard"></a>Spécifier des informations sur la source (Assistant Dimension)
  La page **Sélectionner la table de dimension principale** permet de sélectionner la vue de source de données, la table de dimension principale, les colonnes clés et la colonne des noms de membre pour la dimension à créer.  
  
 **Pour ouvrir l'Assistant Dimension**  
  
-   Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **Dimensions** pour un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Nouvelle dimension**.  
  
## <a name="options"></a>Options  
 **Vue de source de données**  
 Sélectionnez une vue de source de données  
  
 **Table principale**  
 Sélectionnez une table à partir de la vue de source de données sélectionnée à utiliser en tant que table principale pour la dimension.  
  
 **Colonnes clés**  
 Sélectionnez les colonnes clés à partir de la table spécifiée dans **Table principale** pour l’attribut clé de la dimension.  
  
> [!NOTE]  
>  Vous pouvez sélectionner plusieurs colonnes. Si la table contient une clé primaire composite, sélectionnez toutes les colonnes y étant comprises. L'ordre des colonnes clés est important.  
  
 **Colonne de nom**  
 Sélectionnez la colonne de la table spécifiée dans **Table principale** qui fournit les noms de membres pour la dimension. Une colonne de nom doit être spécifiée lorsqu'une clé composite est utilisée. Pour créer une colonne de nom pour une clé composite, il est recommandé de créer un calcul nommé dans la vue de source de données qui concatène les colonnes clés spécifiées. Lorsqu'une clé unique est utilisée, la colonne de nom est facultative.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
