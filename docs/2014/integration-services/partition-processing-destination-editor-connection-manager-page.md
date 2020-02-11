---
title: Éditeur de destination de traitement de partition (page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 44e116ece7460787f272f0b8cc6e99a4300fc728
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056707"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a>Éditeur de destination de traitement de partition (page Gestionnaire de connexions)
  La page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination de traitement de partition** vous permet de spécifier une connexion à un projet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Pour en savoir plus sur la destination de traitement de partition, consultez [Partition Processing Destination](data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Les tâches décrites ici ne s’appliquent pas aux modèles tabulaires Analysis Services.  Vous ne pouvez pas mapper des colonnes d’entrée aux colonnes de partition pour les modèles tabulaires. Vous pouvez en revanche utiliser la tâche DDL d'exécution [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) d'Analysis Services pour traiter la partition.  
  
## <a name="options"></a>Options  
 **Connection manager**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez une connexion à l’aide de la boîte de dialogue **Ajout d’un gestionnaire de connexions Analysis Services** .  
  
 **Liste des partitions disponibles**  
 Sélectionnez la partition à traiter.  
  
 **Méthode de traitement**  
 Sélectionnez la méthode de traitement. La valeur par défaut de cette option est **Complète**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Ajouter (incrémentiel)|Permet d'effectuer un traitement incrémentiel de la partition.|  
|Complète|Permet d'effectuer un traitement complet de la partition.|  
|Données seulement|Permet d'effectuer un traitement de mise à jour de la partition.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination de traitement de partition &#40;page Mappages&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)   
 [Éditeur de destination de traitement de partition &#40;page avancé&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
