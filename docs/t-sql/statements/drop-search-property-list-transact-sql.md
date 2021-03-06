---
title: DROP SEARCH PROPERTY LIST (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_SEARCH_PROPERTY_LIST_TSQL
- DROP SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- DROP SEARCH PROPERTY LIST statement
- search property lists [SQL Server], dropping
- search property lists [SQL Server], deleting
ms.assetid: 7c7ce52a-6b77-4a1c-9abf-d5feb664bea8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 746d2f33d780e4eada7accabdd029998c9e61742
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070183"
---
# <a name="drop-search-property-list-transact-sql"></a>DROP SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Supprime une liste de propriétés de la base de données actuelle si la liste de propriétés de recherche n'est pas associée actuellement à un index de recherche en texte intégral dans la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP SEARCH PROPERTY LIST property_list_name  
;  
```  
  
## <a name="arguments"></a>Arguments  
 *property_list_name*  
 Nom de la liste de propriétés de recherche à supprimer. *property_list_name* est un identificateur.  
  
 Pour consulter les noms des listes de propriétés existantes, utilisez la vue de catalogue [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md), comme suit :  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez pas supprimer de liste de propriétés de recherche d'une base de données tant que la liste est associée à un index de recherche en texte intégral, et toute tentative dans ce sens échoue. Pour supprimer une liste de propriétés de recherche d’un index de recherche en texte intégral donné, utilisez l’instruction [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) et spécifiez la clause SET SEARCH PROPERTY LIST avec OFF ou le nom d’une autre liste de propriétés de recherche.  
  
 **Pour consulter les listes de propriétés sur une instance de serveur**  
  
-   [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 **Pour consulter les listes de propriétés associées aux index de recherche en texte intégral**  
  
-   [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
 **Pour supprimer une liste de propriétés d’un index de recherche en texte intégral**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation CONTROL dans la liste de propriétés de recherche.  
  
> [!NOTE]  
>  Le propriétaire d'une liste de propriétés peut accorder des autorisations CONTROL sur la liste. Par défaut, l'utilisateur qui crée une liste de propriétés de recherche est son propriétaire. Il est possible de changer le propriétaire à l’aide de l’instruction [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la liste de propriétés `JobCandidateProperties` de la base de données `AdventureWorks2012`.  
  
```  
DROP SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
  
