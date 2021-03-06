---
title: Utilisation des paramètres table | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cd5f00d551c189f583af4232fe31716b51594df
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003928"
---
# <a name="using-table-valued-parameters"></a>Utilisation de paramètres table

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL.  
  
Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard. Les paramètres table sont fortement typés et leur structure est validée automatiquement. La taille des paramètres table est limitée uniquement par la mémoire du serveur.  
  
> [!NOTE]  
> La prise en charge des paramètres table est disponible à partir du pilote Microsoft JDBC 6,0 pour SQL Server.
>
> Vous ne pouvez pas retourner de données dans un paramètre table. Les paramètres table sont des valeurs d’entrée uniquement; le mot clé OUTPUT n’est pas pris en charge.  
  
 Pour plus d’informations sur les paramètres table, consultez les ressources suivantes.  
  
| Ressource                                                                                                             | Description                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Paramètres table (moteur de base de données)](https://go.microsoft.com/fwlink/?LinkId=98363) dans documentation en ligne de SQL Server | Décrit comment créer et utiliser des paramètres table                             |
| [Types de tables définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkId=98364) dans documentation en ligne de SQL Server                  | Décrit les types de tables définis par l’utilisateur qui permettent de déclarer des paramètres table. |
| La section [moteur de base de données Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=120507) de CodePlex        | Contient des exemples qui montrent comment utiliser des fonctionnalités et fonctionnalités de SQL Server  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Passage de plusieurs lignes dans les versions précédentes de SQL Server  

Avant l’introduction des paramètres table dans SQL Server 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrable étaient limitées. Un développeur peut choisir parmi les options suivantes pour transmettre plusieurs lignes au serveur:  
  
- Utilisez une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données. La quantité de données qui peuvent être passées à l’aide de cette méthode est limitée par le nombre de paramètres autorisés. SQL Server procédures peuvent avoir, au plus, des paramètres 2100. La logique côté serveur est requise pour assembler ces valeurs individuelles dans une variable de table ou une table temporaire à des fins de traitement.  
  
- Regroupez plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis transmettez ces valeurs de texte à une procédure ou une instruction. Cela requiert que la procédure ou l’instruction inclue la logique nécessaire pour valider les structures de données et dissocier les valeurs.  
  
- Créer une série d’instructions SQL pour les modifications de données qui affectent plusieurs lignes. Les modifications peuvent être envoyées au serveur individuellement ou regroupées par lot. Toutefois, même lorsqu’elles sont soumises dans des lots contenant plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.  
  
- Utilisez le programme utilitaire bcp ou l’objet [SQLServerBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx) pour charger de nombreuses lignes de données dans une table. Bien que cette technique soit très efficace, elle ne prend pas en charge le traitement côté serveur à moins que les données ne soient chargées dans une table temporaire ou une variable de table.  
  
## <a name="creating-table-valued-parameter-types"></a>Création de types de paramètres table  

Les paramètres table sont basés sur des structures de table fortement typées qui sont définies à l’aide d' `CREATE TYPE` instructions Transact-SQL. Vous devez créer un type de table et définir la structure dans SQL Server avant de pouvoir utiliser les paramètres table dans vos applications clientes. Pour plus d’informations sur la création de types de table, consultez [types de tables définis par l’utilisateur](https://go.microsoft.com/fwlink/?LinkID=98364) dans documentation en ligne de SQL Server.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

Après avoir créé un type de table, vous pouvez déclarer des paramètres table basés sur ce type. Le fragment Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée. Notez que le `READONLY` mot clé est requis pour déclarer un paramètre table.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modification de données à l’aide de paramètres table (Transact-SQL)  

Les paramètres table peuvent être utilisés dans les modifications de données basées sur des ensembles qui affectent plusieurs lignes en exécutant une instruction unique. Par exemple, vous pouvez sélectionner toutes les lignes d’un paramètre table et les insérer dans une table de base de données, ou vous pouvez créer une instruction Update en joignant un paramètre table à la table que vous souhaitez mettre à jour.  
  
L’instruction Transact-SQL UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table categories. Lorsque vous utilisez un paramètre table avec une jointure dans une clause FROM, vous devez également créer un alias pour celui-ci, comme illustré ici, où le paramètre table est un alias avec la valeur «EC»:  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

Cet exemple Transact-SQL montre comment sélectionner des lignes à partir d’un paramètre table pour effectuer une insertion dans une opération basée sur un jeu unique.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Limitations des paramètres table

Les paramètres table présentent plusieurs limitations:  
  
- Vous ne pouvez pas passer de paramètres table aux fonctions définies par l’utilisateur.  
  
- Les paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes de clé primaire ou UNIQUE. SQL Server ne tient pas à jour de statistiques sur les paramètres table.  
  
- Les paramètres table sont en lecture seule dans le code Transact-SQL. Vous ne pouvez pas mettre à jour les valeurs de colonne dans les lignes d’un paramètre table et vous ne pouvez pas insérer ou supprimer des lignes. Pour modifier les données qui sont passées à une procédure stockée ou à une instruction paramétrée dans un paramètre table, vous devez insérer les données dans une table temporaire ou dans une variable de table.  
  
- Vous ne pouvez pas utiliser d’instructions ALTER TABLE pour modifier la conception de paramètres table.

- Vous pouvez diffuser en continu des objets volumineux dans un paramètre table.  
  
## <a name="configuring-a-table-valued-parameter"></a>Configuration d’un paramètre table

À compter de Microsoft JDBC Driver 6,0 pour SQL Server, les paramètres table sont pris en charge avec une instruction paramétrable ou une procédure stockée paramétrable. Les paramètres table peuvent être remplis à partir d’un SQLServerDataTable, d’un ResultSet ou d’une implémentation fournie par l’utilisateur de l’interface ISQLServerDataRecord. Lors de la définition d’un paramètre table pour une requête préparée, vous devez spécifier un nom de type qui doit correspondre au nom d’un type compatible précédemment créé sur le serveur.  
  
Les deux fragments de code suivants montrent comment configurer un paramètre table avec un SQLServerPreparedStatement et un SQLServerCallableStatement pour insérer des données. Ici, sourceTVPObject peut être un SQLServerDataTable, un jeu de résultats ou un objet ISQLServerDataRecord. Les exemples supposent que la connexion est un objet de connexion actif.  

```java
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =
    (SQLServerPreparedStatement) connection.prepareStatement("INSERT INTO dbo.Categories SELECT * FROM ?");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```

```java
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour la définition du paramètre table.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Passage d’un paramètre table en tant qu’objet SQLServerDataTable  

À compter de Microsoft JDBC Driver 6,0 pour SQL Server, la classe SQLServerDataTable représente une table en mémoire de données relationnelles. Cet exemple montre comment construire un paramètre table à partir de données en mémoire à l’aide de l’objet SQLServerDataTable. Le code crée d’abord un objet SQLServerDataTable, définit son schéma et remplit la table avec des données. Le code configure ensuite un SQLServerPreparedStatement qui transmet cette table de données en tant que paramètre table à SQL Server.  

```java
/* Assumes connection is an active Connection object. */

// Create an in-memory data table.  
SQLServerDataTable sourceDataTable = new SQLServerDataTable();
  
// Define metadata for the data table.  
sourceDataTable.addColumnMetadata("CategoryID" ,java.sql.Types.INTEGER);
sourceDataTable.addColumnMetadata("CategoryName" ,java.sql.Types.NVARCHAR);
  
// Populate the data table.  
sourceDataTable.addRow(1, "CategoryNameValue1");
sourceDataTable.addRow(2, "CategoryNameValue2");
  
// Pass the data table as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
            "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceDataTable);  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour la définition du paramètre table.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Passage d’un paramètre table en tant qu’objet ResultSet  

Cet exemple montre comment diffuser en continu des lignes de données d’un jeu de résultats vers un paramètre table. Le code First récupère les données d’une table source dans un objet crée un objet SQLServerDataTable, définit son schéma et remplit la table avec des données. Le code configure ensuite un SQLServerPreparedStatement qui transmet cette table de données en tant que paramètre table à SQL Server.  

```java
/* Assumes connection is an active Connection object. */

// Create the source ResultSet object. Here SourceCategories is a table defined with the same schema as Categories table.
ResultSet sourceResultSet = connection.createStatement().executeQuery("SELECT * FROM SourceCategories");  

// Pass the source result set as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceResultSet);  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour la définition du paramètre table.  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Passage d’un paramètre table en tant qu’objet ISQLServerDataRecord  

À compter de Microsoft JDBC Driver 6,0 pour SQL Server, une nouvelle interface ISQLServerDataRecord est disponible pour la diffusion de données en continu (selon la façon dont l’utilisateur fournit l’implémentation) à l’aide d’un paramètre table. L’exemple suivant montre comment implémenter l’interface ISQLServerDataRecord et comment la passer en tant que paramètre table. Par souci de simplicité, l’exemple suivant passe une seule ligne avec des valeurs codées en dur au paramètre table. Dans l’idéal, l’utilisateur implémenterait cette interface pour diffuser en continu des lignes à partir de n’importe quelle source, par exemple à partir de fichiers texte.  

```java
class MyRecords implements ISQLServerDataRecord  
{  
    int currentRow = 0;  
    Object[] row = new Object[2];  
  
    MyRecords(){  
        // Constructor. This implementation has just one row.
        row[0] = new Integer(1);  
        row[1] = "categoryName1";  
    }  
  
    public int getColumnCount(){  
        // Return the total number of columns, for this example it is 2.  
        return 2;  
    }  
  
    public SQLServerMetaData getColumnMetaData(int columnIndex) {  
        // Return the column metadata.  
        if (1 == columnIndex)  
            return new SQLServerMetaData("CategoryID", java.sql.Types.INTEGER);  
        else  
            return new SQLServerMetaData("CategoryName", java.sql.Types.NVARCHAR);  
    }  
  
    public Object[] getRowData(){  
        // Return the columns in the current row as an array of objects. This implementation has just one row.  
        return row;
    }  
  
    public boolean next(){  
        // Move to the next row. This implementation has just one row, after processing the first row, return false.  
        currentRow++;  
        if (1 == currentRow)  
            return true;  
        else  
            return false;  
    }
}

// Following code demonstrates how to pass MyRecords object as a table-valued parameter.  
MyRecords sourceRecords = new MyRecords();  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceRecords);  
pStmt.execute();  
```

> [!NOTE]  
> Consultez la section **API de paramètre table pour le pilote JDBC** ci-dessous pour obtenir la liste complète des API disponibles pour la définition du paramètre table.

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>API de paramètre table pour le pilote JDBC

### <a name="sqlservermetadata"></a>SQLServerMetaData

Cette classe représente les métadonnées d’une colonne. Elle est utilisée dans l’interface ISQLServerDataRecord pour passer des métadonnées de colonne au paramètre table. Les méthodes de cette classe sont les suivantes:  

| Créer une vue d’abonnement                                                                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData (String columnName, int sqlType, int Precision, int Scale, Boolean useServerDefault, Boolean isUniqueKey, SQLServerSortOrder sortOrder, int sortOrdinal) | Initialise une nouvelle instance de SQLServerMetaData avec le nom de colonne, le type SQL, la précision, l’échelle et la valeur par défaut du serveur spécifiés. Cette forme du constructeur prend en charge les paramètres table en vous permettant de spécifier si la colonne est unique dans le paramètre table, l’ordre de tri pour la colonne et l’ordinal de la colonne de tri. <br/><br/>useServerDefault: spécifie si cette colonne doit utiliser la valeur de serveur par défaut; La valeur par défaut est false.<br>isUniqueKey-indique si la colonne dans le paramètre table est unique; La valeur par défaut est false.<br>sortOrder: indique l’ordre de tri d’une colonne; La valeur par défaut est SQLServerSortOrder. Unspecified.<br>sortOrdinal: spécifie l’ordinal de la colonne de tri; sortOrdinal démarre à partir de 0; La valeur par défaut est-1. |
| public SQLServerMetaData( String columnName, int sqlType)                                                                                                                        | Initialise une nouvelle instance de SQLServerMetaData en utilisant le nom de colonne et le type SQL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| public SQLServerMetaData( String columnName, int sqlType, int length)                                                                                                                        | Initialise une nouvelle instance de SQLServerMetaData à l’aide du nom de colonne, du type SQL et de la longueur (pour les données de type chaîne). La longueur est utilisée pour différencier les chaînes volumineuses des chaînes dont la longueur est inférieure à 4000 caractères. Introduite dans la version 7,2 du pilote JDBC.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public SQLServerMetaData( String columnName, int sqlType, int precision, int scale)                                                                                              | Initialise une nouvelle instance de SQLServerMetaData à l’aide du nom de colonne, du type SQL, de la précision et de l’échelle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Public SQLServerMetaData(SQLServerMetaData sqlServerMetaData)                                                                                                                    | Initialise une nouvelle instance de SQLServerMetaData à partir d’un autre objet SQLServerMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Chaîne publique getColumName ()                                                                                                                                                     | Récupère le nom de la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| public int getSqlType()                                                                                                                                                          | Récupère le type SQL Java.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| public int getPrecision ()                                                                                                                                                        | Récupère la précision du type passé à la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getScale ()                                                                                                                                                            | Récupère l’échelle du type passé à la colonne.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public SQLServerSortOrder getSortOrder()                                                                                                                                         | Récupère l’ordre de tri.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getSortOrdinal ()                                                                                                                                                      | Récupère l’ordinal de tri.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public booléen isUniqueKey ()                                                                                                                                                     | Retourne une valeur indiquant si la colonne est unique.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| useServerDefault booléen public ()                                                                                                                                                | Retourne une valeur indiquant si la colonne utilise la valeur par défaut du serveur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Énumération qui définit l’ordre de tri. Les valeurs possibles sont croissant, décroissant et non spécifié.
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

Cette classe représente une table de données en mémoire à utiliser avec des paramètres table. Les méthodes de cette classe sont les suivantes:  

| Créer une vue d’abonnement                                                          | Description                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Public SQLServerDataTable()                                   | Initialise une nouvelle instance de SQLServerDataTable.    |
| < d’entrée\<d’itérateur public entier, objet [] > > getIterator ()      | Récupère un itérateur sur les lignes de la table de données. |
| public void addColumnMetadata (String columnName, int sqlType) | Ajoute des métadonnées pour la colonne spécifiée.              |
| public void addColumnMetadata(SQLServerDataColumn column)     | Ajoute des métadonnées pour la colonne spécifiée.              |
| public void addRow (objet... valeurs                          | Ajoute une ligne de données à la table de données.              |
| public Map\<Integer, SQLServerDataColumn> getColumnMetadata() | Récupère les métadonnées de colonne de cette table de données.       |
| public void Clear ()                                           | Efface cette table de données.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Cette classe représente une colonne de la table de données en mémoire représentée par SQLServerDataTable. Les méthodes de cette classe sont les suivantes:  

| Créer une vue d’abonnement                                                       | Description                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| public SQLServerDataColumn(String columnName, int sqlType) | Initialise une nouvelle instance de SQLServerDataColumn avec le nom et le type de la colonne. |
| public String getColumnName ()                              | Récupère le nom de la colonne.                                                       |
| public int getColumnType ()                                 | Récupère le type de colonne.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Cette classe représente une interface que les utilisateurs peuvent implémenter pour diffuser en continu des données vers un paramètre table. Les méthodes de cette interface sont les suivantes:  
  
| Créer une vue d’abonnement                                                    | Description                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData getColumnMetaData(int column); | Récupère les métadonnées de colonne de l’index de colonne donné.                                               |
| public int getColumnCount();                            | Récupère le nombre total de colonnes.                                                                  |
| public Object[] getRowData();                           | Récupère les données de la ligne active sous forme de tableau d’objets.                                          |
| public boolean next();                                  | Passe à la ligne suivante. Retourne la valeur true si le déplacement a réussi et qu’il y a une ligne suivante, false dans le cas contraire. |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Les méthodes suivantes ont été ajoutées à cette classe pour prendre en charge le passage de paramètres table.  

| Créer une vue d’abonnement                                                                                                    | Description                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured (int parameterIndex, String tvpName, SQLServerDataTable tvpDataTable)    | Remplit un paramètre table avec une table de données. parameterIndex est l’index du paramètre, tvpName est le nom du paramètre table et tvpDataTable est l’objet table de données source.                                                                                                          |
| public final void setStructured (int parameterIndex, String tvpName, ResultSet tvpResultSet)             | Remplit un paramètre table avec un ResultSet récupéré à partir d’une autre table. parameterIndex est l’index du paramètre, tvpName est le nom du paramètre table et tvpResultSet est l’objet de l’ensemble de résultats source.                                                                               |
| public final void setStructured (int parameterIndex, String tvpName, ISQLServerDataRecord tvpDataRecord) | Remplit un paramètre table à l’aide d’un objet ISQLServerDataRecord. ISQLServerDataRecord est utilisé pour les données de diffusion en continu et l’utilisateur décide de son utilisation. parameterIndex est l’index du paramètre, tvpName est le nom du paramètre table et tvpDataRecord est un objet ISQLServerDataRecord. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Les méthodes suivantes ont été ajoutées à cette classe pour prendre en charge le passage de paramètres table.  
  
| Créer une vue d’abonnement                                                                                                        | Description                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured (String paratemeterName, String tvpName, SQLServerDataTable tvpDataTable)    | Remplit un paramètre table passé à une procédure stockée avec une table de données. paratemeterName est le nom du paramètre, tvpName est le nom du type TVP et tvpDataTable est l’objet table de données.                                                                                                                 |
| public final void setStructured (String paratemeterName, String tvpName, ResultSet tvpResultSet)             | Remplit un paramètre table passé à une procédure stockée avec un jeu de résultats extrait d’une autre table. paratemeterName est le nom du paramètre, tvpName est le nom du type TVP et tvpResultSet est l’objet de l’ensemble de résultats source.                                                                              |
| public final void setStructured (String paratemeterName, String tvpName, ISQLServerDataRecord tvpDataRecord) | Remplit un paramètre table passé à une procédure stockée avec un objet ISQLServerDataRecord. ISQLServerDataRecord est utilisé pour les données de diffusion en continu et l’utilisateur décide de son utilisation. paratemeterName est le nom du paramètre, tvpName est le nom du type TVP et tvpDataRecord est un objet ISQLServerDataRecord. |

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
