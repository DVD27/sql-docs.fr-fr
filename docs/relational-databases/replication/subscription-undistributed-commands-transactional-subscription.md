---
title: Abonnement, commandes non distribuées (abonnement transactionnel) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 48a5742ab40b9b3f4a210b16939caddaf6fa3ed6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769421"
---
# <a name="subscription-undistributed-commands-transactional-subscription"></a>Abonnement, commandes non distribuées (abonnement transactionnel)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  L'onglet **Commandes non distribuées** contient des informations sur le nombre de commandes de la base de données de distribution qui n'ont pas été distribuées à l'abonné sélectionné, ainsi que le délai estimé de distribution de ces commandes. Pour plus d’informations sur l’affichage des commandes dans la base de données de distribution, consultez [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Options  
 **Nombre de commandes dans la base de données de distribution attendant d'être appliquées à cet abonné.**  
 Nombre de commandes dans la base de données de distribution qui n'ont pas été distribuées à l'abonné sélectionné. Une commande est constituée d'une instruction DML (Data Manipulation Language) Transact-SQL ou d'une instruction DDL (Data Definition Language).  
  
 **Temps estimé pour appliquer ces commandes, sur base des performances passées**  
 Délai estimé de distribution des commandes à l'Abonné. Si cette valeur est supérieure au délai nécessaire pour générer et appliquer un instantané à l'Abonné, réinitialisez l'Abonné. Pour plus d’informations, consultez [Réinitialiser des abonnements](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Analyser les performances avec le moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
