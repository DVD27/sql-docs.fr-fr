---
title: Configurer le travail du jeu de transactions pour un serveur de publication Oracle (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 48282f08df588f54b6f03a0b99c58a2f0cf039ac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67793540"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a>Configurer le travail d'un jeu de transactions pour un serveur de publication Oracle (programmation Transact-SQL de la réplication)
  Le travail **Xactset** est un travail de base de données Oracle créé par la réplication qui s'exécute sur un serveur de publication Oracle pour créer des jeux de transactions lorsque l'Agent de lecture du journal n'est pas connecté au serveur de publication. Vous pouvez activer et configurer par programmation ce travail du serveur de distribution à l'aide de procédures stockées de réplication. Pour plus d’informations, consultez [Réglage des performances pour les serveurs de publication Oracle](../non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Pour activer le travail du jeu de transactions  
  
1.  Sur le serveur de publication Oracle, définissez le paramètre d'initialisation **job_queue_processes** avec une valeur suffisante pour autoriser l'exécution du travail Xactset. Pour plus d'informations sur ce paramètre, consultez la documentation de base de données du serveur de publication Oracle.  
  
2.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication ** \@** Oracle pour le serveur de `xactsetbatching` publication, la valeur pour ** \@PropertyName**et `enabled` la valeur pour ** \@PropertyValue**.  
  
3.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication ** \@** Oracle pour le serveur de `xactsetjobinterval` publication, la valeur pour ** \@PropertyName**et l’intervalle de travail, en minutes, pour ** \@PropertyValue**.  
  
4.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication ** \@** Oracle pour le serveur de `xactsetjob` publication, la valeur pour ** \@PropertyName**et `enabled` la valeur pour ** \@PropertyValue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Pour configurer le travail du jeu de transactions  
  
1.  (Facultatif) Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication ** \@** Oracle pour le serveur de publication. Les propriétés du travail **Xactset** sur le serveur de publication sont ainsi retournées.  
  
2.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication ** \@** Oracle pour le serveur de publication, le nom de la propriété de tâche Xactset définie pour ** \@PropertyName**et le nouveau paramètre pour ** \@PropertyValue**.  
  
3.  (Facultatif) Répétez l'étape 2 pour chaque propriété de travail Xactset définie. Lorsque vous modifiez `xactsetjobinterval` la propriété, vous devez redémarrer le travail sur le serveur de publication Oracle pour que le nouvel intervalle prenne effet.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Pour afficher les propriétés du travail du jeu de transactions  
  
1.  Sur le serveur de distribution, exécutez [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql). Spécifiez le nom du serveur de publication ** \@** Oracle pour le serveur de publication.  
  
### <a name="to-disable-the-transaction-set-job"></a>Pour désactiver le travail du jeu de transactions  
  
1.  Sur le serveur de distribution, exécutez [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql). Spécifiez le nom du serveur de publication ** \@** Oracle pour le serveur de `xactsetjob` publication, la valeur pour ** \@PropertyName**et `disabled` la valeur pour ** \@PropertyValue**.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant active le `Xactset` travail et définit un intervalle de trois minutes entre deux exécutions.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a>Voir aussi  
 [Réglage des performances pour les serveurs de publication Oracle](../non-sql/performance-tuning-for-oracle-publishers.md)   
 [Concepts liés aux procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
