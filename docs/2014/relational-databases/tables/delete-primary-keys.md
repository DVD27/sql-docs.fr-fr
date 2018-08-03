---
title: Supprimer des clés primaires | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fec4f178208119774696b9f088824c2d32e9a22b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164182"
---
# <a name="delete-primary-keys"></a>Supprimer des clés primaires
  Vous pouvez supprimer une clé primaire dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Lorsque la clé primaire est supprimée, l'index correspondant l'est également.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une clé primaire à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a>Pour supprimer une contrainte de clé primaire à l'aide de l'Explorateur d'objets  
  
1.  Dans l'Explorateur d'objets, développez la table qui contient la clé primaire, puis développez **Clés**.  
  
2.  Cliquez avec le bouton droit sur la clé, puis sélectionnez **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer un objet** , vérifiez que la clé correcte est spécifiée et cliquez sur **OK**.  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a>Pour supprimer une contrainte de clé primaire à l'aide du Concepteur de tables  
  
1.  Dans l’Explorateur d'objets, cliquez avec le bouton droit sur la table avec la clé primaire, puis cliquez sur **Conception**.  
  
2.  Dans la grille de la table, cliquez avec le bouton droit sur la ligne contenant la clé primaire et choisissez **Supprimer la clé primaire** pour désactiver le paramètre.  
  
    > [!NOTE]  
    >  Pour annuler cette action, fermez la table sans enregistrer les modifications. La suppression d'une clé primaire ne peut pas être annulée sans perdre toutes les autres modifications apportées à la table.  
  
3.  Dans le menu **Fichier**, cliquez sur **Enregistrer***nom de la table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-primary-key-constraint"></a>Pour supprimer une contrainte de clé primaire  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple identifie d'abord le nom de la contrainte de clé primaire et supprime ensuite la contrainte.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE& #40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) et [sys.key_constraints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-constraints-transact-sql)  
  
###  <a name="TsqlExample"></a>  