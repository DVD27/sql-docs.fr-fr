---
title: MStracer_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MStracer_history
- MStracer_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_history system table
ms.assetid: 97237a0c-d574-4b17-8a94-1a8730b31d98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e1683427057ac458e09bddde51dc70d8d402d38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016449"
---
# <a name="mstracer_history-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MStracer_history** conserve un enregistrement de tous les jetons de suivi qui ont été reçus au niveau de l’abonné. Cette table est stockée dans la base de données de distribution et sert au moment de la réplication à l'analyse des performances.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|Identifie de manière unique un jeton de suivi.|  
|**agent_id**|**int**|Identifie l'Agent qui a géré l'enregistrement du jeton de suivi.|  
|**subscriber_commit**|**DATETIME**|Date et heure auxquelles l'enregistrement du jeton de suivi a été validé sur l'Abonné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
