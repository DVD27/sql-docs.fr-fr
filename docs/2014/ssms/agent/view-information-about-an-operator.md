---
title: Afficher les informations relatives à un opérateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- viewing operators
- operators (users) [Database Engine], viewing with Management Studio
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- displaying operators
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9d1cab01b6fc496de90975966bfcf29b70e041fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68188748"
---
# <a name="view-information-about-an-operator"></a>Afficher des informations relatives à un opérateur
  Cette rubrique explique comment afficher des informations sur un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] opérateur de l' [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] agent dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] à [!INCLUDE[tsql](../../includes/tsql-md.md)]l’aide de ou de.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher des informations sur un opérateur, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de SQL Server Agent](sql-server-agent-fixed-database-roles.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-operator"></a>Pour afficher des informations relatives à un opérateur  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient l'opérateur que vous souhaitez afficher.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Opérateurs** .  
  
4.  Cliquez avec le bouton droit sur l’opérateur à afficher, puis sélectionnez **Propriétés**.  
  
     Pour plus d’informations sur les options disponibles contenues dans la boîte de dialogue**Propriétés** de la _operator_name_, consultez :  
  
    -   [Propriétés de l’opérateur et nouvel opérateur &#40;&#41;page général](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [Propriétés de l’opérateur : nouvel opérateur &#40;page notifications&#41;](operator-properties-new-operator-notifications-page.md)  
  
    -   [Propriétés de l’opérateur &#40;page historique&#41;](operator-properties-history-page.md)  
  
5.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-information-about-an-operator"></a>Pour afficher des informations relatives à un opérateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- reports information about operator Fran??ois Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'Fran??ois Ajenstat' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_help_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql).  
  
  
