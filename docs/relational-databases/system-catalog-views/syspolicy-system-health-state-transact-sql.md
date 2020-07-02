---
title: syspolicy_system_health_state (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 64967beda33273097015fad0656c4c8026d083d0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85663787"
---
# <a name="syspolicy_system_health_state-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Affiche une ligne pour chaque association d'expression de requête cible et de stratégie de la Gestion basée sur des stratégies. Utilisez la vue syspolicy_system_health_state pour vérifier par programme l'intégrité de la stratégie du serveur. Le tableau suivant décrit les colonnes dans la vue syspolicy_system_health_state.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|Identificateur de l'enregistrement de l'état d'intégrité de la stratégie.|  
|policy_id|**int**|Identificateur de la stratégie.|  
|last_run_date|**datetime**|Date et heure de la dernière exécution de la stratégie.|  
|target_query_expression_with_id|**nvarchar(400)**|Expression cible, dont les valeurs sont attribuées aux variables d'identité, qui définit la cible par rapport à laquelle la stratégie est évaluée.|  
|target_query_expression|**nvarchar(max)**|Expression qui définit la cible par rapport à laquelle la stratégie est évaluée.|  
|result|**bit**|État d'intégrité de cette cible par rapport à la stratégie :<br /><br /> 0 = Échec<br /><br /> 1 = Réussite|  
  
## <a name="remarks"></a>Remarques  
 La vue syspolicy_system_health_state affiche l'état le plus récent de l'expression de requête cible pour chaque stratégie active (activée). La page Explorateur d'objets et Détails de l'Explorateur d'objets [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] regroupe l'intégrité de la stratégie de cette vue pour afficher l'état d'intégrité critique.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
