---
title: Propriétés personnalisées de la destination DataReader | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: janinezhang
ms.author: janinez
ms.openlocfilehash: eb252810f2136cfd478bf7ce02690d1ba84dc8d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049373"
---
# <a name="datareader-destination-custom-properties"></a>Propriétés personnalisées de la destination DataReader

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La destination DataReader comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination DataReader. Toutes les propriétés sont en lecture/écriture, à l’exception de **DataReader** .  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|DataReader|String|Nom de classe de la destination DataReader.|  
|FailOnTimeout|Booléen|Indique s’il faut faire échouer l’opération ou non quand un **ReadTimeout** se produit. La valeur par défaut de cette propriété est **False**.|  
|ReadTimeout|Entier|Nombre de millisecondes devant s'écouler avant l'expiration du délai d'attente. La valeur par défaut de cette propriété est 30000 (30 secondes).|  
  
 L'entrée et les colonnes d'entrée de la destination DataReader ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination DataReader](../../integration-services/data-flow/datareader-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
