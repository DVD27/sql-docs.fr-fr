---
title: SQL Server, objet Query Store | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store object
- SQL Server:Query Store
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 08cc5200801b99442c8973583f4ab7caa9ea9fb5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68140728"
---
# <a name="sql-server-query-store-object"></a>SQL Server, objet de magasin de requêtes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L’objet de magasin de requêtes fournit des compteurs pour surveiller l’utilisation des ressources de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de stocker les textes des requêtes, les plans d’exécution et les statistiques d’exécution concernant les objets tels que les procédures stockées, les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ad hoc et préparées, et les déclencheurs.  
  
 Ce tableau décrit les compteurs **SQLServer:Query Store**.  
  
|Compteurs de magasin de requêtes SQL Server|Description|  
|-------------------------------------|-----------------|  
|**Utilisation de l’UC du magasin de requêtes**|Indique l’utilisation de l’UC des magasins de requête.|  
|**Lectures logiques du magasin de requêtes**|Indique le nombre de lectures logiques effectuées par le magasin de requêtes.|  
|**Écritures logiques du magasin de requêtes**|Indique la quantité de données mise en file d’attente avant la vidange du magasin de requêtes. La fréquence et le délai d’ajout d’éléments (représentant les statistiques d’exécution) dans la file d’attente sont contrôlés par le paramètre Intervalle de vidange de données.|  
|**Lectures physiques du magasin de requêtes**|Indique le nombre de lectures physiques effectuées par le magasin de requêtes.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Instance de magasin de requêtes|Description|  
|--------------------------|-----------------|  
|**_Total**|Informations relatives au magasin de requêtes pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|\<nom_base_de_données>|Informations relatives au magasin de requête pour cette base de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Procédures stockées du Magasin des requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [Affichages catalogue du Magasin des requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
