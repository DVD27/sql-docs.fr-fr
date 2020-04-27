---
title: Implémenter des travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cef657960da876b25003a6fc1017a372abe410a0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63074014"
---
# <a name="implement-jobs"></a>Implémenter des travaux
  Vous pouvez utiliser les travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour automatiser les tâches d'administration régulières et les exécuter de façon récurrente, dans le but de rendre l'administration plus efficace.  
  
 Un travail est constitué d'une série d'opérations spécifiques exécutées de manière séquentielle par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un travail peut effectuer une grande variété d'activités, y compris l'exécution de scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] , d'applications de ligne de commande, de scripts Microsoft ActiveX, de packages Integration Services, de commandes et de requêtes Analysis Services ou de tâches de réplication. Les travaux peuvent exécuter des tâches répétitives ou des tâches planifiables ; en outre, ils peuvent notifier leur état automatiquement aux utilisateurs en générant des alertes, ce qui simplifie grandement l'administration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Vous pouvez exécuter un travail manuellement ou le configurer de manière à ce qu'il s'exécute en fonction d'une planification ou en réponse à des alertes.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Contient des informations sur la création de travaux et l'affectation de propriétés.|[Créer des travaux](create-jobs.md)|  
|Contient des informations sur l'organisation des travaux en catégories.|[organiser les travaux](organize-jobs.md)|  
|Contient des informations relatives aux différents types d'étapes de travail que vous pouvez gérer et à la procédure à suivre à cet effet.|[Gérer les étapes de travail](manage-job-steps.md)|  
|Contient des informations relatives à la planification du démarrage de l'exécution des travaux et à leur fréquence d'exécution.|[Créer des planifications et les attacher à des travaux](create-and-attach-schedules-to-jobs.md)|  
|Contient des informations relatives à l'exécution manuelle des travaux (sans planification).|[Exécuter des travaux](run-jobs.md)|  
|Contient des informations relatives à la configuration du comportement de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par rapport aux travaux. Par exemple, vous pouvez configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent de manière à notifier aux administrateurs l'achèvement des travaux.|[Spécifier des réponses à un travail](specify-job-responses.md)|  
|Contient des informations relatives à la visualisation des travaux existants, à leur historique une fois exécutés et à leur modification.|[Afficher ou modifier les travaux](view-or-modify-jobs.md)|  
|Contient des informations sur la suppression de travaux.|[Supprimer des travaux](delete-jobs.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter la sécurité de l'Agent SQL Server](implement-sql-server-agent-security.md)  
  
  
