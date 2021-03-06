---
title: dbo.sysjobsteps (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13cf57e181c3fbb1371c10b554eb9da344a951d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004733"
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur chaque étape d'un travail devant être exécuté par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID du travail.|  
|**step_id**|**Int**|ID de l'étape dans le travail|  
|**step_name**|**sysname**|Nom de l'étape du travail|  
|**subsystem**|**nvarchar(40)**|Nom du sous-système utilisé par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour exécuter l'étape du travail|  
|**commande**|**nvarchar(max)**|Commande à exécuter par **sous-système**.|  
|**flags**|**Int**|Réservé.|  
|**additional_parameters**|**ntext**|Réservé.|  
|**cmdexec_success_code**|**int**|Valeur de niveau d’erreur retourné par **CmdExec** étapes du sous-système pour indiquer la réussite.|  
|**on_success_action**|**tinyint**|Action à exécuter lors du succès d'une étape|  
|**on_success_step_id**|**int**|ID de la prochaine étape à exécuter après le succès d'une étape|  
|**on_fail_action**|**tinyint**|Action à exécuter lors de l'échec d'une étape|  
|**on_fail_step_id**|**int**|ID de l'étape à exécuter après l'échec d'une étape|  
|**server**|**sysname**|Réservé.|  
|**database_name**|**sysname**|Nom de la base de données dans lequel **commande** est exécutée si **sous-système** TSQL.|  
|**database_user_name**|**sysname**|Nom de l'utilisateur de la base de données dont le compte sera utilisé lors de l'exécution de l'étape|  
|**retry_attempts**|**int**|Nombre de tentatives de reprise en cas d'échec de l'étape|  
|**retry_interval**|**Int**|Délai d'attente entre chaque tentative de reprise|  
|**os_run_priority**|**int**|Réservé.|  
|**output_file_name**|**nvarchar(200)**|Nom du fichier dans lequel le résultat de l’étape est enregistré lorsque **sous-système** TSQL, PowerShell, ou **CmdExec** _._|  
|**last_run_outcome**|**int**|Issue de l'exécution précédente de l'étape du travail<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **2** = nouvelle tentative<br /><br /> **3** = annulée<br /><br /> **5** = inconnu|  
|**last_run_duration**|**Int**|Durée (hhmmss) de l'étape lors de sa dernière exécution.|  
|**last_run_retries**|**int**|Nombre de tentatives de reprises lors de la dernière exécution de l'étape du travail|  
|**last_run_date**|**int**|Date (aaaammjj) de début de la dernière exécution de l'étape.|  
|**last_run_time**|**int**|Heure (hhmmss) de début de la dernière exécution de l'étape.|  
|**proxy_id**|**int**|Proxy pour les étapes du travail.|  
|**step_uid**|**uniqueidentifier**|Identificateur de l’étape de travail.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de l’Agent SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
