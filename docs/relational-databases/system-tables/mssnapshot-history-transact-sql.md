---
title: MSsnapshot_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshot_history
- MSsnapshot_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshot_history system table
ms.assetid: 56bf4128-1689-4963-9343-432dd0898d31
author: stevestein
ms.author: sstein
ms.openlocfilehash: a84b8c8caae460975a871a22d7cdac6d741d4d93
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997282"
---
# <a name="mssnapshothistory-transact-sql"></a>MSsnapshot_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsnapshot_history** table contient des lignes d’historique pour les Agents d’instantané associé à un serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ID de l'Agent d'instantané.|  
|**runstatus**|**int**|État d'exécution :<br /><br /> **1** = démarrage.<br /><br /> **2** = réussisse.<br /><br /> **3** = en cours d’exécution.<br /><br /> **4** = inactif.<br /><br /> **5** = nouvelle tentative.<br /><br /> **6** = échec.|  
|**start_time**|**datetime**|Heure de démarrage de l'exécution de la tâche|  
|**time**|**datetime**|Heure de consignation du message dans le journal|  
|**duration**|**int**|Durée, en secondes, de la session de message.|  
|**comments**|**nvarchar(255)**|Texte du message.|  
|**delivered_transactions**|**Int**|Nombre total des transactions transmises dans la session.|  
|**delivered_commands**|**int**|Nombre de commandes transmises par seconde.|  
|**delivery_rate**|**float(53)**|Moyenne des commandes transmises par seconde.|  
|**error_id**|**Int**|L’ID de l’erreur dans le [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) (table système).|  
|**timestamp**|**timestamp**|Colonne timestamp de cette table|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
