---
title: Forcer l’interrogation d’un serveur maître par un serveur cible | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e9580839c18ed40a6163ab933ce40276bc413ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63044054"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>Forcer l'interrogation d'un serveur maître par un serveur cible
  Cette rubrique explique comment forcer l'interrogation du serveur maître par un serveur cible. Le serveur cible doit être un serveur inscrit sur le serveur maître.  
  
 Un travail est une série d'actions exécutées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un travail multiserveur est un travail exécuté par un serveur maître sur un ou plusieurs serveurs cibles. Chaque serveur cible peut exécuter une instance du même travail au même moment. Chaque serveur cible interroge régulièrement le serveur maître, télécharge une copie des nouveaux travaux affectés au serveur cible, puis se déconnecte. Le serveur cible exécute localement le travail, puis se reconnecte au serveur maître pour charger l'état de la sortie du travail.  
  
> [!NOTE]  
>  Si le serveur maître est accessible lorsque le serveur cible tente de charger l'état du travail, ce dernier est mis en attente dans le spouleur jusqu'à ce que le serveur maître soit accessible.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#Restrictions), [sécurité](#Security)  
  
-   **Pour forcer l’interrogation du serveur maître par un serveur cible, avec :**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Le serveur cible doit être un serveur inscrit sur le serveur maître. Vous devez exécuter les instructions fournies dans cette rubrique à partir du serveur maître.  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) et [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
 **Pour forcer l'interrogation d'un serveur maître par un serveur cible**  
  
1.  Dans l' **Explorateur d'objets**, développez le serveur maître.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Gérer les serveurs cibles**.  
  
3.  Cliquez sur un serveur cible, puis sur **Forcer l'interrogation**.  
  
  
