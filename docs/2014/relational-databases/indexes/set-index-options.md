---
title: Définir les options d’index | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 24587f27710381ac787fe8045029df681e401af5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63036190"
---
# <a name="set-index-options"></a>Définir les options d'index
  Cette rubrique explique comment modifier les propriétés d'un index dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour modifier les propriétés d'un index, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les options suivantes sont immédiatement appliquées à l’index à l’aide de la clause SET de l’instruction ALTER INDEX : ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY et STATISTICS_NORECOMPUTE.  
  
-   Les options suivantes peuvent toutefois être définies lorsque vous reconstruisez un index à l’aide de l’instruction ALTER INDEX REBUILD ou CREATE INDEX WITH DROP_EXISTING : PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP et DROP_EXISTING (CREATE INDEX uniquement).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite une autorisation ALTER sur la table ou la vue.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a>Pour modifier les propriétés d'un index dans le Concepteur de tables  
  
1.  Dans l’Explorateur d’objets, cliquez sur le signe plus (+) pour développer la base de données qui contient la table sur laquelle vous souhaitez modifier les propriétés d’un index.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Tables** .  
  
3.  Cliquez avec le bouton droit sur la table sur laquelle vous voulez modifier les propriétés d’un index et sélectionnez **Conception**.  
  
4.  Dans le menu **Concepteur de tables** , cliquez sur **Index/Clés**.  
  
5.  Sélectionnez l'index à modifier. Ses propriétés apparaîtront dans la grille principale.  
  
6.  Modifiez les paramètres de l'ensemble de propriétés pour personnaliser l'index.  
  
7.  Cliquez sur **Fermer**.  
  
8.  Dans le menu **Fichier** , sélectionnez **Enregistrer**_nom_table_.  
  
#### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a>Pour modifier les propriétés d'un index dans l'Explorateur d'objets  
  
1.  Dans l’Explorateur d’objets, cliquez sur le signe plus (+) pour développer la base de données qui contient la table sur laquelle vous souhaitez modifier les propriétés d’un index.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Tables** .  
  
3.  Cliquez sur le signe plus (+) pour développer la table sur laquelle vous souhaitez modifier les propriétés d’un index.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index dont vous voulez modifier les propriétés, puis sélectionnez **Propriétés**.  
  
6.  Sous **Sélectionner une page**, sélectionnez **Options**.  
  
7.  Modifiez les paramètres de l'ensemble de propriétés pour personnaliser l'index.  
  
8.  Pour ajouter, supprimer ou déplacer une colonne d’index, sélectionnez la page **Général** dans la boîte de dialogue **Propriétés de l’index -** _nom_index_ . Pour plus d'informations, consultez [Index Properties F1 Help](index-properties-f1-help.md)  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a>Pour afficher les propriétés de tous les index d'une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### <a name="to-set-the-properties-of-an-index"></a>Pour définir les propriétés d'un index  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
  
