---
title: Charger des données avec Integration Services - Parallel Data Warehouse | Microsoft Docs
description: Fournit des informations de référence et de déploiement pour le chargement des données dans Parallel Data Warehouse (PDW) à l’aide des packages SQL Server Integration Services (SSIS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 90d9f7422a3073df79a93949b3b7ed2e94208412
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960670"
---
# <a name="load-data-with-integration-services-to-parallel-data-warehouse"></a>Charger des données avec Integration Services à Parallel Data Warehouse
Fournit des informations de référence et de déploiement pour le chargement de données dans SQL Server Parallel Data Warehouse à l’aide des packages SQL Server Integration Services (SSIS).  
  
<!-- MISSING LINKS

## <a name="BeforeBegin"></a>Before You Begin  
Before you can start loading data, use the following topics to install the Integration Services Destination Adapters and to create an Integration Services package that connects SQL Server PDW:  


-   [Install Integration Services destination adapters](install-integration-services-destination-adapters.md)  
  
-   [Connect With Integration Services for loading](connect-with-ssis-for-loading.md)  
  
For general information about developing Integration Services packages, see [Designing and Implementing Packages (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx) on MSDN.  

-->
  
## <a name="Basics"></a>Principes de base  
Integration Services est le composant de SQL Server pour l’extraction de hautes performances, de transformation et chargement (ETL) de données et est couramment utilisé pour remplir et mettre à jour d’un entrepôt de données.  
  
L’adaptateur de Destination PDW est un composant des Services d’intégration qui vous permet de charger des données dans PDW à l’aide des packages Integration Services dtsx. Dans un workflow de package pour SQL ServerPDW, vous pouvez charger et fusionner des données provenant de plusieurs sources et charger des données vers plusieurs destinations. Les charges se produisent en parallèle, toutes les deux dans un package et entre plusieurs packages s'exécutant simultanément, avec un maximum de 10 charges s'exécutant en parallèle sur la même appliance.  
  
Outre les tâches décrites dans cette rubrique, vous pouvez utiliser d’autres fonctionnalités des Services d’intégration pour filtrer, transformer, analyser et nettoyer vos données avant de les charger dans l’entrepôt de données. Vous pouvez également améliorer le flux de travail du package en exécutant des instructions SQL, en exécutant des packages enfants ou en envoyant des messages électroniques.  
  
Pour obtenir une documentation complète d’Integration Services, consultez [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).  
  
## <a name="HowToDeployPackage"></a>Méthodes pour l’exécution d’un package Integration Services  
Utiliser une des méthodes suivantes pour exécuter un package Integration Services.  
  
### <a name="run-from-sql-server-2008-r2-business-intelligence-development-studio-bids"></a>Exécuter à partir de SQL Server 2008 R2 Business Intelligence Development Studio (BIDS)  
Pour exécuter le package à partir de BIDS, avec le bouton droit sur votre package et choisissez **exécuter le Package**.  
  
Par défaut, BIDS exécute des packages à l’aide des fichiers binaires 64 bits. Cela est déterminé par le **Run64BitRuntime** propriété du package. Pour définir cette propriété, accédez à **l’Explorateur de solutions**, avec le bouton droit sur votre projet et choisissez **propriétés**. Sur le **Pages de propriétés Integration Services**, accédez à **propriétés de Configuration** et sélectionnez **débogage**. Vous verrez la **Run64BitRuntime** propriété sous la **Options déboguer**. Pour utiliser des runtimes 32 bits, affectez la valeur **False**. Pour utiliser des runtimes 64 bits, affectez la valeur **True**.  
  
### <a name="run-from-sql-server-2012-sql-server-data-tools"></a>Exécuter à partir de SQL Server 2012 SQL Server Data Tools  
Pour exécuter le package à partir de SQL Server Data Tools, avec le bouton droit sur votre package et choisissez **exécuter le Package**.  
  
### <a name="run-from-powershell"></a>Exécuter à partir de PowerShell  
Pour exécuter le package à partir de Windows PowerShell, à l’aide de la **dtexec** utilitaire : `dtexec /FILE <packagePath>`  
  
Par exemple : `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
### <a name="run-from-a-windows-command-prompt"></a>Invite de commandes de s’exécuter à partir de Windows 
Pour exécuter le package à partir d’une invite de commandes Windows, à l’aide de la **dtexec** utilitaire : `dtexec /FILE <packagePath>`  
  
Par exemple : `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
## <a name="DataTypes"></a>Types de données  
Lorsque vous utilisez les Services d’intégration pour charger des données à partir d’une source de données dans une base de données SQL Server PDW, les données sont tout d’abord mappées à partir de la source de données aux types de données Integration Services. Cela permet à des données provenant de plusieurs sources de données d'être mappées à un ensemble commun de types de données.  
  
Puis les données sont mappées à partir des Services d’intégration pour les types de données SQL Server PDW. Pour chaque type de données SQL Server PDW, le tableau suivant répertorie les types de données Integration Services qui peuvent être convertis au type de données SQL Server PDW.  
  
|Type de données PDW|Integration Services types de données (s) correspondant au type de données PDW|  
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|  
|BIT|DT_BOOL|  
|BIGINT|DT_I1, DT_I2, DT_I4, DT_I8, DT_UI1, DT_UI2, DT_UI4|  
|CHAR|DT_STR|  
|DATE|DT_DBDATE|  
|DATETIME|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIME2|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIMEOFFSET|DT_WSTR|  
|DECIMAL|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|FLOAT|DT_R4, DT_R8|  
|INT|DT_I1, DTI2, DT_I4, DT_UI1, DT_UI2|  
|MONEY|DT_CY|  
|NCHAR|DT_WSTR|  
|NUMERIC|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|NVARCHAR|DT_WSTR, DT_STR|  
|REAL|DT_R4|  
|SMALLDATETIME|DT_DBTIMESTAMP2|  
|SMALLINT|DT_I1, DT_I2, DT_UI1|  
|SMALLMONEY|DT_R4|  
|TIME|DT_WSTR|  
|TINYINT|DT_I1|  
|VARBINARY|DT_BYTES|  
|VARCHAR|DT_STR|  
  
**Prise en charge limitée pour la précision du type de données**  
  
PDW génère une erreur de validation si vous mappez une colonne d’entrée DT_NUMERIC ou DT_DECIMAL qui contient une valeur avec une précision supérieure à 28.  
  
**Types de données non pris en charge**  
  
SQL Server PDW ne prend pas en charge les types de données Integration Services suivants :  
  
-   DT_DBTIMESTAMPOFFSET  
  
-   DT_DBTIME2  
  
-   DT_GUID  
  
-   DT_IMAGE  
  
-   DT_NTEXT  
  
-   DT_TEXT  
  
Pour charger les colonnes qui contiennent ces types de données dans SQL Server PDW, vous devez ajouter une transformation de Conversion de données en amont du flux de données pour convertir les données à un type de données compatible.  
  
## <a name="permissions"></a>Autorisations  
Pour exécuter un package de charge d’Integration Services, vous devez :  
  
-   Autorisation de la charge sur la base de données.  
  
-   Applicable INSERT, UPDATE, les autorisations de suppression sur la table de destination.  
  
-   Si une base de données intermédiaire est utilisé, l’autorisation créer sur la base de données intermédiaire. Il s’agit pour la création d’une table temporaire.  
  
-   Si aucune base de données intermédiaire n’est utilisé, l’autorisation créer sur la base de données de destination. Il s’agit pour la création d’une table temporaire.  
  
## <a name="GenRemarks"></a>Remarques d’ordre générales  
Lorsqu’un package Integration Services a plusieurs destinations de SQL Server PDW en cours d’exécution et l’une des connexions est arrêtée, Integration Services cesse de publier des données pour toutes les destinations de SQL Server PDW.  
  
## <a name="Limits"></a>Limitations et restrictions  
Pour un package Integration Services, le nombre de destinations de SQL Server PDW pour la même source de données est limité par le nombre maximal de charges actives. Le maximum est préconfiguré et n'est pas configurable par l'utilisateur. 

<!-- MISSING LINKS
For the maximum number of loads and queued loads per appliance, see [Minimum and maximum values](minimum-and-maximum-values.md).  
-->
  
Chaque destination de package Integration Services pour la même source de données compte comme une seule charge lorsque le package est en cours d’exécution. Supposons, par exemple, que le nombre maximal de charges actives soit de 10. Le package ne s'exécute pas s'il tente d'ouvrir 11 destinations ou plus pour la même source de données.  
  
Plusieurs packages peuvent s'exécuter simultanément à condition que chaque package n'utilise pas plus de charges actives que le nombre maximal. Par exemple, si le nombre maximal de charges actives est de 10, vous pouvez exécuter simultanément deux packages qui utilisent chacun 10 destinations. Un package s'exécute pendant que l'autre attend dans la file d'attente des charges.  
  
Si le nombre de charges présentes dans la file d'attente des charges dépasse le nombre maximal de charges mises en file d'attente, le package ne s'exécute pas. Par exemple, si le nombre maximal de charges est de 10 par appliance et que le nombre maximal de charges en file d’attente est de 40 par appliance, vous pouvez exécuter simultanément cinq packages Integration Services qui ouvrent chacun 10 destinations. Si vous essayez d'exécuter un sixième package, il ne s'exécute pas.  

> [!IMPORTANT]
> À l’aide d’une source de données OLE DB dans SSIS avec l’adaptateur de destination PDW, peut entraîner une altération des données si la table source contient les colonnes char et varchar avec des classements SQL. Nous vous recommandons d’utiliser une source ADO.NET si la table source contient les colonnes char ou varchar avec des classements SQL. 

  
## <a name="Locks"></a>Comportement de verrouillage  
Lors du chargement des données avec Integration Services, SQL ServerPDW utilise des verrous au niveau des lignes à mettre à jour des données dans la table de destination. Cela signifie que chaque ligne est verrouillée en lecture et en écriture pendant sa mise à jour. Les lignes de la table de destination ne sont pas verrouillées pendant le chargement des données dans la table de mise en lots.  
  
## <a name="Examples"></a>Exemples  
  
### <a name="Walkthrough"></a>A. Charge simple de fichier plat  
La procédure suivante montre un chargement de données simple à l’aide d’Integration Services pour charger des données de fichier plat vers une appliance de SQL Server PDW.  Cet exemple suppose que les Services d’intégration a déjà été installé sur l’ordinateur client, et la destination SQL Server PDW a été installée, comme décrit ci-dessus.  
  
Dans cet exemple nous se charge selon la `Orders` table, qui a la DDL suivante. Le `Orders` table fait partie de la `LoadExampleDB` base de données.  
  
```sql  
CREATE TABLE LoadExampleDB.dbo.Orders (  
   id INT,  
   city varchar(25),  
   lastUpdateDate DATE,  
   orderDate DATE)  
;  
```  
  
Voici les données de charge :  
  
```  
id        city           lastUpdateDate     orderdate  
--------- -------------- ------------------ ----------  
1         Seattle        2010-05-01         2010-01-01  
2         Denver         2002-06-25         1999-01-02  
```  
  
En préparation de la charge, créer le fichier plat `exampleLoad.txt`, contenant les données de charge :  
  
```  
id,city,lastUpdateDate,orderDate  
1,Seattle,2010-05-01,2010-01-01  
2,Denver,2002-06-25,1999-01-02  
```  
  
Tout d’abord, créez un package Integration Services en procédant comme suit :  
  
1.  Dans SQL Server Data Tools \(SSDT\), sélectionnez **fichier**, **New**, puis **projet**. Sélectionnez **projet Integration Services** parmi les options proposées. Nommez ce projet `ExampleLoad`, puis cliquez sur **OK**.  
  
2.  Cliquez sur le **flux de contrôle** onglet, puis faites glisser le **Data Flow Task** à partir de la **boîte à outils** à la **flux de contrôle** volet.  
  
3.  Cliquez sur le **de flux de données** onglet, puis faites glisser **Source de fichier plat** à partir de la **boîte à outils** à la **de flux de données** volet. Double-cliquez sur la zone que vous venez de créer pour ouvrir la **éditeur de Source de fichier plat**.  
  
4.  Cliquez sur **Gestionnaire de connexions** puis cliquez sur **New**.  
  
5.  Dans le **nom de gestionnaire de connexion** , entrez un nom convivial pour la connexion. Pour cet exemple, `Example Load Flat File CM`.  
  
6.  Cliquez sur **Parcourir** et sélectionnez le `ExampleLoad.txt` fichier à partir de l’ordinateur local.  
  
7.  Dans la mesure où le fichier plat contient une ligne avec les noms de colonnes, cliquez sur le **des noms de colonnes dans la première ligne de données** boîte.  
  
8.  Cliquez sur **colonnes** dans la colonne de gauche et l’aperçu les données qui seront chargées pour vous assurer que les noms de colonnes et les données ont été interprétées correctement.  
  
9. Cliquez sur **avancé** dans la colonne de gauche. Cliquez sur chaque nom de colonne pour passer en revue le type de données qui a été associé aux données. Tapez les modifications dans la zone afin que les types de données des données chargées seront compatibles avec les types de colonnes de destination.  
  
10. Cliquez sur **OK** pour enregistrer votre gestionnaire de connexions.  
  
11. Cliquez sur **OK** pour quitter le **éditeur de Source de fichier plat**.  
  
Spécifiez la destination pour le flux de données.  
  
1.  Faites glisser le **Destination SQL Server PDW** à partir de la **boîte à outils** à la **de flux de données** volet.  
  
2.  Double-cliquez sur la zone que vous venez de créer pour charger le **éditeur de Destination SQL Server PDW**.  
  
3.  Cliquez sur la flèche vers le bas en regard **Gestionnaire de connexions**.  
  
4.  Sélectionnez **créer une nouvelle connexion**.  
  
5.  Remplissez les informations relatives à la base de données de serveur, d’utilisateur, de mot de passe et de destination avec les informations spécifiques à votre appliance. (Les exemples sont présentés ci-dessous). Cliquez ensuite sur **OK**.  
  
    Pour les connexions InfiniBand, **nom du serveur**: Entrez < nom du matériel >-SQLCTL01, 17001.  
  
    Pour les connexions Ethernet, **nom du serveur**: Entrez l’adresse IP du cluster de nœud de contrôle, virgules, le port 17001. Par exemple, 10.192.63.134,17001.  
  
    **Utilisateur :** `user1`  
  
    **Mot de passe :** `password1`  
  
    **Base de données de destination :** `LoadExampleDB`  
  
6.  Sélectionnez la table de destination : `Orders`.  
  
7.  Sélectionnez **Append** comme le mode de chargement et cliquez sur **OK**.  
  
Spécifiez le flux de données à partir de la source vers la destination.  
  
1.  Sur le **de flux de données** volet, faites glisser la flèche verte à partir de la **Source de fichier plat** boîte à la **Destination SQL Server PDW** boîte.  
  
2.  Double-cliquez sur le **Destination SQL Server PDW** zone que vous voyez le **éditeur de Destination SQL Server PDW** à nouveau. Vous devez voir les noms des colonnes à partir du fichier plat sur la gauche, sous **des colonnes d’entrée non mappées**. Vous devez voir les noms de colonnes à partir de la table de destination à droite, sous **des colonnes de Destination non mappées**. Mappez les colonnes en faisant glisser ou en double-cliquant sur les noms de colonne correspondante dans le **des colonnes d’entrée non mappées** et **des colonnes de Destination non mappées** répertorie à la **colonnes mappées**boîte. Cliquez sur **OK** pour enregistrer vos paramètres.  
  
3.  Enregistrer le package en cliquant sur **enregistrer** dans le **fichier** menu.  
  
Exécuter le package sur votre ordinateur Integration Services.  
  
1.  Dans les Services d’intégration**l’Explorateur de solutions** (colonne de droite), avec le bouton droit `Package.dtsx` et sélectionnez **Execute**.  
  
2.  Le package s’exécute et la progression ainsi que toutes les erreurs seront affichent dans le **progression** volet. Utilisez un client SQL pour vérifier la charge, ou surveiller la charge par le biais de la Console d’administration SQL Server PDW.  
  
## <a name="see-also"></a>Voir aussi  
[Créer une tâche de script qui utilise l’adaptateur de destination SSIS PDW](create-ssis-script-task-using-pdw-destination-adapter.md)  
[SQL Server Integration Services](../integration-services/sql-server-integration-services.md)  
[Conception et implémentation de Packages (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx)  
[Tutoriel : Création d’un Package de base à l’aide d’un Assistant](https://technet.microsoft.com/library/ms365330\(v=sql11\).aspx)  
[Mise en route (Integration Services)](https://go.microsoft.com/fwlink/?LinkId=202412)  
[Exemple de génération dynamique de Package](https://go.microsoft.com/fwlink/?LinkId=202413)  
[Conception de vos Packages SSIS pour le parallélisme (vidéo liée à SQL Server)](https://msdn.microsoft.com/library/dd795221.aspx)  
[Exemples de communauté Microsoft SQL Server : Integration Services](https://go.microsoft.com/fwlink/?LinkId=202415)  
[Amélioration des chargements incrémentiels avec la Capture de données modifiées](../integration-services/change-data-capture/change-data-capture-ssis.md)  
[Transformation de dimension à variation lente](../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)  
[Tâche d’insertion en bloc](../integration-services/control-flow/bulk-insert-task.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examples](metadata-query-examples.md)
-->
