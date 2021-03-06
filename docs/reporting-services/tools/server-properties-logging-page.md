---
title: Propriétés du serveur (page Enregistrement) | Microsoft Docs
ms.date: 06/10/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9e9286363970b568e0690b622fac6d94c2b01f6b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65571387"
---
# <a name="server-properties-logging-page"></a>Propriétés du serveur (page Enregistrement)
  Utilisez cette page [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] dans [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] pour définir des limites sur les données d’exécution des rapports qui sont collectées par un serveur de rapports. Les données d'exécution sont stockées en interne dans la base de données du serveur de rapports. Vous pouvez effectuer le suivi de l'activité des rapports pour le serveur de rapports qui s'exécute en mode natif ou mode intégré SharePoint. Si le serveur de rapports fait partie d'un déploiement avec montée en puissance parallèle, le journal d'exécution des rapports gère un enregistrement de l'ensemble de l'activité des rapports pour tout le déploiement dans un seul fichier journal.  
  
 Pour ouvrir cette page
 1) Démarrer [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) Connectez-vous à un serveur de rapports.
 3) Cliquez avec le bouton droit sur le nom du serveur de rapports et sélectionnez **Propriétés**. 
 4) Cliquez sur **Enregistrement** pour ouvrir cette page.  
  
## <a name="options"></a>Options  
 **Activer la journalisation de l’exécution des rapports**  
 Cliquez pour créer et stocker des informations sur l'activité des rapports sur le serveur. Si cette option est activée, le serveur de rapports effectuera le suivi des rapports qui sont utilisés, de la fréquence de traitement des rapports, du type d'opération de rapport effectuée, du format de sortie et de la personne qui a exécuté le rapport. Pour plus d’informations sur les points de données supplémentaires capturés dans le journal, consultez [Journal des exécutions du serveur de rapports et vue ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Supprimer les entrées du journal antérieures au nombre de jours suivant**  
 Spécifiez le nombre de jours après lesquels les entrées du journal seront effacées du journal d'exécution des rapports. La valeur par défaut est 60 jours.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Se connecter à un serveur de rapports dans Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Fichiers journaux et sources de Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Journal des exécutions du serveur de rapports et vue ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
