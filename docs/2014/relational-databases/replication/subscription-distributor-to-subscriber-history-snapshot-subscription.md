---
title: Abonnement, Historique du serveur de distribution vers l’abonné (Abonnement aux instantanés) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.pubtodist.snapshot.f1
ms.assetid: d3575964-f287-4bcf-8d2e-f81a33141b25
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9e0520c28d78b8036072b70de2d8f83a1a8c72da
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62628774"
---
# <a name="subscription-distributor-to-subscriber-history-snapshot-subscription"></a>Abonnement, Historique du serveur de distribution vers l'Abonné (abonnement aux instantanés)
  L’onglet historique du serveur **de distribution vers l’abonné** affiche des informations détaillées sur la agent de distribution, y compris l’État, l’historique, les messages d’information et les messages d’erreur éventuels.  
  
## <a name="options"></a>Options  
 Dans le menu **Affichage** , sélectionnez les sessions de l'Agent de distribution à afficher. Sélectionnez ensuite une session particulière dans la grille étiquetée **Sessions de l'Agent de distribution**. Des informations détaillées sur cette session s'affichent dans la grille étiquetée **Actions dans la session sélectionnée**. Si la session sélectionnée s'est terminée sur une erreur, la zone de texte étiquetée **Détails de l'erreur ou message de la session sélectionnée** s'affiche également.  
  
 **Afficher**  
 Sélectionnez les sessions de l'Agent de distribution à afficher.  
  
 **État**  
 État de l'Agent de distribution La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Completed  
  
-   Nouvel essai  
  
-   Exécution en cours  
  
 **Heure de début**  
 Heure d'ouverture de la session.  
  
 **Heure de fin**  
 Heure de fin de la session. Si l'agent ne s'est pas arrêté, ce champ est vide.  
  
 **Durée**  
 Durée d'exécution de l'Agent de distribution dans cette session. Cette durée représente le temps écoulé si l'agent est en cours d'exécution et le temps total de la session si l'agent de la session s'est terminé.  
  
 **Message d’erreur**  
 Si une session s'est terminée sur une erreur, ce champ affiche le dernier message d'erreur enregistré par l'Agent de distribution. Dans le cas contraire, ce champ est vide.  
  
 **Message d’action**  
 Tous les messages d'information ou d'erreur que l'Agent de distribution a enregistrés pendant la session sélectionnée.  
  
 **Heure de l’action**  
 Heure à laquelle l'action décrite dans la colonne **Message d'action** s'est déroulée.  
  
 **Détails de l’erreur ou message de la session sélectionnée**  
 S'affiche uniquement si la session sélectionnée affiche une valeur **Erreur** dans la colonne **État** . La zone de texte affiche des informations d'erreur détaillées, ainsi que la commande émise au moment de l'erreur. Elle comporte également des liens vers des informations supplémentaires à propos de l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Surveillance de la réplication](monitoring-replication.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  
