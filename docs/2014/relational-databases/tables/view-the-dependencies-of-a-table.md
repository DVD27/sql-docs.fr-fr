---
title: Afficher les dépendances d’une table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f5f30232a4f6d382af6e3a21f022b86cdf1a4fd4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68196608"
---
# <a name="view-the-dependencies-of-a-table"></a>Afficher les dépendances d'une table
  Vous pouvez afficher les dépendances d’une table dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher les dépendances d’une table à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation VIEW DEFINITION sur la base de données et l'autorisation SELECT sur sys.sql_expression_dependencies pour la base de données. Par défaut, l'autorisation SELECT est accordée uniquement aux membres du rôle de base de données fixe db_owner. Lorsque les autorisations SELECT et VIEW DEFINITION sont accordées à un autre utilisateur, le bénéficiaire peut consulter toutes les dépendances dans la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-the-dependencies-of-a-table"></a>Pour afficher les dépendances d'une table  
  
1.  Dans l' **Explorateur d'objets**, développez **Bases de données**, développez une base de données, puis **Tables**.  
  
2.  Cliquez avec le bouton droit sur une table, puis cliquez sur **Afficher les dépendances**.  
  
3.  Dans la boîte de dialogue **dépendances**_\<_ d’objets nom de l’objet>, sélectionnez les **objets qui dépendent du nom de** _ \<l’objet>_ ou **les**_\< _objets dont le nom d’objet>**dépend**.  
  
4.  Sélectionnez un objet dans la grille **Dépendances** . Le type de l’objet (par exemple « déclencheur » ou « procédure stockée ») apparaît dans la zone **Type** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a>Pour afficher les objets qui dépendent d'une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a>Pour afficher les objets dont dépend une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  L'exemple suivant retourne les objets qui dépendent de la table `Production.Product`. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 Pour plus d’informations, consultez [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
