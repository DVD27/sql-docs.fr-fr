---
title: Propriétés de planification (page Rapports) | Microsoft Docs
ms.date: 06/30/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0e8441dec655398ec530bc95049a339edd9e01ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65571403"
---
# <a name="schedule-properties-reports-page"></a>Propriétés de planification (page Rapports)
  Utilisez la page Propriétés de planification de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] dans [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] pour consulter la liste de tous les rapports qui utilisent la planification partagée spécifique. Les planifications peuvent être utilisées pour actualiser les instantanés de rapport, générer un historique de rapport, déclencher un abonnement ou faire expirer une copie mise en cache du rapport. Pour savoir comment la planification est utilisée, consultez les informations sur les propriétés et les abonnements du rapport.  
  
 Bien que cette page affiche chaque rapport qui utilise la planification partagée, elle n'indique pas le nombre de fois où la planification partagée est utilisée dans cet unique rapport. Par exemple, supposons que 20 abonnés différents au rapport des ventes de l'entreprise utilisent tous la même planification partagée pour déclencher le traitement des abonnements. Dans ce cas, le rapport des ventes de l'entreprise apparaîtra seulement une fois dans cette liste, même s'il contient 20 références à la planification partagée.  
  
 Pour ouvrir la page Propriétés de planification :
 1. Démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 2. Connectez-vous à un serveur de rapports.
 3. Ouvrez le dossier **Planifications partagées** .
 4. Cliquez avec le bouton droit sur une planification partagée, puis sélectionnez **Propriétés**.
 5. Cliquez sur **Rapports**.  
  
  Vous pouvez aussi gérer les planifications partagées à partir de la page **Paramètres du site** du portail web [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] .
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Éditions et fonctionnalités prises en charge de SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  
  
## <a name="options"></a>Options  
 **Dossier**  
 Spécifie le chemin d'accès au rapport.  
  
 **Rapport**  
 Définit le nom du rapport qui utilise la planification.  
  
## <a name="see-also"></a>Voir aussi  
 [Create, Modify, and Delete Schedules](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)   
 [Planifications](../../reporting-services/subscriptions/schedules.md)   
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Se connecter à un serveur de rapports dans Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Configurer les propriétés générales d'un rapport (Gestionnaire de rapports)](https://msdn.microsoft.com/10b941b2-28e6-4408-9ee4-acebc63c8496)  
  
  

