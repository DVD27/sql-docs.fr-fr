---
title: Créer un travail principal SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], master jobs
- jobs [SQL Server Agent], creating
- master SQL Server Agent job [SQL Server]
ms.assetid: c12ab23f-d7ee-43a5-8cd2-0a9121292bcd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e80d5790f78c83a8a1ff3059e12e0946e206c060
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211450"
---
# <a name="create-a-sql-server-agent-master-job"></a>Créer un travail principal SQL Server Agent
  Cette rubrique explique comment créer un travail principal [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Les modifications apportées aux travaux principaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doivent être appliquées à tous les serveurs cibles concernés. Étant donné que les serveurs cibles ne téléchargent pas le travail tant que ces cibles ne sont pas spécifiées, [!INCLUDE[msCoName](../../includes/msconame-md.md)] vous recommande d'achever toutes les étapes et planifications de travail pour un travail donné avant de spécifier des serveurs cibles. Sinon, vous devez demander manuellement que les serveurs cibles retéléchargent le travail modifié, soit en exécutant la procédure stockée **sp_post_msx_operation** , soit en modifiant le travail à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [sp_post_msx_operation &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) ou [modifier un travail](modify-a-job.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les travaux distribués dont les étapes sont associées à un proxy sont exécutés dans le contexte du compte proxy du serveur cible. Assurez-vous que les conditions suivantes sont remplies ou que les étapes de travail associées à un proxy ne seront pas téléchargées du serveur maître vers la cible :  
  
-   La sous-clé de Registre **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*nom_instance*> \SQL Server Agent\AllowDownloadedJobsToMatchProxyName**(REG_DWORD) a pour valeur 1 (true). Par défaut, la valeur de cette sous-clé est 0 (False).  
  
-   Il existe sur le serveur cible un compte proxy possédant le même nom que le compte proxy du serveur maître sur lequel l'étape du travail est exécutée.  
  
 Si les étapes du travail utilisant des comptes proxy échouent pendant leur téléchargement à partir du serveur maître vers le serveur cible, vous pouvez vérifier la colonne **error_message** dans la table **sysdownloadlist** de la base de données **msdb** pour les messages d’erreur suivants :  
  
-   « L'étape du travail nécessite un compte proxy, cependant la mise en correspondance de proxy est désactivée sur le serveur cible. » Pour corriger ce problème, affectez à la sous-clé de Registre **AllowDownloadedJobsToMatchProxyName** la valeur 1.  
  
-   « Proxy introuvable. » Pour résoudre ce problème, vérifiez qu'un compte proxy portant le même nom que le compte proxy du serveur maître sous lequel l'étape s'exécute existe sur le serveur cible.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a>Pour créer un travail principal SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer un travail SQL Server Agent.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Travaux** et sélectionnez **Nouveau travail...** .  
  
4.  Dans la boîte de dialogue **Nouveau travail** , sur la page **Général** , modifiez les propriétés générales du travail. Pour plus d’informations sur les options disponibles sur cette page, consultez [propriétés du travail et la nouvelle tâche &#40;Général Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
5.  Sur la page **Étapes** , organisez les étapes de travail. Pour plus d’informations sur les options disponibles sur cette page, consultez [propriétés du travail : nouveau travail &#40;Page étapes&#41;](job-properties-new-job-steps-page.md)  
  
6.  Sur la page **Planifications** , organisez les planifications du travail. Pour plus d’informations sur les options disponibles sur cette page, consultez [propriétés du travail : Nouveau travail &#40;Page planifications&#41;](job-properties-new-job-schedules-page.md)  
  
7.  Sur la page **Alertes** , organisez les alertes pour le travail. Pour plus d’informations sur les options disponibles sur cette page, consultez [propriétés du travail : Nouveau travail &#40;Page alertes&#41;](job-properties-new-job-alerts-page.md)  
  
8.  Sur la page **Notifications** , définissez des actions que l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devra exécuter une fois le travail terminé. Pour plus d’informations sur les options disponibles sur cette page, consultez [propriétés du travail : Nouveau travail &#40;Page Notifications&#41;](job-properties-new-job-notifications-page.md).  
  
9. Sur la page **Cibles** , gérez les serveurs cibles pour le travail. Pour plus d’informations sur les options disponibles sur cette page, consultez [propriétés du travail : Nouveau travail &#40;cible Page&#41;](job-properties-new-job-targets-page.md).  
  
10. Lorsque vous avez terminé, cliquez sur **OK**.  
  

  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a>Pour créer un travail principal SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE msdb ;  
    GO  
    -- Adds a new job executed by the SQLServerAgent service called 'Weekly Sales Data Backup'  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    -- Adds a step (operation) to the 'Weekly Sales Data Backup' job.  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    -- Creates a schedule called RunOnce  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    -- Sets the 'RunOnce' schedule to the "Weekly Sales Data Backup' Job  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2  
    -- assumes that SEATTLE2 is registered as a target server for the current instance.  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 Pour plus d'informations, consultez :  
  
-   [sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  

  
  
