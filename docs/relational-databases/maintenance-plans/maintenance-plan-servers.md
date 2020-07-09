---
title: Plan de maintenance (Serveurs) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.servers.f1
- sql13.swb.maint.maintplanproperties.server.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b94b427f2523dce7057e835aeae48b2d40d24e83
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754526"
---
# <a name="maintenance-plan-servers"></a>Plan de maintenance (Serveurs)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La boîte de dialogue **Serveurs** permet de sélectionner les serveurs sur lesquels vous souhaitez exécuter le plan de maintenance.  
  
 Pour créer un plan de maintenance multiserveur, vous devez configurer un environnement multiserveur contenant un serveur maître et un ou plusieurs serveurs cibles. Pour les plans de maintenance multiserveurs, le serveur local doit être configuré comme serveur maître. Dans les environnements multiserveurs, cette boîte de dialogue affiche le serveur maître **(local)** et tous les serveurs cibles correspondants. Un travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créé pour le serveur local. Celui-ci est activé ou désactivé selon que vous avez sélectionné le serveur **(local)** . Si des serveurs cibles sont sélectionnés, un travail multiserveur est créé et téléchargé vers chacun des serveurs cibles sélectionnés. Si aucun serveur cible n'est sélectionné, le travail multiserveur est supprimé.  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md)   
 [Créer un serveur maître](../../ssms/agent/make-a-master-server.md)   
 [Créer un serveur cible](../../ssms/agent/make-a-target-server.md)  
  
  
