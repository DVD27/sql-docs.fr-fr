---
title: Vues de compatibilité de système (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- compatibility views [SQL Server]
- system tables [SQL Server], compatibility views
- type IDs [SQL Server]
- system views [SQL Server], compatibility
- metadata [SQL Server], views
- backward compatibility [SQL Server], compatibility views
- compatibility [SQL Server], compatibility views
- backward compatibility [SQL Server], system tables
- compatibility [SQL Server], system tables
- user IDs [SQL Server]
ms.assetid: 8e4624f5-9d36-4ce7-9c9e-1fe010fa2122
author: rothja
ms.author: jroth
ms.openlocfilehash: 466dc68da1c5cef56a7debe3953ba38956bb2993
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018031"
---
# <a name="system-compatibility-views-transact-sql"></a>Vues de compatibilité de système (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Une grande partie des tables système des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont maintenant implémentées sous la forme d'un ensemble de vues. Ces vues sont connues sous le nom de vues de compatibilité car elles ont été exclusivement conçues à des fins de compatibilité descendante. Elles exposent les mêmes métadonnées que celles qui étaient disponibles dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. En revanche, elles n'exposent pas les métadonnées liées aux fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. Par conséquent, lorsque vous utilisez une nouvelle fonctionnalité (comme [!INCLUDE[ssSB](../../includes/sssb-md.md)] ou le partitionnement), vous devez impérativement utiliser les affichages catalogue.  
  
 Il existe une autre raison justifiant la mise à niveau vers les affichages catalogue : les colonnes des vues de compatibilité qui stockent les ID d'utilisateur et de type peuvent retourner la valeur NULL ou déclencher des dépassements arithmétiques. Vous pouvez en effet créer plus de 32 767 utilisateurs, groupes, rôles et types de données. Imaginons par exemple que vous devez créer 32 768 utilisateurs, puis exécuter la requête suivante : `SELECT * FROM sys.sysusers`. Si l'option ARITHABORT est activée (ON), la requête échoue en raison d'une erreur de dépassement arithmétique. Si l’option ARITHABORT est désactivée (OFF), le **uid** colonne retourne NULL.  
  
 Pour éviter ces problèmes, nous vous recommandons d'utiliser les nouveaux affichages catalogue qui peuvent gérer le nombre accru d'ID d'utilisateur et d'ID de type. Le tableau suivant recense les colonnes sujettes à ce dépassement.  
  
|Nom de la colonne|Vue de compatibilité|Vue SQL Server 2005|  
|-----------------|------------------------|--------------------------|  
|**xusertype**|**syscolumns**|**sys.columns**|  
|**usertype**|**syscolumns**|**sys.columns**|  
|**memberuid**|**sysmembers**|**sys.database_role_members**|  
|**groupuid**|**sysmembers**|**sys.database_role_members**|  
|**uid**|**sysobjects**|**sys.objects**|  
|**uid**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**Fournisseur d’autorisations**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**xusertype**|**systypes**|**sys.types**|  
|**uid**|**systypes**|**sys.types**|  
|**uid**|**sysusers**|**sys.database_principals**|  
|**altuid**|**sysusers**|**sys.database_principals**|  
|**gid**|**sysusers**|**sys.database_principals**|  
|**uid**|**syscacheobjects**|**sys.dm_exec_plan_attributes**|  
|**uid**|**sysprocesses**|**sys.dm_exec_requests**|  
  
 Lors de la référence à une base de données utilisateur, les tables de système qui ont été annoncées comme déconseillées dans SQL Server 2000 (telles que **syslanguages** ou **syscacheobjects**), sont maintenant liées à la vue de compatibilité descendante dans le **sys** schéma. Les tables SQL Server 2000 étant déconseillées depuis plusieurs versions, cette modification n'est pas considérée comme une modification avec rupture.  
  
 Exemple : Si un utilisateur crée une table utilisateur appelée **syslanguages** dans une base de données utilisateur, dans SQL Server 2008, l’instruction `SELECT * from dbo.syslanguages;` dans cette base de données retournerait les valeurs de la table utilisateur. À compter de SQL Server 2012, cette pratique retourne les données à partir de la vue système **sys.syslanguages**.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
