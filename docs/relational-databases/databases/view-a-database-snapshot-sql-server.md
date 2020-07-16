---
title: Afficher un instantané de base de données (SQL Server) | Microsoft Docs
description: Découvrez comment afficher une capture instantanée de base de données à l’aide de SQL Server Management Studio ou de Transact-SQL.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7ba50746752b0c3531d1ae3a0b1b9d4820dea82
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727539"
---
# <a name="view-a-database-snapshot-sql-server"></a>Afficher un instantané de base de données (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique explique comment afficher un instantané de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  Pour créer, restaurer ou supprimer un instantané de base de données, vous devez impérativement utiliser [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Pour afficher un instantané de base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher un instantané de base de données**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Développez **Bases de données**.  
  
3.  Développez **Instantanés de base de données**et sélectionnez l’instantané que vous voulez afficher.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher un instantané de base de données**  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Pour répertorier les instantanés de base de données de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], interrogez la colonne **source_database_id** de l’affichage catalogue [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) pour les valeurs non-NULL.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer un instantané de base de données &#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [Rétablir une base de données dans l’état d’un instantané de base de données](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
-   [Supprimer un instantané de base de données &#40;Transact-SQL&#41;](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instantanés de base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
