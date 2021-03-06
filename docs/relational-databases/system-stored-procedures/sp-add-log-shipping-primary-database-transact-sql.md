---
title: sp_add_log_shipping_primary_database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_primary_database
- sp_add_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_primary_database
ms.assetid: 69531611-113f-46b5-81a6-7bf496d0353c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5af11c14c7b0bf3b8e32d503c4b77e59623ce9ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140445"
---
# <a name="spaddlogshippingprimarydatabase-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Initialise la base de données primaire d'une configuration d'envoi de journaux, ce qui inclut le travail de sauvegarde, l'enregistrement de surveillance local, et l'enregistrement de surveillance distant.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_log_shipping_primary_database [ @database = ] 'database',   
[ @backup_directory = ] 'backup_directory',   
[ @backup_share = ] 'backup_share',   
[ @backup_job_name = ] 'backup_job_name',   
[, [ @backup_retention_period = ] backup_retention_period]  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] backup_threshold ]   
[, [ @threshold_alert = ] threshold_alert ]   
[, [ @threshold_alert_enabled = ] threshold_alert_enabled ]   
[, [ @history_retention_period = ] history_retention_period ]  
[, [ @backup_job_id = ] backup_job_id OUTPUT ]  
[, [ @primary_id = ] primary_id OUTPUT]  
[, [ @backup_compression = ] backup_compression_option ]  
  
```  
  
## <a name="arguments"></a>Arguments  
`[ @database = ] 'database'` Est le nom du journal de transaction base de données primaire. *base de données* est **sysname**, sans valeur par défaut, et ne peut pas être NULL.  
  
`[ @backup_directory = ] 'backup_directory'` Est le chemin d’accès au dossier de sauvegarde sur le serveur principal. *backup_directory* est **nvarchar (500)** , sans valeur par défaut, et ne peut pas être NULL.  
  
`[ @backup_share = ] 'backup_share'` Est le chemin d’accès réseau au répertoire de sauvegarde sur le serveur principal. *backup_share* est **nvarchar (500)** , sans valeur par défaut, et ne peut pas être NULL.  
  
`[ @backup_job_name = ] 'backup_job_name'` Est le nom de la tâche de l’Agent SQL Server sur le serveur principal qui copie la sauvegarde dans le dossier de sauvegarde. *backup_job_name* est **sysname** et ne peut pas être NULL.  
  
`[ @backup_retention_period = ] backup_retention_period` Est la longueur de la durée, en minutes, de conserver le fichier de sauvegarde de journal dans le répertoire de sauvegarde sur le serveur principal. *backup_retention_period* est **int**, sans valeur par défaut, et ne peut pas être NULL.  
  
`[ @monitor_server = ] 'monitor_server'` Est le nom du serveur moniteur. *Monitor_server* est **sysname**, sans valeur par défaut, et ne peut pas être NULL.  
  
`[ @monitor_server_security_mode = ] monitor_server_security_mode` Le mode de sécurité utilisé pour se connecter au serveur moniteur.  
  
 1 = Authentification Windows.  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. *monitor_server_security_mode* est **bits** et ne peut pas être NULL.  
  
`[ @monitor_server_login = ] 'monitor_server_login'` Est le nom d’utilisateur du compte utilisé pour accéder au serveur moniteur.  
  
`[ @monitor_server_password = ] 'monitor_server_password'` Est le mot de passe du compte utilisé pour accéder au serveur moniteur.  
  
`[ @backup_threshold = ] backup_threshold` Est la longueur de la durée, en minutes, après la dernière sauvegarde avant qu’un *threshold_alert ne* erreur est générée. *backup_threshold* est **int**, avec une valeur par défaut de 60 minutes.  
  
`[ @threshold_alert = ] threshold_alert` Est l’alerte à déclencher lorsque le seuil de sauvegarde est dépassé. *threshold_alert ne* est **int**, avec 14 420 comme valeur par défaut.  
  
`[ @threshold_alert_enabled = ] threshold_alert_enabled` Spécifie si une alerte est déclenchée quand *backup_threshold* est dépassé. La valeur par défaut zéro (0) indique que l'alerte est désactivée et ne sera pas déclenchée. *threshold_alert_enabled* est **bits**.  
  
`[ @history_retention_period = ] history_retention_period` Est la durée en minutes pendant laquelle l’historique doit être conservé. *history_retention_period* est **int**, avec NULL comme valeur par défaut. Une valeur de 14420 sera utilisée en l'absence de toute autre spécification.  
  
`[ @backup_job_id = ] backup_job_id OUTPUT` Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ID de tâche de l’Agent associé à la tâche de sauvegarde sur le serveur principal. *backup_job_id* est **uniqueidentifier** et ne peut pas être NULL.  
  
`[ @primary_id = ] primary_id OUTPUT` ID de la base de données primaire pour la configuration d’envoi de journaux. *primary_id* est **uniqueidentifier** et ne peut pas être NULL.  
  
`[ @backup_compression = ] backup_compression_option` Spécifie si une configuration de copie des journaux utilise [compression de la sauvegarde](../../relational-databases/backup-restore/backup-compression-sql-server.md). Ce paramètre est pris en charge uniquement dans le [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (ou une version ultérieure).  
  
 0 = Désactivées. Ne jamais compresser des sauvegardes de journal.  
  
 1 = Activé. Toujours compresser des sauvegardes de journal.  
  
 2 = utiliser le paramètre de la [afficher ou configurer l’Option de Configuration de serveur par défaut de compression de la sauvegarde](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 **sp_add_log_shipping_primary_database** doit être exécuté à partir de la **master** base de données sur le serveur principal. Cette procédure stockée remplit les fonctions suivantes :  
  
1.  Génère un ID primaire et ajoute une entrée pour la base de données primaire dans la table **log_shipping_primary_databases** à l’aide des arguments fournis.  
  
2.  Elle crée un travail de sauvegarde pour la base de données primaire qui est désactivée.  
  
3.  Définit l’ID de tâche de sauvegarde dans le **log_shipping_primary_databases** entrée à l’ID du travail de la tâche de sauvegarde.  
  
4.  Ajoute un enregistrement moniteur local dans la table **log_shipping_monitor_primary** sur le serveur principal à l’aide des arguments fournis.  
  
5.  Si le serveur moniteur est différent du serveur principal, ajoute un enregistrement moniteur dans **log_shipping_monitor_primary** sur le moniteur de serveur à l’aide des arguments fournis.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 Cet exemple ajoute la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] en tant que base de données primaire dans une configuration d'envoi de journaux.  
  
```  
DECLARE @LS_BackupJobId AS uniqueidentifier ;  
DECLARE @LS_PrimaryId AS uniqueidentifier ;  
  
EXEC master.dbo.sp_add_log_shipping_primary_database   
@database = N'AdventureWorks'   
,@backup_directory = N'c:\lsbackup'   
,@backup_share = N'\\tribeca\lsbackup'   
,@backup_job_name = N'LSBackup_AdventureWorks'   
,@backup_retention_period = 1440  
,@monitor_server = N'rockaway'   
,@monitor_server_security_mode = 1   
,@backup_threshold = 60   
,@threshold_alert = 0   
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440   
,@backup_job_id = @LS_BackupJobId OUTPUT   
,@primary_id = @LS_PrimaryId OUTPUT   
,@overwrite = 1   
,@backup_compression = 0;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
