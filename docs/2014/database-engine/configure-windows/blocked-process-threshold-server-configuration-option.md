---
title: blocked process threshold (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 02f2fcfd3534a4ae1902a2984d2bd0fac0fc727c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62786328"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>blocked process threshold (option de configuration de serveur)
  L'option **blocked process threshold** permet de spécifier le seuil, en secondes, à partir duquel des rapports de processus bloqués sont générés. Le seuil peut être compris entre 0 et 86 400. Par défaut, aucun rapport de processus bloqué n'est généré. Cet événement n'est pas généré pour les tâches système ou les tâches en attente de ressources qui ne génèrent pas de blocages détectables.  
  
 Vous pouvez définir une [alerte](../../ssms/agent/alerts.md) à exécuter dès lorsque cet événement est généré. Ainsi, par exemple, vous pouvez choisir de contacter l'administrateur par récepteur de radiomessagerie afin de l'inviter à gérer la situation de blocage de manière appropriée.  
  
 L'option « blocked process threshold » utilise le thread d'arrière-plan Moniteur de blocage pour parcourir la liste des tâches en attente depuis une durée supérieure ou multiple du seuil configuré. L'événement est généré une fois par intervalle de génération de rapports pour chaque tâche bloquée.  
  
 Les rapports de processus bloqués sont générés le plus tôt possible. Toutefois, rien ne garantit qu'ils seront générés en temps réel ou quasiment en temps réel.  
  
 Le paramètre prend effet immédiatement, sans arrêt et redémarrage du serveur.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, l'option `blocked process threshold` est définie à `20` secondes, générant ainsi un rapport de processus bloqué pour chaque tâche bloquée.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Blocked Process Report, classe d’événements](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
