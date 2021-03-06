---
title: sp_copysnapshot (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysnapshot
- sp_copysnapshot_TSQL
helpviewer_keywords:
- sp_copysnapshot
ms.assetid: a012a32f-6f26-45bf-8046-b51cd7fec455
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30e96ad145abdb123e5bc5540f74f23251d1a69e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768889"
---
# <a name="sp_copysnapshot-transact-sql"></a>sp_copysnapshot (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Copie le dossier d’instantané de la publication spécifiée dans le dossier indiqué dans **@destination_folder** le. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication. Elle permet de copier un instantané sur un support amovible, tel qu'un CD-ROM.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_copysnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication dont le contenu de l’instantané doit être copié. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @destination_folder = ] 'destination_folder'`Nom du dossier dans lequel le contenu de l’instantané de publication doit être copié. *destination_folder*est de type **nvarchar (255)** , sans valeur par défaut. Le *destination_folder* peut être un autre emplacement, par exemple sur un autre serveur, sur un lecteur réseau ou sur un support amovible (tel qu’un CD-ROM ou un disque amovible).  
  
`[ @subscriber = ] 'subscriber'`Nom de l’abonné. Subscriber est de type sysname, avec NULL comme valeur par défaut.  
  
`[ @subscriber_db = ] 'subscriber_db'`Nom de la base de données d’abonnement. *subscriber_db* est de type sysname, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_copysnapshot** est utilisé dans tous les types de réplications. Les abonnés [!INCLUDE[msCoName](../../includes/msconame-md.md)] qui exécutent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la version 7,0 et les versions antérieures ne peuvent pas utiliser l’autre emplacement d’instantané.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_copysnapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](../../relational-databases/replication/snapshot-options.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
