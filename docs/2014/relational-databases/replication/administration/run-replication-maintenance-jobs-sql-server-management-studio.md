---
title: Exécuter des travaux de maintenance de réplication (SQL Server Management Studio)| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c00479e5587c8662d81e554cae5add2e295183
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068756"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>Exécuter des travaux de maintenance de réplication (SQL Server Management Studio)
  Les travaux de maintenance de la réplication sont les suivants :  
  
-   **Réinitialiser les abonnements présentant des erreurs de validation de données**
-   **Nettoyage de l'historique de l'agent : distribution**
-   **Actualisateur d'analyse de réplication pour la distribution.**
-   **Contrôle des agents de réplication**
-   **Nettoyage de la distribution : distribution**
-   **Nettoyage de l'abonnement expiré**  
  
 Démarrez et arrêtez ces travaux à partir du dossier **Travaux** de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et à partir de l’onglet **Agents** du moniteur de réplication. Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../monitor/start-the-replication-monitor.md). Affichez et modifiez les propriétés de chaque travail dans la boîte de dialogue **Propriétés du travail- \<Job> ** , accessible à partir du même dossier et du même onglet.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>Pour démarrer ou arrêter un travail de maintenance de réplication dans Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez avec le bouton droit sur un travail, puis cliquez sur **Démarrer le travail** ou sur **Arrêter le travail**.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>Pour démarrer ou arrêter un travail de maintenance de réplication dans le moniteur de réplication  
  
1.  Développez un groupe du serveur de publication dans le moniteur de réplication, puis sélectionnez un serveur de publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez avec le bouton droit sur un travail dans la grille, puis cliquez sur **Démarrer le travail** ou sur **Arrêter le travail**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>Pour afficher et modifier les propriétés d'un travail de maintenance de réplication dans Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez avec le bouton droit sur un travail, puis sélectionnez **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés du travail- \<Job> ** , modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>Pour afficher et modifier les propriétés d'un travail de maintenance de réplication dans le moniteur de réplication  
  
1.  Développez un groupe du serveur de publication dans le moniteur de réplication, puis sélectionnez un serveur de publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez avec le bouton droit sur un travail dans la grille, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés du travail- \<Job> ** , modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer et arrêter un agent de réplication &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Administration de l’Agent de réplication](../agents/replication-agent-administration.md)  
  
  
