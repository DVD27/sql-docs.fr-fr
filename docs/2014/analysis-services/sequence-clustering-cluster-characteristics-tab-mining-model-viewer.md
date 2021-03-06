---
title: Sequence Clustering onglet caractéristiques du Cluster (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a3a9121129ab0f7e4e185e35418132a4f1aa663f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66069168"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a>Onglet Caractéristiques du cluster du modèle Sequence Clustering (Visionneuse de modèle d'exploration de données)
  L'onglet **Caractéristiques du cluster** dans la **Visionneuse de l'algorithme MSC** (Microsoft Sequence Clustering) fournit une liste détaillée des caractéristiques qui définissent un cluster de séquence. Ces fonctionnalités peuvent inclure des paires attribut-valeur simples, ainsi que des transitions entre les états.  
  
 Utilisez cette vue d'un modèle Sequence Clustering pour explorer le contenu du cluster et consulter les séquences représentatives d'un cluster.  
  
 **Pour plus d’informations :** [Algorithme Microsoft Sequence Clustering](data-mining/microsoft-sequence-clustering-algorithm.md), [Explorer un modèle à l’aide de la séquence de Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données pour afficher le contenu de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour consulter le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée ou la **Visionneuse de l'arborescence de contenu générique Microsoft**. Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Cluster**  
 Choisissez le cluster à afficher.  
  
 **Caractéristiques pour \<Cluster >**  
 Ce tableau présente une liste des séquences affectées au cluster actuel, classée par la probabilité. Souvenez-vous qu'une séquence est à la base une paire attribut-valeur, suivie d'un ou plusieurs paires attribut-valeur supplémentaires. La combinaison des séquences et leurs probabilités constituent les caractéristiques de définition de chaque cluster.  
  
 Par exemple, dans un modèle Sequence Clustering basé sur l'analyse du panier d'achat, un cluster peut avoir comme principale caractéristique un client choisissant l'article de vente puis mettant fin à la transaction sans effectuer d'autres achats. Dans un modèle Sequence Clustering qui cherche à analyser les erreurs d'un serveur, les caractéristiques principales d'un cluster peuvent être une série d'événements d'erreurs de fréquence élevée.  
  
|Value|Description|  
|-----------|-----------------|  
|**Variable**|Cette colonne indique si la caractéristique est une valeur ou une transition.<br /><br /> Si la caractéristique est une valeur, le **Variable** colonne contient le nom d’attribut.<br /><br /> Si la caractéristique représente une transition d’état, le **Variable** colonne contient le texte « Transitions ».|  
|**Valeurs**|La valeur de cette colonne dépend du fait que la caractéristique est une paire attribut-valeur simple, ou une transition d'état représentant une séquence commune d'éléments ou d'événements.<br /><br /> Si la caractéristique est une valeur, le **valeur** colonne contient l’état.<br /><br /> Si la caractéristique représente une transition d’état, le **valeur** colonne contient la description de la transition d’état.|  
|**Probabilité**|Cette colonne affiche une barre qui indique la probabilité relative que cette caractéristique (une paire attribut-valeur simple ou une combinaison des états) soit membre du cluster actuel.<br /><br /> Vous pouvez positionner la souris sur la paire pour afficher la valeur de fréquence de la caractéristique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
