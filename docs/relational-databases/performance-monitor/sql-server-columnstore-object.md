---
title: SQL Server, objet columnstore | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 334a8388b7abc217123071fdc37c9e1091f6a3fc
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "67987134"
---
# <a name="sql-server-columnstore-object"></a>SQL Server, objet columnstore
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L’objet **SQLServer:Columnstore** fournit des compteurs permettant de surveiller l’exécution des index columnstore dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le tableau suivant décrit les compteurs **Columnstore** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs ColumnStore|Description|  
|--------------------------|-----------------|  
|**Rowgroups delta fermés**|Nombre de rowgroups delta fermés.|  
|**Rowgroups delta compressés**|Nombre de rowgroups delta compressés.|  
|**Rowgroups delta créés**|Nombre de rowgroups delta créés.|  
|**Taux d’accès au cache de segments**|Pourcentage de segments de colonne détectés dans le pool columnstore sans devoir effectuer de lecture à partir du disque.|  
|**Base du taux d’accès au cache de segments**|À usage interne uniquement.|
|**Lectures de segments/s**|Nombre de lectures de segments physiques effectuées.|  
|**Total des tampons de suppression migrés**|Nombre de nettoyages du tampon de suppression par le moteur de tuple.|  
|**Total des évaluations de la stratégie de fusion**|Nombre d’évaluations de la stratégie de fusion pour columnstore.|  
|**Total des rowgroups compressés**|Nombre total de rowgroups compressés.|  
|**Nombre total de rowgroups prêts pour la fusion**|Nombre de rowgroups sources prêts pour l’opération MERGE depuis le démarrage de SQL Server.|  
|**Total des rowgroups fusionnés et compressés**|Nombre de rowgroups cibles compressés créés avec MERGE depuis le démarrage de SQL Server.|  
|**Total des rowgroups sources fusionnés**|Nombre de rowgroups sources fusionnés depuis le démarrage de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
