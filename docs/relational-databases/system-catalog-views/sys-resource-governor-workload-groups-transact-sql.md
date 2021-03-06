---
title: Sys.resource_governor_workload_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_workload_groups
- resource_governor_workload_groups_TSQL
- sys.resource_governor_workload_groups_TSQL
- resource_governor_workload_groups
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_workload_groups catalog view
ms.assetid: 619ba4b7-868f-4784-b527-ec1dfd703c4f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0f80d9ba8f5b5a1e81949d0fb2ea4b1d9bca59d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904444"
---
# <a name="sysresourcegovernorworkloadgroups-transact-sql"></a>sys.resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la configuration de groupe de charge de travail stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chaque groupe de charges de travail peut s'abonner à un seul et unique pool de ressources.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|group_id|**int**|ID unique du groupe de charges de travail. N'accepte pas la valeur NULL.|  
|name|**sysname**|Nom du groupe de charges de travail. N'accepte pas la valeur NULL.|  
|importance|**sysname**|**Remarque :** Importance s’applique uniquement aux groupes de charges de travail dans le même pool de ressources.<br /><br /> Importance relative d'une demande dans ce groupe de charges de travail. Le paramètre Importance peut avoir les valeurs suivantes, MEDIUM étant la valeur par défaut : FAIBLE, MOYEN, ÉLEVÉ.<br /><br /> N'accepte pas la valeur NULL.|  
|request_max_memory_grant_percent|**Int**|Allocation de mémoire maximale, en pourcentage, pour une demande unique. La valeur par défaut est 25. N'accepte pas la valeur NULL.<br /><br /> **Remarque :** Si ce paramètre est supérieur à 50 pour cent, les requêtes volumineuses exécutera une à la fois. Par conséquent, le risque de rencontrer une erreur de mémoire insuffisante est plus important pendant l'exécution de la demande.|  
|request_max_cpu_time_sec|**int**|Limite maximale d'utilisation de l'UC, en secondes, pour une demande unique. La valeur par défaut 0 spécifie qu'il n'y a pas de limite. N'accepte pas la valeur NULL.<br /><br /> **Remarque :** Pour plus d’informations, consultez [Classe d’événements CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|request_memory_grant_timeout_sec|**Int**|Délai d'allocation de mémoire, en secondes, pour une demande unique. La valeur par défaut 0 utilise un calcul interne basé sur le coût de requête. N'accepte pas la valeur NULL.|  
|max_dop|**int**|Degré maximal de parallélisme pour le groupe de charges de travail. La valeur par défaut 0 utilise des paramètres globaux. N'accepte pas la valeur NULL.<br /><br /> **Nœud :** Ce paramètre remplace l’option de requête **maxdop**.|  
|group_max_requests|**int**|Nombre maximal de demandes simultanées. La valeur par défaut 0 spécifie qu'il n'y a pas de limite. N'accepte pas la valeur NULL.|  
|pool_id|**int**|ID du pool de ressources utilisé par ce groupe de charges de travail.|  
|external_pool_id|**int**|**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> ID du pool de ressources externe qui utilise ce groupe de charge de travail.|  
  
## <a name="remarks"></a>Notes  
 L'affichage catalogue affiche les métadonnées stockées. Pour afficher la configuration en mémoire, utilisez la vue de gestion dynamique correspondante, [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md).  
  
 La configuration stockée et en mémoire peut être différente si la configuration du gouverneur de ressources a été modifiée mais que l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE n'a pas été appliquée.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW ANY DEFINITION pour consulter le contenu, requiert l'autorisation CONTROL SERVER pour modifier le contenu.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue du gouverneur de ressources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)  
  
  
