---
title: Changer le compte de démarrage du service pour SQL Server (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server services, startup account changes
- startup accounts [SQL Server]
- changing startup accounts for services
ms.assetid: d721c796-0397-46a7-901b-1a9a3c3fb385
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a2a830ad4d6fa87cd754910baf8be53216086cab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62810434"
---
# <a name="change-the-service-startup-account-for-sql-server-sql-server-configuration-manager"></a>Modifier le compte de démarrage du service pour SQL Server (Gestionnaire de configuration SQL Server)
  Cette rubrique explique [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comment utiliser la Configuration Manager pour modifier les options de démarrage des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services et pour modifier les comptes de service utilisés par le, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’agent, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le navigateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], et. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de PowerShell. Pour plus d’informations sur la sélection d’un compte de service adéquat, consultez [Configurer les comptes de service Windows et les autorisations](configure-windows-service-accounts-and-permissions.md).  
  
> [!IMPORTANT]  
>  Lorsque vous modifiez le compte de démarrage du service pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssDE](../../includes/ssde-md.md)]) doit être redémarré pour que la modification soit prise en compte. Lorsque le service redémarre, toutes les bases de données associées à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne seront pas disponibles tant que le service n'a pas redémarré correctement. Si vous devez modifier le compte de démarrage du service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , veillez à effectuer cette opération au cours des opérations de maintenance planifiées régulièrement ou lorsqu'il est possible de mettre les bases de données hors ligne sans interrompre les opérations quotidiennes.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Serveurs en cluster  
  
     La modification du compte de service utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être effectuée à partir du nœud actif du cluster [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Lors de l'exécution sur Windows Server 2008 (dans une configuration autre que celle par défaut utilisant des groupes de domaines), la modification du compte de service utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] arrête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mettant les groupes de ressources hors ligne.  
  
-   Mise à niveau de SKU ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] vers SKU non-Express)  
  
     Au cours de l'installation de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est configuré pour utiliser le compte de service réseau, mais est désactivé. Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut changer le compte affecté au service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, mais le service ne peut pas être activé ou démarré. Après la mise à niveau d'une référence SKU de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] vers non-Express, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n'est pas automatiquement activé, mais il peut l'être lorsque cela est nécessaire en utilisant le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et en modifiant le mode de démarrage du service par Manuel ou Automatique.  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-change-the-sql-server-service-startup-account"></a>Pour modifier le compte de démarrage du service SQL Server  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
    > [!NOTE]  
    >  Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.  
    >   
    >  -   **Windows 10**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans la **page de démarrage**, tapez SQLServerManager12. msc ( [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]pour). Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , remplacez 12 par un nombre plus petit. Le fait de cliquer sur SQLServerManager12.msc ouvre le Gestionnaire de Configuration. Pour épingler le Configuration Manager à la page de démarrage ou à la barre des tâches, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **ouvrir l’emplacement du fichier**. Dans l’Explorateur de fichiers Windows, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **épingler pour démarrer** ou **Épingler à la barre des tâches**.  
    > -   **Windows 8**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans l’icône **Rechercher** , sous **applications**, tapez **SQLServerManager\<version>. msc** , par `SQLServerManager12.msc`exemple, puis appuyez sur **entrée**.  
  
2.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Services SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dont vous souhaitez modifier le compte de démarrage de service, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de SQL Server \<***nom_instance***>**, cliquez sur l’onglet **Ouvrir une session** et sélectionnez un type de compte **Ouvrir une session en tant que**.  
  
5.  Après avoir sélectionné le nouveau compte de démarrage de service, cliquez sur **OK**.  
  
     Un message vous demande si vous souhaitez redémarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
6.  Cliquez sur **Oui**, puis fermez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter, suspendre, reprendre, redémarrer le service Moteur de base de données, SQL Server Agent ou SQL Server Browser](start-stop-pause-resume-restart-sql-server-services.md)   
 [Configurer WMI pour afficher l'état du serveur dans les outils SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
