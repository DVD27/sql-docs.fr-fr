---
title: DROP USER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_USER_TSQL
- DROP USER
dev_langs:
- TSQL
helpviewer_keywords:
- dropping users
- DROP USER statement
- deleting users
- database user removal [SQL Server]
- removing users
- users [SQL Server], removing
ms.assetid: d6e0e21a-7568-4321-b6d6-bcfba183a719
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 99f4c5ac155f821dfaf69f335629730d99eb6933
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072092"
---
# <a name="drop-user-transact-sql"></a>DROP USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime un utilisateur de la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP USER [ IF EXISTS ] user_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP USER user_name  
```  
  
## <a name="arguments"></a>Arguments  
 *IF EXISTS*  
 **S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sssds](../../includes/sssds-md.md)].  
  
 Supprime, de manière conditionnelle, l’utilisateur uniquement s’il existe déjà.  
  
 *user_name*  
 Spécifie le nom qui identifie l'utilisateur dans cette base de données.  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez pas supprimer de la base de données des utilisateurs qui possèdent des éléments sécurisables. Avant de supprimer un utilisateur de base de données propriétaire d'éléments sécurisables, vous devez supprimer ou transférer la propriété de ces éléments sécurisables.  
  
 Vous ne pouvez pas supprimer l'utilisateur invité, mais vous pouvez le désactiver en révoquant son autorisation CONNECT. Pour ce faire, vous devez exécuter REVOKE CONNECT FROM GUEST dans toute base de données autre que la base master ou tempdb.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER ANY USER sur la base de données.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant supprime l'utilisateur `AbolrousHazem` de la base de données `AdventureWorks2012`.  
  
```  
DROP USER AbolrousHazem;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [ALTER USER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-user-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
