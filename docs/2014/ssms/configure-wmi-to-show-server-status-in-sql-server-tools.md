---
title: Configurer WMI pour afficher l’état du serveur dans les outils SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0b0b8236187698917dddd3ca98830add6c3fde9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245665"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Configurer WMI pour afficher l'état du serveur dans les outils SQL Server
  Cette rubrique explique comment configurer WMI pour afficher l'état du serveur dans les outils SQL Server dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Lors de la connexion aux serveurs, les composants Serveurs inscrits et Explorateur d'objets de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ainsi que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , utilisent WMI (Windows Management Instrumentation) pour obtenir l'état des services [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER). Pour afficher l'état du service, l'utilisateur doit disposer des droits d'accéder à distance à l'objet WMI. Cette autorisation peut être configurée seulement si WMI a été installé sur le serveur.  
  
##  <a name="to-configure-wmi-permission"></a><a name="SSMSProcedure"></a>Pour configurer l’autorisation WMI  
  
1.  Sur le serveur distant, dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans la zone **ouvrir** , `wmimgmt.msc`tapez, puis cliquez sur **OK**.  
  
3.  Dans le programme **Windows Management Infrastructure** , cliquez avec le bouton droit sur **Contrôle WMI (local)** , puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de WMI Control (Local)** , sous l’onglet **Sécurité** , développez **Root**, puis cliquez sur **CIMV2**.  
  
5.  Cliquez sur **Sécurité** pour ouvrir la boîte de dialogue **Sécurité pour ROOT\CIMV2** .  
  
6.  Ajoutez un groupe ou un utilisateur à la zone **Noms de groupes ou d’utilisateurs** et sélectionnez-le.  
  
7.  Dans la zone **autorisations pour**_\<le groupe ou l’utilisateur>_ , sélectionnez la colonne **autoriser** , pour l’autorisation **activation à distance** , pour les utilisateurs pour lesquels vous souhaitez détecter à distance l’état du service.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
