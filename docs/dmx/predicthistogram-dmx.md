---
title: PredictHistogram (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fdc63d1c93d1290c701233cb94f71f157c771182
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893849"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne une table qui représente un histogramme de la prévision d'une colonne donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Référence de colonne scalaire ou référence de colonne de cluster. Peut être utilisée avec tous les types d'algorithmes, à l'exception de l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association.  
  
## <a name="return-type"></a>Type de retour  
 Table.  
  
## <a name="remarks"></a>Notes  
 Un histogramme génère des colonnes statistiques. La structure de colonne de l’histogramme retourné dépend du type de référence de colonne utilisé avec la fonction **PredictHistogram** .  
  
## <a name="scalar-columns"></a>Colonnes scalaires  
 Pour une \<référence de colonne scalaire >, l’histogramme retourné par la fonction **PredictHistogram** se compose des colonnes suivantes:  
  
-   La valeur actuellement en cours de prévision  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]les algorithmes d’exploration de données ne prennent pas en charge **$ProbabilityVariance**. Cette colonne contient toujours 0 pour les algorithmes [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]les algorithmes d’exploration de données ne prennent pas en charge **$ProbabilityStdev**. Cette colonne contient toujours 0 pour les algorithmes [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$AdjustedProbability**  
  
     La colonne **$AdjustedProbability** est une [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] extension de la [!INCLUDE[msCoName](../includes/msconame-md.md)] spécification OLE DB pour l’exploration de données.  
  
## <a name="cluster-columns"></a>Colonnes de cluster  
 L’histogramme retourné par la fonction **PredictHistogram** pour une \<référence de colonne de cluster > se compose des colonnes suivantes:  
  
-   **$Cluster** (représente le nom du cluster)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne l'état prévisible de la colonne Bike Buyer (Acheteur de bicyclette) dans une requête singleton. La requête retourne également les deux premiers États les plus probables de l’attribut vélo Buyer, en fonction de la probabilité ajustée obtenue à l’aide de la fonction **PredictHistogram** .  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DMX &#40;du cluster&#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)   
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Référence des fonctions &#40;DMX&#41; des extensions d’exploration de données](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions &#40;de prédiction générales DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
