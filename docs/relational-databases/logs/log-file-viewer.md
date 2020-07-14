---
title: Visionneuse du fichier journal | Microsoft Docs
description: La Visionneuse du fichier journal dans SQL Server Management Studio permet d’accéder aux informations sur les erreurs et événements capturés dans les fichiers journaux.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7425bb2175b9a2e7b813f63e7d78aec7e73ef5ec
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85668127"
---
# <a name="log-file-viewer"></a>Visionneuse du fichier journal
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La Visionneuse du fichier journal dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] permet d'accéder aux informations sur les erreurs et événements capturés dans les fichiers journaux.  
  
## <a name="benefits-of-using-log-file-viewer"></a>Avantages liés à l'utilisation de la Visionneuse du fichier journal  
 Vous pouvez consulter des fichiers journaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'une instance locale ou distante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque l'instance cible est hors connexion ou ne peut pas démarrer. Vous pouvez accéder aux fichiers journaux hors connexion à partir des serveurs inscrits, ou par programmation via des requêtes WMI et WQL (WMI Query Language). Pour plus d’informations, consultez [Afficher les fichiers journaux hors connexion](../../relational-databases/logs/view-offline-log-files.md). Voici les types de fichiers journaux auxquels vous pouvez accéder à l'aide de la Visionneuse du fichier journal :  
  
-   Collection d'audits  
  
-   Collecte de données  
  
-   Messagerie de base de données  
  
-   Historique des travaux  
  
-   Plans de maintenance  
  
-   Plans de maintenance distants  
  
-   SQL Server  
  
-   SQL Server Agent  
  
-   Windows NT (ces événements Windows sont également accessibles à partir de l'Observateur d'événements)  
  
## <a name="log-file-viewer-tasks"></a>Tâches de la Visionneuse du fichier journal  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment ouvrir la Visionneuse du fichier journal de différentes façons, selon les informations que vous souhaitez consulter.|[Ouvrir la Visionneuse du fichier journal](../../relational-databases/logs/open-log-file-viewer.md)|  
|Explique comment afficher des fichiers journaux hors ligne par le biais de serveurs inscrits et comment vérifier les autorisations WMI.|[Afficher les fichiers journaux hors connexion](../../relational-databases/logs/view-offline-log-files.md)|  
|Fournit l'aide (accessible à l'aide de la touche F1) relative à la Visionneuse du fichier journal.|[Visionneuse du fichier journal - Aide (F1)](../../relational-databases/logs/log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Audit &#40moteur de base de données&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
