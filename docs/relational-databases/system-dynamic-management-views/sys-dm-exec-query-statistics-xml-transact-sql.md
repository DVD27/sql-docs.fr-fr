---
title: sys.dm_exec_query_statistics_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 06091ffc26ea036a4a0bd7e30196545bcaca60d3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936947"
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Retourne plan de requête d’exécution pour les demandes en cours. Utilisez cette vue de gestion dynamique pour récupérer de showplan XML avec des statistiques temporaires. 

## <a name="syntax"></a>Syntaxe

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Arguments 
*session_id*  
 L’id de session exécute le lot à rechercher. *session_id* est **smallint**. *session_id* peut être obtenu à partir d’objets de gestion dynamique suivants :  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Table retournée

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|ID de la session. N'accepte pas la valeur NULL.|
|request_id|**int**|ID de la demande. N'accepte pas la valeur NULL.|
|sql_handle|**varbinary(64)**|Est un jeton qui identifie de façon unique le lot ou une procédure stockée qui fait partie de la requête. Autorise la valeur Null.|
|plan_handle|**varbinary(64)**|Est un jeton qui identifie de façon unique un plan d’exécution de requête pour un lot en cours d’exécution. Autorise la valeur Null.|
|query_plan|**xml**|Contient la représentation sous forme de plan d’exécution du plan de requête d’exécution qui est spécifié avec runtime *plan_handle* contenant des statistiques partielles. Le plan d'exécution de requêtes est au format XML. Un plan est généré pour chaque traitement contenant par exemple des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ad hoc, des appels de procédures stockées et des appels de fonctions définies par l'utilisateur. Autorise la valeur Null.|

## <a name="remarks"></a>Notes
Cette fonction système est disponible à partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1. Consultez la base de connaissances [3190871](https://support.microsoft.com/en-us/help/3190871)

Cette fonction système fonctionne dans les répertoires **standard** et **léger** infrastructure de profilage des statistiques d’exécution de requête. Pour plus d’informations, consultez [Infrastructure du profilage de requête](../../relational-databases/performance/query-profiling-infrastructure.md).  

Dans les conditions suivantes, aucune sortie Showplan n’est retournée dans le **query_plan** colonne de la table retournée pour **sys.dm_exec_query_statistics_xml**:  
  
-   Si le plan de requête qui correspond à spécifié *session_id* n’est plus exécuté, le **query_plan** colonne de la table retournée est null. Par exemple, ceci peut se produire s’il existe un délai entre le moment où le descripteur de plan est capturé et lorsqu’il a été utilisé avec **sys.dm_exec_query_statistics_xml**.  
    
En raison d’une limitation du nombre de niveaux imbriqués autorisés dans les **xml** type de données, **sys.dm_exec_query_statistics_xml** ne peut pas retourner des plans de requête qui correspondent ou sont supérieurs à 128 niveaux d’éléments imbriqués. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette condition empêchait les retours par le plan de requête et générait l'erreur 6335. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 et versions ultérieures, le **query_plan** colonne retourne NULL.   

## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation `VIEW SERVER STATE` sur le serveur.  

## <a name="examples"></a>Exemples  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>R. Examinez les statistiques de plan et l’exécution des requêtes actives pour un lot en cours d’exécution  
 L’exemple suivant interroge **sys.dm_exec_requests** pour rechercher la requête vous intéresse et copie son `session_id` à partir de la sortie.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Ensuite, pour obtenir les statistiques de plan et l’exécution de requêtes actives, utilisez le texte copié `session_id` avec la fonction système **sys.dm_exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 Ou combiné pour toutes les demandes en cours d’exécution.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>Voir aussi
  [Indicateurs de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

