---
title: MSmerge_metadataaction_request (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
author: stevestein
ms.author: sstein
ms.openlocfilehash: 09f3fa61a1f79e98b8cd3330a03361b1b6a5c507
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106370"
---
# <a name="msmergemetadataactionrequest-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_metadataaction_request** table stocke une ligne pour chaque action de compensation est nécessaire. À l’aide de la synchronisation Web, si une erreur se produit et la synchronisation doit être retentée, une entrée est transformée en **MSmerge_metadataaction_request**. Lors de la phase de téléchargement de la fusion suivante, les demandes de tous les articles appartenant à la publication à synchroniser sont extraites de cette table et téléchargées. Lorsque la synchronisation est effectuée, la ligne correspondante dans le **MSmerge_metadataaction_request** table est supprimée. Cette table est stockée dans la base de données de publication du serveur de publication et dans la base de données d'abonnement de l'Abonné.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**Int**|Surnom de la table publiée.|  
|**rowguid**|**uniqueidentifier**|Identificateur de ligne pour la ligne concernée.|  
|**action**|**tinyint**|Définit l'action de compensation nécessaire.|  
|**génération**|**bigint**|Valeur de la génération pour laquelle l'action de compensation est nécessaire.|  
|**changed**|**Int**|Interne-usage uniquement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Synchronisation web pour la réplication de fusion](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
