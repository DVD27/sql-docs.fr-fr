---
title: sys.linked_logins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dfde20205de71a302c7ba8151fc6171cecc05a08
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140679"
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne par mappage de connexion de serveur lié dans le but d'utiliser ce mappage dans les requêtes RPC et les requêtes distribuées en provenance du serveur local et à destination du serveur lié correspondant.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID du serveur dans **sys.servers**.|  
|**local_principal_id**|**int**|Serveur principal auquel s'applique le mappage.<br /><br /> 0 = générique ou public.|  
|**uses_self_credential**|**bit**|Si la valeur de la colonne est égale à 1, le mappage indique que la session doit utiliser ses propres informations d'identification ; la valeur 0 indique que la session utilise les nom et mot de passe fournis.|  
|**remote_name**|**sysname**|Nom utilisateur distant servant à la connexion. Le mot de passe est également stocké mais n'est pas exposé dans les interfaces des vues de catalogue.|  
|**modify_date**|**datetime**|Date de la dernière modification de la connexion liée.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de serveurs liés &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
