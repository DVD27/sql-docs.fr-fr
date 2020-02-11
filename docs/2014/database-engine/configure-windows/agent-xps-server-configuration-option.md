---
title: Agent XPs (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4ed2a24c72765c51e7d05fecaa5ab22c344013b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62789020"
---
# <a name="agent-xps-server-configuration-option"></a>Agent XPs (option de configuration de serveur)
  Utilisez l’option **Agent XPs** pour activer les procédures stockées étendues de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur ce serveur. Si cette option n'est pas activée, le nœud de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas disponible dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 Quand vous utilisez l’outil [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour démarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, ces procédures stockées étendues sont activées automatiquement. Pour plus d'informations, consultez [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] L’Explorateur d’objets n’affiche pas le contenu du nœud [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent, sauf si ces procédures stockées étendues sont activées, quel que soit l’état du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 Les valeurs possibles sont les suivantes :  
  
-   **0**, qui indique que les procédures stockées étendues de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne sont pas disponibles (valeur par défaut).  
  
-   **1**, qui indique que les procédures stockées étendues de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont disponibles.  
  
 Le paramètre prend effet immédiatement, sans arrêt et redémarrage du serveur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant active les procédures stockées étendues de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches d’administration automatisées &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md)   
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
