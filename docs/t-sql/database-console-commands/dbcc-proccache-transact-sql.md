---
title: DBCC PROCCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
author: pmasl
ms.author: umajay
ms.openlocfilehash: 7720324915ea147cf5cac938c196957a6cb04c51
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68116461"
---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Affiche des informations sous forme de table relatives au cache de procédure.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Arguments  
 WITH  
 Permet de spécifier des options.  
  
 NO_INFOMSGS  
 Supprime tous les messages d'information dont le niveau de gravité est compris entre 0 et 10.  
  
## <a name="remarks"></a>Notes  
Le cache de procédure permet de mettre en cache les plans compilés et exécutables afin d'accélérer l'exécution des traitements. Les entrées d'un cache de procédure sont situées à un niveau de traitement. Le cache de procédure comporte les entrées suivantes :
-   Plans compilés  
-   Plans d'exécution  
-   Arborescence d'algébrisation  
-   Procédures étendues  
  
## <a name="result-sets"></a>Jeux de résultats  
Le tableau suivant décrit les colonnes du jeu de résultats.
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**num proc buffs**|Nombre total de pages utilisées par toutes les entrées du cache de procédure.|  
|**num proc buffs used**|Nombre total de pages utilisées par toutes les entrées en cours d'utilisation.|  
|**num proc buffs active**|Pour compatibilité descendante uniquement. Nombre total de pages utilisées par toutes les entrées en cours d'utilisation.|  
|**proc cache size**|Nombre total d'entrées du cache de procédure.|  
|**proc cache used**|Nombre total d'entrées en cours d'utilisation.|  
|**proc cache active**|Pour compatibilité descendante uniquement. Nombre total d'entrées en cours d'utilisation.|  
  
## <a name="permissions"></a>Autorisations  
Nécessite l’appartenance au rôle de serveur fixe **sysadmin** ou au rôle de base de données fixe **db_owner** .
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
