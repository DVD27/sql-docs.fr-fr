---
title: Bases de données système | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b2bce8ef0c47a26ef1b1a095160ce6cc7357a00f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127364"
---
# <a name="system-databases"></a>Bases de données système

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut les bases de données système suivantes.  
  
|Base de données système|Description|  
|---------------------|-----------------|  
|[Base de données master](../../relational-databases/databases/master-database.md)|Enregistre toutes les informations système relatives à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Base de données msdb](../../relational-databases/databases/msdb-database.md)|Utilisée par l'Agent SQL Server pour planifier les alertes et les travaux.|  
|[Base de données model](../../relational-databases/databases/model-database.md)|Fait office de modèle pour toutes les bases de données créées sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les modifications apportées à la base de données **model** , telles que la taille de la base de données, le classement, le mode de récupération et les autres options de base de données, s'appliquent aux bases de données créées par la suite.|  
|[Base de données Resource](../../relational-databases/databases/resource-database.md)|Base de données en lecture seule contenant des objets système fournis avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les objets système sont conservés physiquement dans la base de données **Resource** , mais ils figurent logiquement dans le schéma **sys** de chaque base de données.|  
|[Base de données tempdb](../../relational-databases/databases/tempdb-database.md)|Espace de travail destiné à accueillir les objets temporaires ou les ensembles de résultats intermédiaires.|  

> [!IMPORTANT]
> Pour les pools élastiques et les bases de données uniques Azure SQL Database, seules les bases de données MASTER et tempdb s’appliquent. Pour plus d’informations, consultez [Qu’est-ce qu’un serveur Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-servers#what-is-an-azure-sql-database-server). Pour en savoir plus sur tempdb dans le contexte d’Azure SQL Database, consultez [Base de données tempdb dans Azure SQL Database](tempdb-database.md#tempdb-database-in-sql-database). Pour SQL Database Managed Instance, toutes les bases de données système s’appliquent. Pour plus d’informations sur les instances gérées dans Azure SQL Database, voir [Présentation des instances gérées](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
## <a name="modifying-system-data"></a>modification de données système  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne permet pas aux utilisateurs de mettre directement à jour les informations contenues dans les objets système, tels que les tables système, les procédures stockées système et les vues de catalogue. En revanche, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propose un jeu complet d'outils d'administration qui permettent aux utilisateurs d'administrer complètement leur système et de gérer tous les utilisateurs et objets d'une base de données. Ces options en question sont les suivantes :  
  
-   Utilitaires d'administration, tels que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   API SQL-SMO. Cet outil permet aux programmeurs d'inclure des fonctionnalités complètes visant à administrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans leurs applications.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] . Ceux-ci peuvent utiliser des procédures stockées système et des instructions DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Ces outils prémunissent les applications contre les modifications des objets système. Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est parfois amené à modifier les tables système dans les nouvelles versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de prendre en charge les nouvelles fonctionnalités ajoutées à cette version. Les applications qui lancent des instructions SELECT référençant directement les tables système dépendent souvent de l'ancien format des tables système. Il est possible que les sites ne soient pas en mesure de procéder à la mise à niveau vers une nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tant qu'ils n'ont pas réécrit les applications de sélection dans les tables système. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considère les procédures stockées système, DDL et SQL-SMO comme des interfaces publiées, et veille à en maintenir la compatibilité descendante.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les déclencheurs définis sur les tables système, car ils peuvent perturber le bon fonctionnement du système.  
  
> [!NOTE]  
>  Les bases de données système ne peuvent pas résider dans les répertoires partagés UNC.  
  
## <a name="viewing-system-database-data"></a>affichage de données de bases de données système  
 Vous ne devez pas coder les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui interrogent directement les tables système, sauf s'il s'agit de la seule méthode d'obtention des informations requises par l'application. Au lieu de cela, les applications doivent obtenir les informations de catalogue et du système par l'un des moyens suivants :  
  
-   Vues de catalogue système  
  
-   SQL-SMO  
  
-   Interface WMI (Windows Management Instrumentation)  
  
-   Fonctions de catalogue, méthodes, attributs ou propriétés de l'API de données utilisée dans l'application, notamment ADO, OLE DB ou ODBC.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] Procédures stockées système et fonctions intégrées.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Sauvegarde et restauration des bases de données système &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Masquer les objets système dans l'Explorateur d'objets](../../ssms/object/hide-system-objects-in-object-explorer.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
 [Bases de données](../../relational-databases/databases/databases.md)  
  
  
