---
title: sp_registercustomresolver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_registercustomresolver
- sp_registercustomresolver_TSQL
helpviewer_keywords:
- sp_registercustomresolver
ms.assetid: 6d2b0472-0e1f-4005-833c-735d1940fe93
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d003cccfa6fdedd0610ea34f15acb6ee1833e5a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075734"
---
# <a name="spregistercustomresolver-transact-sql"></a>sp_registercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet d'inscrire un gestionnaire de logique métier ou un résolveur personnalisé COM qui peut être appelé lors du processus de synchronisation de réplication de fusion. Cette procédure stockée est exécutée sur le serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_registercustomresolver [ @article_resolver = ] 'article_resolver'   
    [ , [ @resolver_clsid = ] 'resolver_clsid' ]  
    [ , [ @is_dotnet_assembly = ] 'is_dotnet_assembly' ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @article_resolver = ] 'article_resolver'` Spécifie le nom convivial pour la logique métier personnalisée en cours d’inscription. *article_resolver* est **nvarchar (255)** , sans valeur par défaut.  
  
`[ @resolver_clsid = ] 'resolver_clsid'` Spécifie la valeur CLSID de l’objet COM qui en cours d’inscription. Logique métier personnalisée *resolver_clsid* est **nvarchar (50)** , avec NULL comme valeur par défaut. Ce paramètre doit avoir pour valeur un CLSID valide ou la valeur NULL lors de l'inscription d'un assembly de gestionnaire de logique métier.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly'` Spécifie le type de logique métier personnalisée en cours d’inscription. *is_dotnet_assembly* est **nvarchar (50)** , avec FALSE comme valeur par défaut. **true** indique que la logique métier personnalisée en cours d’inscription est un gestionnaire de logique métier Assembly ; **false** indique qu’il s’agit d’un composant COM.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name'` Est le nom de l’assembly qui implémente le Gestionnaire de logique métier. *dotnet_assembly_name* est **nvarchar (255)** , avec NULL comme valeur par défaut. Vous devez spécifier le chemin d'accès complet à l'assembly si celui-ci n'est pas déployé dans le même répertoire que l'exécutable de l'Agent de fusion, que l'application qui démarre de façon synchronisée l'Agent de fusion, ou dans le GAC (Global Assembly Cache).  
  
`[ @dotnet_class_name = ] 'dotnet_class_name'` Est le nom de la classe qui remplace <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> pour implémenter le Gestionnaire de logique métier. Le nom doit être spécifié sous la forme **Namespace.Classname**. *dotnet_class_name* est **nvarchar (255)** , avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_registercustomresolver** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_registercustomresolver**.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter un gestionnaire de logique métier pour un article de fusion](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
