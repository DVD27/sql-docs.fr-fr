---
title: Comment créer une procédure stockée à l’aide de sqlrutils
description: Utilisez le package R sqlrutils dans SQL Server pour regrouper du code de langage R dans une fonction unique qui peut être passée comme argument à une procédure stockée.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 22faeb2ea9f3e2104c2c1921b91a26ec5068079e
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715703"
---
# <a name="create-a-stored-procedure-using-sqlrutils"></a>Créer une procédure stockée à l’aide de sqlrutils
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les étapes de conversion de votre code R pour qu’il s’exécute en tant que procédure stockée T-SQL. Pour de meilleurs résultats, vous devrez peut-être modifier un peu votre code pour être sûr que toutes les entrées peuvent être paramétrées.

## <a name="bkmk_rewrite"></a>Étape 1. Réécrire le script R

Pour obtenir les meilleurs résultats, vous devez réécrire votre code R pour l’encapsuler en tant que fonction unique.

Toutes les variables utilisées par la fonction doivent être définies à l’intérieur de la fonction ou définies en tant que paramètres d’entrée. Consultez l' [exemple de code](#samples) dans cet article.

En outre, étant donné que les paramètres d’entrée de la fonction R deviendront les paramètres d’entrée de la procédure stockée SQL, vous devez vous assurer que vos entrées et sorties sont conformes aux exigences de type suivantes:

### <a name="inputs"></a>Entrées

Parmi les paramètres d’entrée, il peut y avoir au plus une trame de données.

Les objets à l’intérieur de la trame de données, ainsi que tous les autres paramètres d’entrée de la fonction, doivent être des types de données R suivants :
- POSIXct
- numérique
- caractère
- entier
- logique
- brut

Si un type d’entrée n’est pas l’un des types ci-dessus, il doit être sérialisé et transmis à la fonction en tant que type *brut*. Dans ce cas, la fonction doit également inclure du code pour désérialiser l’entrée.

### <a name="outputs"></a>Outputs

La fonction peut générer l’une des sorties suivantes :

- Une trame de données contenant les types de données pris en charge. Tous les objets dans la trame de données doivent utiliser l’un des types de données pris en charge.
- Une liste nommée contenant au plus une trame de données. Tous les membres de la liste doivent utiliser l’un des types de données pris en charge.
- Une valeur NULL, si la fonction ne retourne pas de résultat.

## <a name="step-2-generate-required-objects"></a>Étape 2. Générer les objets requis

Une fois que votre code R a été nettoyé et peut être appelé en tant que fonction unique, vous allez utiliser les fonctions du package **sqlrutils** pour préparer les entrées et les sorties dans un format qui peut être passé au constructeur qui crée réellement la procédure stockée.

**sqlrutils** fournit des fonctions qui définissent le schéma et le type des données d’entrée, et définissent le schéma et le type des données de sortie. Il comprend également des fonctions qui peuvent convertir des objets R vers le type de sortie requis. Vous pouvez effectuer plusieurs appels de fonction pour créer les objets requis, en fonction des types de données utilisés par votre code.

### <a name="inputs"></a>Entrées

Si votre fonction prend des entrées, pour chaque entrée, appelez les fonctions suivantes:

- `setInputData`Si l’entrée est une trame de données
- `setInputParameter`pour tous les autres types d’entrée

Lorsque vous effectuez chaque appel de fonction, un objet R est créé, que vous passerez ultérieurement comme argument `StoredProcedure`à pour créer la procédure stockée complète.

### <a name="outputs"></a>Outputs

**sqlrutils** fournit plusieurs fonctions pour convertir des objets R tels que des listes en données. Frame requis par SQL Server.
Si votre fonction génère une trame de données directement, sans l’encapsuler au préalable dans une liste, vous pouvez ignorer cette étape.
Vous pouvez également ignorer cette étape si votre fonction retourne la valeur NULL.

Lors de la conversion d’une liste ou de l’obtention d’un élément particulier d’une liste, choisissez l’une des fonctions suivantes:

- `setOutputData`Si la variable à obtenir de la liste est une trame de données
- `setOutputParameter`pour tous les autres membres de la liste

Lorsque vous effectuez chaque appel de fonction, un objet R est créé, que vous passerez ultérieurement comme argument `StoredProcedure`à pour créer la procédure stockée complète.

## <a name="step-3-generate-the-stored-procedure"></a>Étape 3. Générer la procédure stockée

Lorsque tous les paramètres d’entrée et de sortie sont prêts, effectuez un `StoredProcedure` appel au constructeur.

**Utilisation**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

Pour illustrer cela, supposons que vous souhaitez créer une procédure stockée nommée **sp_rsample** avec les paramètres suivants:

- Utilise une fonction existante **foosql**. La fonction était basée sur du code existant dans R Function **foo**, mais vous avez réécrit la fonction pour qu’elle soit conforme aux exigences comme décrit dans [cette section](#bkmk_rewrite)et nommé la fonction mise à jour en tant que **foosql**.
- Utilise la trame de données **queryinput** comme entrée
- Génère comme sortie une trame de données avec le nom de la variable R, **SQLOutput**
- Vous souhaitez créer le code T-SQL sous la forme d’un fichier `C:\Temp` dans le dossier, afin de pouvoir l’exécuter à l’aide de SQL Server Management Studio plus tard

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> Étant donné que vous écrivez le fichier dans le système de fichiers, vous pouvez omettre les arguments qui définissent la connexion à la base de données.

La sortie de la fonction est une procédure stockée T-SQL qui peut être exécutée sur une instance de SQL Server 2016 (nécessite R services) ou SQL Server 2017 (requiert Machine Learning Services avec R). 

Pour obtenir des exemples supplémentaires, consultez l’aide du package `help(StoredProcedure)` en appelant à partir d’un environnement R.

## <a name="step-4-register-and-run-the-stored-procedure"></a>Étape 4. Inscrire et exécuter la procédure stockée

Vous pouvez exécuter la procédure stockée de deux manières:

- À l’aide de T-SQL, depuis n’importe quel client qui prend en charge les connexions à l’instance SQL Server 2016 ou SQL Server 2017
- À partir d’un environnement R

Les deux méthodes requièrent que la procédure stockée soit enregistrée dans la base de données où vous avez l’intention d’utiliser la procédure stockée.

### <a name="register-the-stored-procedure"></a>Inscrire la procédure stockée

Vous pouvez inscrire la procédure stockée à l’aide de R, ou vous pouvez exécuter l’instruction CREATe PROCEDURE dans T-SQL.

- À l’aide de T-SQL.  Si vous vous sentez plus à l’aise avec T-SQL, ouvrez SQL Server Management Studio (ou tout autre client qui peut exécuter des commandes DDL SQL) et exécutez l’instruction CREATE PROCEDURE à `StoredProcedure` l’aide du code préparé par la fonction.
- À l’aide de R. Si vous êtes toujours dans votre environnement R, vous pouvez utiliser la `registerStoredProcedure` fonction dans **sqlrutils** pour enregistrer la procédure stockée avec la base de données.

  Par exemple, vous pouvez inscrire la procédure stockée **sp_rsample** dans l’instance et la base de données définies dans *sqlConnStr*, en effectuant cet appel R:

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> Que vous utilisiez R ou SQL, vous devez exécuter l’instruction à l’aide d’un compte disposant des autorisations nécessaires pour créer des objets de base de données.

### <a name="run-using-sql"></a>Exécuter à l’aide de SQL

Une fois la procédure stockée créée, ouvrez une connexion à la base de données SQL à l’aide de n’importe quel client qui prend en charge T-SQL et transmettez les valeurs des paramètres requis par la procédure stockée.

### <a name="run-using-r"></a>Exécuter à l’aide de R

Une préparation supplémentaire est nécessaire si vous souhaitez exécuter la procédure stockée à partir du code R, plutôt qu’à partir de SQL Server. Par exemple, si la procédure stockée requiert des valeurs d’entrée, vous devez définir ces paramètres d’entrée avant que la fonction puisse être exécutée, puis passer ces objets à la procédure stockée dans votre code R.

L’ensemble du processus d’appel de la procédure stockée SQL préparée est le suivant:

1. Appelez `getInputParameters` pour obtenir une liste d’objets de paramètres d’entrée.
2. Définissez un `$query` ou un `$value` pour chaque paramètre d’entrée.
3. Utilisez `executeStoredProcedure` pour exécuter la procédure stockée à partir de l’environnement de développement R, en passant la liste des objets de paramètres d’entrée que vous avez définis.

## <a name = "samples"></a>Tels

Cet exemple montre les versions avant et après d’un script R qui obtient des données d’une base de données SQL Server, effectue certaines transformations sur les données et les enregistre dans une autre base de données.

Cet exemple simple est utilisé uniquement pour montrer comment vous pouvez réorganiser votre code R pour faciliter la conversion en une procédure stockée.

### <a name="before-code-preparation"></a>Avant la préparation du code


```R
sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineSrc;Trusted_Connection=Yes;"
  
sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineTest;Trusted_Connection=Yes;"
  
sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"
  
dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
xFunc <- function(data) {
    data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
    return(data)
    }
  
xVars <- c("CRSDepTime")
  
sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
rxOpen(dsSqlFrom)
rxOpen(dsSqlTo)
  
if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo))   {
    rxSqlServerDropTable("cleanData")}
  
rxDataStep(inData = dsSqlFrom, 
     outFile = dsSqlTo,
     transformFunc = xFunc,
     transformVars = xVars,
     overwrite = TRUE)
```

> [!NOTE]
> 
> Lorsque vous utilisez une connexion ODBC au lieu d’appeler la fonction *RxSqlServerData* , vous devez ouvrir la connexion à l’aide de *rxOpen* avant de pouvoir effectuer des opérations sur la base de données.


### <a name="after-code-preparation"></a>Après la préparation du code

Dans la version mise à jour, la première ligne définit le nom de la fonction. Tout autre code de la solution R d’origine devient une partie de cette fonction.

```R
myetl1function <- function() { 
   sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=Airline01;Trusted_Connection=Yes;"
   sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer02;Database=Airline02;Trusted_Connection=Yes;"
    
   sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"

   dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
   dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
   xFunc <- function(data) {
     data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
     return(data)}
  
   xVars <- c("CRSDepTime")
  
   sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
   if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo)) {rxSqlServerDropTable("cleanData")}
  
   rxDataStep(inData = dsSqlFrom, 
        outFile = dsSqlTo,
        transformFunc = xFunc,
        transformVars = xVars,
        overwrite = TRUE)
   return(NULL)
}
```

> [!NOTE]
> 
> Bien que vous n’ayez pas besoin d’ouvrir la connexion ODBC explicitement dans le cadre de votre code, une connexion ODBC est quand même nécessaire pour utiliser **sqlrutils**.

## <a name="see-also"></a>Voir aussi

[sqlrutils (SQL)](ref-r-sqlrutils.md)


