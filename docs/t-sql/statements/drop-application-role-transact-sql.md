---
title: DROP APPLICATION ROLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_APPLICATION_ROLE_TSQL
- DROP APPLICATION ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- dropping application roles
- deleting application roles
- removing application roles
- application roles [SQL Server], removing
- DROP APPLICATION ROLE statement
ms.assetid: 44121ee7-ef40-405d-b03b-f8ddb4e3c559
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 251394047af1e37c505308c830e1428f163b81c6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85766560"
---
# <a name="drop-application-role-transact-sql"></a>DROP APPLICATION ROLE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Supprime un rôle d'application de la base de données active.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP APPLICATION ROLE rolename  
```  
  
## <a name="arguments"></a>Arguments  
 *rolename*  
 Spécifie le nom du rôle d'application à supprimer.  
  
## <a name="remarks"></a>Notes  
 Si le rôle d'application possède des éléments sécurisables, il ne peut pas être supprimé. Avant de supprimer un rôle d'application propriétaire d'éléments sécurisables, vous devez transférer la propriété de ces éléments sécurisables ou les supprimer.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER ANY APPLICATION ROLE sur la base de données.  
  
## <a name="examples"></a>Exemples  
 Suppression du rôle d'application « weekly_ledger » dans la base de données  
  
```  
DROP APPLICATION ROLE weekly_ledger;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles d’application](../../relational-databases/security/authentication-access/application-roles.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [ALTER APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
