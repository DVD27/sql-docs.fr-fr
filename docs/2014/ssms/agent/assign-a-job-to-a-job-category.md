---
title: Affecter un travail à une catégorie de travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab7695b6a80772ddcd01996e783fffd806447c59
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62473200"
---
# <a name="assign-a-job-to-a-job-category"></a>Affecter un travail à une catégorie de travaux
  Cette rubrique décrit comment affecter [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des travaux de l’agent à des [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] catégories de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]travaux [!INCLUDE[tsql](../../includes/tsql-md.md)] dans à l’aide de, ou SQL Server Management Objects.  
  
 Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Par exemple, vous pouvez organiser tous vos travaux de sauvegarde de base de données dans la catégorie Maintenance de bases de données. Vous pouvez affecter des travaux à des catégories de travaux intégrées, ou vous pouvez créer une catégorie de travaux définie par l’utilisateur, à laquelle vous affectez ensuite des travaux.  
  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Pour affecter un travail à une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus pour développer le serveur sur lequel vous souhaitez affecter un travail à une catégorie de travaux.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Travaux** .  
  
4.  Cliquez avec le bouton droit sur le travail à modifier, puis sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue **Propriétés du travail-**_job_name_ , dans la liste **catégorie** , sélectionnez la catégorie de travaux que vous voulez affecter au travail.  
  
6.  Cliquez sur **OK**.  
  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Pour affecter un travail à une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).  
  
  
  
##  <a name="SMO"></a>Utilisation de SQL Server Management Objects  
 **Pour affecter un travail à une catégorie de travaux**  
  
 Utilisez la classe `JobCategory` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell.  
  
  
  
  
