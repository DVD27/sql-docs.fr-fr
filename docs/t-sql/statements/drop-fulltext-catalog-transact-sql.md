---
title: DROP FULLTEXT CATALOG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_FULLTEXT_CATALOG_TSQL
- DROP FULLTEXT CATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- dropping full-text catalogs
- removing full-text catalogs
- full-text catalogs [SQL Server], removing
- deleting full-text catalogs
- DROP FULLTEXT CATALOG statement
ms.assetid: b54efb0b-400b-49ce-923b-ce20a2a12255
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 03d1c92ddd48daf48f6b410e5a613f997b08640c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68044249"
---
# <a name="drop-fulltext-catalog-transact-sql"></a>DROP FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime un catalogue de texte intégral d'une base de données. Vous devez supprimer tous les index de recherche en texte intégral associés au catalogue avant de supprimer le catalogue.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP FULLTEXT CATALOG catalog_name  
```  
  
## <a name="arguments"></a>Arguments  
 *CATALOG_NAME*  
 Nom du catalogue à supprimer. Si l’argument *catalog_name* n’existe pas, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une erreur et n’exécute pas l’opération de suppression (DROP). Si le groupe de fichiers du catalogue de texte intégral est marqué OFFLINE ou READONLY, la commande échoue.  
  
## <a name="permissions"></a>Autorisations  
 L’utilisateur doit disposer de l’autorisation DROP sur le catalogue de texte intégral ou être membre du rôle de base de données fixe **db_owner** ou **db_ddladmin**.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)  
  
  
