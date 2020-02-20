---
title: Utilisation des types de données de base | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
author: MightyPen
ms.author: genemi
ms.openlocfilehash: abbd2aa3c277ad36f419de849b02433f17d27403
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026512"
---
# <a name="using-basic-data-types"></a>Utilisation des types de données de base

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilise les types de données de base JDBC pour convertir les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un format compréhensible par le langage de programmation Java et inversement. Le pilote JDBC prend en charge l'API JDBC 4.0, qui inclut le type de données **SQLXML** et les types de données nationaux (Unicode), par exemple **NCHAR**, **NVARCHAR**, **LONGNVARCHAR** et **NCLOB**.  
  
## <a name="data-type-mappings"></a>Mappages de types de données

Le tableau suivant répertorie les mappages par défaut entre les types de données de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], JDBC et du langage de programmation Java :  
  
| Types SQL Server   | Types JDBC (java.sql.Types)                        | Types langage Java          |
| ------------------ | -------------------------------------------------- | ---------------------------- |
| bigint             | bigint                                             | long                         |
| binary             | BINARY                                             | byte[]                       |
| bit                | BIT                                                | boolean                      |
| char               | CHAR                                               | String                       |
| Date               | DATE                                               | java.sql.Date                |
| DATETIME           | timestamp                                          | java.sql.Timestamp           |
| datetime2          | timestamp                                          | java.sql.Timestamp           |
| datetimeoffset (2) | microsoft.sql.Types.DATETIMEOFFSET                 | microsoft.sql.DateTimeOffset |
| Décimal            | DECIMAL                                            | java.math.BigDecimal         |
| float              | DOUBLE                                             | double                       |
| image              | LONGVARBINARY                                      | byte[]                       |
| int                | INTEGER                                            | int                          |
| money              | DECIMAL                                            | java.math.BigDecimal         |
| NCHAR              | CHAR<br /><br /> NCHAR (Java SE 6.0)               | String                       |
| ntext              | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | String                       |
| numeric            | NUMERIC                                            | java.math.BigDecimal         |
| NVARCHAR           | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | String                       |
| nvarchar(max)      | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | String                       |
| real               | real                                               | float                        |
| smalldatetime      | timestamp                                          | java.sql.Timestamp           |
| SMALLINT           | SMALLINT                                           | short                        |
| SMALLMONEY         | DECIMAL                                            | java.math.BigDecimal         |
| text               | LONGVARCHAR                                        | String                       |
| time               | TIME (1)                                           | java.sql.Time (1)            |
| timestamp          | BINARY                                             | byte[]                       |
| TINYINT            | TINYINT                                            | short                        |
| udt                | VARBINARY                                          | byte[]                       |
| UNIQUEIDENTIFIER   | CHAR                                               | String                       |
| varbinary          | VARBINARY                                          | byte[]                       |
| varbinary(max)     | VARBINARY                                          | byte[]                       |
| varchar            | VARCHAR                                            | String                       |
| varchar(max)       | VARCHAR                                            | String                       |
| Xml                | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | String<br /><br /> SQLXML    |
| sqlvariant         | SQLVARIANT                                         | Object                       |
| geometry           | VARBINARY                                          | byte[]                       |
| Geography          | VARBINARY                                          | byte[]                       |
  
(1) pour utiliser java.sql.Time avec le type d’heure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez affecter à la propriété de connexion **sendTimeAsDatetime** la valeur False.  
  
(2) Vous pouvez accéder par programmation aux valeurs de **datetimeoffset** avec la [classe DateTimeOffset](../../connect/jdbc/reference/datetimeoffset-class.md).  
  
Les sections suivantes proposent des exemples d'utilisation du pilote JDBC et des types de données de base. Pour obtenir un exemple plus détaillé sur l’utilisation des types de données de base dans une application Java, consultez [Exemple de types de données de base](../../connect/jdbc/basic-data-types-sample.md).  
  
## <a name="retrieving-data-as-a-string"></a>Extraction de données sous la forme d'une chaîne

Si vous devez récupérer des données d’une source de données qui correspond à l’un des types de données de base JDBC pour les afficher en tant que chaîne, ou si des données fortement typées ne sont pas nécessaires, vous pouvez appliquer la méthode [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), comme suit :  
  
[!code[JDBC#UsingBasicDataTypes1](../../connect/jdbc/codesnippet/Java/using-basic-data-types_1.java)]  
  
## <a name="retrieving-data-by-data-type"></a>Extraction de données par type de données

Si vous devez récupérer des données d’une source de données et que vous connaissez le type des données récupérées, utilisez l’une des méthodes get\<Type> de la classe SQLServerResultSet, également connues comme *méthodes d’accesseur Get*. Vous pouvez utiliser soit un nom de colonne, soit un index de colonne avec les méthodes get\<Type>, comme suit :  
  
[!code[JDBC#UsingBasicDataTypes2](../../connect/jdbc/codesnippet/Java/using-basic-data-types_2.java)]  
  
> [!NOTE]  
> Le pilote JDBC déconseille et ne prend pas en charge les méthodes getUnicodeStream et getBigDecimal avec échelle.

## <a name="updating-data-by-data-type"></a>Mise à jour des données par type de données

Si vous devez mettre à jour la valeur d'un champ dans une source de données, utilisez l'une des méthodes update\<Type> de la classe SQLServerResultSet. Dans l’exemple suivant, la méthode [updateInt](../../connect/jdbc/reference/updateint-method-sqlserverresultset.md) est appliquée conjointement avec la méthode [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) pour mettre à jour les données dans la source de données :  
  
[!code[JDBC#UsingBasicDataTypes3](../../connect/jdbc/codesnippet/Java/using-basic-data-types_3.java)]  
  
> [!NOTE]  
> Le pilote JDBC ne peut pas mettre à jour une colonne SQL Server avec un nom de colonne dont la longueur dépasse 127 caractères. Si une mise à jour est tentée sur une colonne dont le nom dépasse 127 caractères, une exception est levée.  
  
## <a name="updating-data-by-parameterized-query"></a>Mise à jour des données par requête paramétrable

Si vous devez mettre à jour des données dans une source de données en utilisant une requête paramétrable, vous pouvez définir le type de données des paramètres à l’aide de l’une des méthodes set\<Type> de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), également connues comme *méthodes d’accesseur Set*. Dans l’exemple suivant, la méthode [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) est utilisée pour précompiler la requête paramétrable, puis la méthode [setString](../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md) est utilisée pour définir la valeur de chaîne du paramètre avant d’appeler la méthode [executeUpdate](../../connect/jdbc/reference/executeupdate-method.md).  
  
[!code[JDBC#UsingBasicDataTypes4](../../connect/jdbc/codesnippet/Java/using-basic-data-types_4.java)]  
  
Pour plus d’informations sur les requêtes paramétrables, consultez [Utilisation d'une instruction SQL avec paramètres](../../connect/jdbc/using-an-sql-statement-with-parameters.md).  

## <a name="passing-parameters-to-a-stored-procedure"></a>Transmission de paramètres à une procédure stockée

Si vous devez transmettre des paramètres typés dans une procédure stockée, vous pouvez définir les paramètres par index ou par nom à l’aide de l’une des méthodes set\<Type> de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Dans l’exemple suivant, la méthode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) est utilisée pour configurer l’appel de la procédure stockée, puis la méthode [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) est utilisée pour définir le paramètre de l’appel avant l’appel de la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md).  
  
[!code[JDBC#UsingBasicDataTypes5](../../connect/jdbc/codesnippet/Java/using-basic-data-types_5.java)]  
  
> [!NOTE]  
> Dans cet exemple, un jeu de résultats est retourné avec les résultats de l'exécution de la procédure stockée.

Pour plus d'informations sur l'utilisation du pilote JDBC avec les procédures stockées et les paramètres d'entrée, consultez [Utilisation d'une procédure stockée avec des paramètres d'entrée](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md).  

## <a name="retrieving-parameters-from-a-stored-procedure"></a>Extraction de paramètres à partir d'une procédure stockée

Si vous devez récupérer des paramètres d’une procédure stockée, vous devez tout d’abord inscrire un paramètre out par nom ou index à l’aide de la méthode [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) de la classe SQLServerCallableStatement, puis attribuer le paramètre out retourné à une variable appropriée après l’exécution de l’appel de la procédure stockée. Dans l’exemple suivant, la méthode prepareCall est utilisée pour configurer l’appel de la procédure stockée, la méthode registerOutParameter est utilisée pour configurer le paramètre out, puis la méthode [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) est utilisée pour définir le paramètre pour l’appel avant l’appel de la méthode executeQuery. La valeur retournée par le paramètre out de la procédure stockée est récupérée à l’aide de la méthode [getShort](../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md).  
  
[!code[JDBC#UsingBasicDataTypes6](../../connect/jdbc/codesnippet/Java/using-basic-data-types_6.java)]  
  
> [!NOTE]  
> Outre le paramètre OUT retourné, un jeu de résultats peut également être retourné avec les résultats de l'exécution de la procédure stockée.  
  
Pour plus d'informations sur l'utilisation du pilote JDBC avec les procédures stockées et les paramètres de sortie, consultez [Utilisation d'une procédure stockée avec des paramètres de sortie](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md).  

## <a name="see-also"></a>Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
