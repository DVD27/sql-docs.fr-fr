---
title: sp_add_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_schedule_TSQL
- sp_add_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_schedule
ms.assetid: 9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 438fe71bcc32c63f97aea95c7105399c2ff8a479
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088505"
---
# <a name="spaddschedule-transact-sql"></a>sp_add_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une planification qui peut être utilisée par un nombre illimité de travaux.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_schedule [ @schedule_name = ] 'schedule_name'   
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @schedule_uid = ] schedule_uid OUTPUT ]  
    [ , [ @schedule_id = ] schedule_id OUTPUT ]  
    [ , [ @originating_server = ] server_name ] /* internal */  
```  
  
## <a name="arguments"></a>Arguments  
`[ @schedule_name = ] 'schedule_name'` Le nom de la planification. *nom_de_la_planification* est **sysname**, sans valeur par défaut.  
  
`[ @enabled = ] enabled` Indique l’état actuel de la planification. *activé* est **tinyint**, avec une valeur par défaut **1** (activé). Si **0**, la planification n’est pas activée. Si la planification n'est pas activée, aucun travail n'est exécuté dans cette dernière.  
  
`[ @freq_type = ] freq_type` Une valeur qui indique quand un travail doit être exécuté. *freq_type* est **int**, avec une valeur par défaut **0**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**4**|Tous les jours|  
|**8**|Semaine|  
|**16**|Mois|  
|**32**|Mensuelle, relatif à *freq_interval*|  
|**64**|Lancé au démarrage du service SQLServerAgent|  
|**128**|Exécution pendant une période d'inactivité de l'ordinateur.|  
  
`[ @freq_interval = ] freq_interval` Les jours d’exécution du travail. *freq_interval* est **int**, avec une valeur par défaut **1**et dépend de la valeur de *freq_type*.  
  
|Valeur de *freq_type*|Effet sur *freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (une fois)|*freq_interval* n’est pas utilisé.|  
|**4** (quotidienne)|Chaque *freq_interval* jours.|  
|**8** (hebdomadaire)|*freq_interval* prend une ou plusieurs des opérations suivantes (combinées avec un opérateur logique OR) :<br /><br /> **1** = dimanche<br /><br /> **2** = lundi<br /><br /> **4** = mardi<br /><br /> **8** = mercredi<br /><br /> **16** = jeudi<br /><br /> **32** = vendredi<br /><br /> **64** = samedi|  
|**16** (mensuellement)|Sur le *freq_interval* jour du mois.|  
|**32** (mensuel relatif)|*freq_interval* est une des opérations suivantes :<br /><br /> **1** = dimanche<br /><br /> **2** = lundi<br /><br /> **3** = mardi<br /><br /> **4** = mercredi<br /><br /> **5** = jeudi<br /><br /> **6** = vendredi<br /><br /> **7** = samedi<br /><br /> **8** = jour<br /><br /> **9** = jour de semaine<br /><br /> **10** = jour de week-end|  
|**64** (démarrage de service SQLServerAgent)|*freq_interval* n’est pas utilisé.|  
|**128**|*freq_interval* n’est pas utilisé.|  
  
`[ @freq_subday_type = ] freq_subday_type` Spécifie les unités pour *freq_subday_interval*. *freq_subday_type* est **int**, avec une valeur par défaut **0**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description (unité)|  
|-----------|--------------------------|  
|**0x1**|À une heure spécifiée|  
|**0x2**|Secondes|  
|**0x4**|Minutes|  
|**0x8**|Heures|  
  
`[ @freq_subday_interval = ] freq_subday_interval` Le nombre de *freq_subday_type* périodes entre chaque exécution d’un travail. *freq_subday_interval* est **int**, avec une valeur par défaut **0**. Remarque : Intervalle doit être supérieur à 10 secondes. *freq_subday_interval* est ignoré dans les cas où *freq_subday_type* est égal à **1**.  
  
`[ @freq_relative_interval = ] freq_relative_interval` Occurrence d’un travail de *freq_interval* chaque mois, si *freq_interval* a la valeur 32 (fréquence mensuelle relative). *freq_relative_interval* est **int**, avec une valeur par défaut **0**, et peut prendre l’une des valeurs suivantes. *freq_relative_interval* est ignoré dans les cas où *freq_type* n’est pas égal à 32.  
  
|Value|Description (unité)|  
|-----------|--------------------------|  
|**1**|Première|  
|**2**|Seconde|  
|**4**|Troisième|  
|**8**|Quatrième|  
|**16**|Dernière|  
  
`[ @freq_recurrence_factor = ] freq_recurrence_factor` Le nombre de semaines ou de mois entre chaque exécution d’une tâche planifiée. *freq_recurrence_factor* est utilisé uniquement si *freq_type* est **8**, **16**, ou **32**. *freq_recurrence_factor* est **int**, avec une valeur par défaut **0**.  
  
`[ @active_start_date = ] active_start_date` La date à laquelle l’exécution d’un travail peut commencer. *active_start_date* est **int**, avec NULL comme valeur par défaut, ce qui indique la date d’aujourd'hui. La date est au format AAAAMMJJ. Si *active_start_date* n’est pas NULL, la date doit être supérieure ou égale à 19900101.  
  
 Après avoir créé la planification, examinez la date de début et assurez-vous qu'elle est correcte. Pour plus d’informations, consultez la section « Planification des Date de début » dans [créer et attacher les planifications de travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 Pour les planifications hebdomadaires ou mensuelles, l'agent ignore si active_start_date se situe dans le passé, et utilise à la place la date actuelle. Lorsqu'une planification de l'agent SQL est créée à l'aide de sp_add_schedule, il existe une option pour spécifier le paramètre active_start_date, qui correspond à la date à laquelle l'exécution du travail commencera. Si le type de planification est hebdomadaire ou mensuel et que le paramètre active_start_date est défini à une date située dans le passé, le paramètre active_start_date est ignoré et la date actuelle est utilisée pour active_start_date.  
  
`[ @active_end_date = ] active_end_date` La date à laquelle l’exécution d’un travail peut s’arrêter. *active_end_date* est **int**, avec une valeur par défaut **99991231**, ce qui indique le 31 décembre 9999. La mise en forme est la suivante : AAAAMMJJ.  
  
`[ @active_start_time = ] active_start_time` L’heure sur n’importe quel jour entre *active_start_date* et *active_end_date* pour commencer l’exécution d’un travail. *heure_de_début_active* est **int**, avec une valeur par défaut **000000**, ce qui indique 12:00:00 a.m. sur une horloge de 24 heures. Elle doit être au format HHMMSS.  
  
`[ @active_end_time = ] active_end_time` L’heure sur n’importe quel jour entre *active_start_date* et *active_end_date* pour arrêter l’exécution d’un travail. *heure_fin_active* est **int**, avec une valeur par défaut **235959**, ce qui indique à 11:59:59 P.M. sur une horloge de 24 heures. Elle doit être au format HHMMSS.  
  
`[ @owner_login_name = ] 'owner_login_name'` Le nom du principal de serveur qui détient la planification. *owner_login_name* est **sysname**, avec NULL comme valeur par défaut, ce qui indique que la planification est détenue par le créateur.  
  
`[ @schedule_uid = ] _schedule_uidOUTPUT` Un identificateur unique pour la planification. *schedule_uid* est une variable de type **uniqueidentifier**.  
  
`[ @schedule_id = ] _schedule_idOUTPUT` Un identificateur pour la planification. *id_de_la_planification* est une variable de type **int**.  
  
`[ @originating_server = ] server_name` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est un outil dont l'interface graphique permet de gérer facilement les travaux. Son utilisation est recommandée pour créer et gérer l'infrastructure des travaux.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-schedule"></a>R. Création d'une planification  
 L'exemple suivant crée une planification nommée `RunOnce`. Elle s'exécute une fois à `23:30` le jour où la planification est créée.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_schedule  
    @schedule_name = N'RunOnce',  
    @freq_type = 1,  
    @active_start_time = 233000 ;  
  
GO  
```  
  
### <a name="b-creating-a-schedule-attaching-the-schedule-to-multiple-jobs"></a>B. Création d'une planification et attachement à plusieurs travaux  
 L'exemple suivant crée une planification nommée `NightlyJobs`. Les travaux qui utilisent cette planification s'exécutent tous les jours lorsque l'heure indiquée par le serveur est `01:00`. L'exemple joint la planification au travail `BackupDatabase` et au travail `RunReports`.  
  
> [!NOTE]  
>  Cet exemple suppose que les travaux `BackupDatabase` et `RunReports` existent déjà.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des planifications et les attacher à des travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Planifier un travail](../../ssms/agent/schedule-a-job.md)   
 [Créer une planification](../../ssms/agent/create-a-schedule.md)   
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
