---
title: Résolution des problèmes liés aux tests unitaires de base de données SQL Server | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cf4c9cd1-7e73-4c3b-922a-68b9247e7b33
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1b7203572d01ca9f344b96a7008dd78b2e35bcdb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68110609"
---
# <a name="troubleshooting-sql-server-database-unit-testing-issues"></a>Dépannage des problèmes liés aux tests unitaires de base de données SQL Server
Vous pouvez rencontrer les problèmes présentés dans cette rubrique lorsque vous exécutez des tests unitaires SQL Server sur une base de données :  
  
-   [Modifications des tests unitaires et du fichier App.Config ignorées lors de l'exécution de tests unitaires](#UnitTestingAndAppConfigChanges)  
  
-   [Déploiement de base de données vers une cible inattendue lors de l'exécution de tests unitaires](#DatabaseDeploymentInUnitTests)  
  
-   [Délais d'expiration lors de l'exécution de tests unitaires de base de données](#TimeoutsDuringUnitTests)  
  
## <a name="UnitTestingAndAppConfigChanges"></a>Modifications des tests unitaires et du fichier App.Config ignorées lors de l'exécution de tests unitaires  
Si vous modifiez le fichier App.Config dans le projet de test, vous devez recréer le projet de test avant que les modifications prennent effet. Ces modifications incluent celles apportées au fichier App.Config en utilisant la boîte de dialogue **Configuration de test de SQL Server**. Si vous ne recréez pas le projet de test, les modifications ne sont pas appliquées lorsque vous exécutez les tests unitaires.  
  
## <a name="DatabaseDeploymentInUnitTests"></a>Déploiement de base de données vers une cible inattendue lors de l'exécution de tests unitaires  
Si vous déployez une base de données à partir d'un projet de base de données lorsque vous exécutez des tests unitaires, la base de données est déployée en utilisant les informations de la chaîne de connexion spécifiée dans la configuration des tests unitaires. Les informations de connexion spécifiées dans les propriétés de débogage du projet de base de données ne sont pas utilisées pour cette tâche, ce qui vous permet d'exécuter des tests unitaires SQL Server par rapport à différentes instances de la même base de données.  
  
## <a name="TimeoutsDuringUnitTests"></a>Délais d'expiration lors de l'exécution de tests unitaires  
Si les tests unitaire de base de données échouent en raison d'un délai d'attente, vous pouvez augmenter le délai d'attente en mettant à jour le fichier app.config dans le projet de test. Le délai d'attente de connexion, défini sur la chaîne de connexion, indique le temps d'attente lorsque le test unitaire se connecte au serveur. Le délai d'expiration de la commande, qui doit être défini directement dans le fichier app.config indique le temps d'attente lorsque le test unitaire exécute le script Transact\-SQL. Si vous rencontrez des problèmes liés aux tests unitaires de longue durée, essayez d'augmenter la valeur de délai d'attente de la commande dans l'élément de contexte approprié. Par exemple, pour indiquer un délai d'expiration de la commande de 120 secondes pour l'élément **PrivilegedContext**, mettez à jour le fichier app.config comme suit :  
  
```  
<SqlUnitTesting_VS2010>  
    <DatabaseDeployment DatabaseProjectFileName="..\..\..\..\..\..\Visual Studio 2010\Projects\Database10\Database10\AdventureWorks.sqlproj"  
        Configuration="Debug" />  
    <DataGeneration ClearDatabase="true" />  
    <ExecutionContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(LocalDB)\Projects;Initial Catalog=AdventureWorks_Test;Integrated Security=True;Pooling=False"  
        CommandTimeout="30" />  
    <PrivilegedContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(LocalDB)\Projects;Initial Catalog=AdventureWorks_Test;Integrated Security=True;Pooling=False"  
        CommandTimeout="120" />  
</SqlUnitTesting_VS2010>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Procédure : créer des tests unitaires SQL Server pour des fonctions, des déclencheurs ou des procédures stockées](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md)  
[Procédure : configurer l’exécution de test unitaire SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md)  
  
