---
title: Supprimer un cluster Azure HDInsight, tâche | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 839350610bdcc55d185fa06c122e71b50c5ca753
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62832658"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Tâche Supprimer un cluster Azure HDInsight
La tâche **Supprimer un cluster Azure HDInsight** permet à un package SSIS de supprimer un cluster Azure HDInsight dans l’abonnement et le groupe de ressources Azure spécifiés.
  
> [!NOTE]
> La suppression d’un cluster HDInsight peut prendre 10 à 20 minutes.  
  
Pour ajouter une **tâche de suppression de cluster Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de suppression de cluster Azure HDInsight** .  
  
Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureResourceManagerConnection|Sélectionnez un gestionnaire de connexions Azure Resource Manager existant ou créez-en un qui sera utilisé pour supprimer le cluster HDInsight.|
|SubscriptionId|Spécifiez l’ID de l’abonnement du cluster HDInsight.|
|ResourceGroup|Spécifiez le groupe de ressources Azure du cluster HDInsight.|
|ClusterName|Spécifiez le nom du cluster à supprimer.|  
|FailIfNotExists|Spécifiez si la tâche doit échouer si le cluster n’existe pas.|
