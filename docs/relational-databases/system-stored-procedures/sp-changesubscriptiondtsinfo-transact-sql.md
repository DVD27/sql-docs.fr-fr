---
title: sp_changesubscriptiondtsinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
author: stevestein
ms.author: sstein
ms.openlocfilehash: a091df0cbbeb2883ff9905d7c5b3718d50efa86b
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68762555"
---
# <a name="spchangesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Modifie les propriétés de package DTS (Data Transformation Services) d'un abonnement. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] job_id`ID du travail de l’Agent de distribution pour l’abonnement par émission de type push. *job_id* est de type **varbinary (16)** , sans valeur par défaut. Pour Rechercher l’ID de tâche de distribution, exécutez **sp_helpsubscription** ou **sp_helppullsubscription**.  
  
`[ @dts_package_name = ] 'dts_package_name'`Spécifie le nom du package DTS. *dts_package_name* est de **type sysname**, avec NULL comme valeur par défaut. Par exemple, pour spécifier un package nommé **DTSPub_Package**, vous devez spécifier `@dts_package_name = N'DTSPub_Package'`.  
  
`[ @dts_package_password = ] 'dts_package_password'`Spécifie le mot de passe du package. *dts_package_password* est de **type sysname** , avec NULL comme valeur par défaut, qui spécifie que la propriété de mot de passe doit rester inchangée.  
  
> [!NOTE]  
>  Un package DTS doit avoir un mot de passe.  
  
`[ @dts_package_location = ] 'dts_package_location'`Spécifie l’emplacement du package. *dts_package_location* est de type **nvarchar (12)** , avec NULL comme valeur par défaut, qui spécifie que l’emplacement du package doit rester inchangé. L’emplacement du package peut être remplacé par **Distributor** ou Subscriber.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changesubscriptiondtsinfo** est utilisé pour la réplication d’instantané et la réplication transactionnelle qui sont des abonnements par émission de type push uniquement.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** , du rôle de base de données fixe **db_owner** ou du créateur de l’abonnement peuvent exécuter **sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
