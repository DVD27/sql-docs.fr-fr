---
title: Afficher les commandes répliquées et autres informations dans la base de données de Distribution (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2bff82764256eebb02141bf2e1fafd86dce026e4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666648"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a>Afficher les commandes répliquées et autres informations dans la base de données de distribution (programmation Transact-SQL de la réplication)
  Lors de l'utilisation de la réplication transactionnelle, les commandes de transaction sont stockées dans la base de données de distribution jusqu'à ce que l'Agent de distribution les propage sur tous les Abonnés ou qu'un Agent de distribution sur l'Abonné extrait les modifications. Ces commandes en attente dans la base de données de distribution peuvent être affichées par programmation à l'aide de procédures stockées de réplication. Pour plus d’informations, consultez [Procédures stockées de réplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>Pour afficher les commandes répliquées de toutes les publications transactionnelles de la base de données de distribution  
  
1.  Sur la base de données de distribution du serveur de distribution, exécutez [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>Pour afficher les commandes répliquées de la base de données de distribution à partir d'un article spécifique ou d'une base de données spécifique publiée à l'aide de la réplication transactionnelle  
  
1.  (Facultatif) Sur la base de données de publication du serveur de publication, exécutez [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql). Spécifiez **@publication** et **@article** . Notez la valeur de **article_id** dans le jeu de résultats.  
  
2.  Sur la base de données de distribution du serveur de distribution, exécutez [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql). (Facultatif) Spécifiez l'ID d'article de l'étape 2 pour **@article_id** . (Facultatif) Spécifiez l'ID de la base de données de publication pour **@publisher_database_id** , qui peut être obtenu à partir de la colonne **database_id** de l'affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller la réplication par programmation](../monitoring-replication.md)  
  
  
