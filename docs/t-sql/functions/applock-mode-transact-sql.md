---
title: APPLOCK_MODE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- APPLOCK_MODE_TSQL
- APPLOCK_MODE
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- APPLOCK_MODE function
ms.assetid: e43d4917-77f1-45cc-b231-68ba7fee3385
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4544cc4f0a4d7c1d6d33e1f71bde4b55c09a59c9
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68040361"
---
# <a name="applock_mode-transact-sql"></a>APPLOCK_MODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette fonction retourne le mode de verrouillage détenu par le propriétaire du verrou sur une ressource d’application particulière. En tant que fonction de verrouillage d'application, APPLOCK_MODE agit sur la base de données active. La base de données constitue l'étendue des verrous d'application.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
APPLOCK_MODE( 'database_principal' , 'resource_name' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Arguments  
'*database_principal*'  
Utilisateur, rôle ou rôle d’application qui peuvent se voir octroyer des autorisations sur des objets dans la base de données. Pour pouvoir appeler la fonction, l’appelant de la fonction doit être membre du rôle de base de données fixe *database_principal*, dbo ou db_owner.
  
'*resource_name*'  
Nom de ressource de verrouillage spécifié par l'application cliente. L'application doit garantir un nom de ressource unique. Le nom spécifié est haché en interne en une valeur que le gestionnaire de verrous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut stocker en interne. *resource_name* est de type **nvarchar(255)** , sans valeur par défaut. L’argument *resource_name* est évalué en binaire et respecte la casse, quels que soient les paramètres de classement de la base de données active.
  
'*lock_owner*'  
Propriétaire du verrou, correspondant à la valeur *lock_owner* lorsque le verrou a été demandé. *lock_owner* est de type **nvarchar(32)** et sa valeur peut être **Transaction** (valeur par défaut) ou **Session**.
  
## <a name="return-types"></a>Types de retour
**nvarchar(32)**
  
## <a name="return-value"></a>Valeur retournée
Renvoie le mode de verrouillage détenu par le propriétaire du verrou sur une ressource d'application particulière. Le mode de verrouillage peut avoir une des valeurs suivantes :
  
||||  
|-|-|-|  
|**NoLock**|**Mettre à jour**|**\*SharedIntentExclusive**|  
|**IntentShared**|**IntentExclusive**|**\*UpdateIntentExclusive**|  
|**Shared**|**Exclusive**||  
  
*Ce mode de verrouillage est une combinaison d'autres modes de verrouillage et sp_getapplock ne peut pas l'acquérir explicitement.
  
## <a name="function-properties"></a>Propriétés de la fonction
**Non déterministe**
  
**Non indexable**
  
**Non parallélisable**
  
## <a name="examples"></a>Exemples  
Deux utilisateurs (A et B) exécutent la séquence d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante dans des sessions différentes.
  
L'utilisateur A exécute :
  
```sql
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result=sp_getapplock  
    @DbPrincipal='public',  
    @Resource='Form1',  
    @LockMode='Shared',  
    @LockOwner='Transaction';  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
GO  
```  
  
L'utilisateur B exécute :
  
```sql
Use AdventureWorks2012;  
GO  
BEGIN TRAN;  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
--Result set: NoLock  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Shared', 'Transaction');  
--Result set: 1 (Lock is grantable.)  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: 0 (Lock is not grantable.)  
GO  
```  
  
L'utilisateur A exécute ensuite :
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
L'utilisateur B exécute :
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
Les utilisateurs A et B exécutent ensuite :
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[APPLOCK_TEST &#40;Transact-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)  
[sp_getapplock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  
