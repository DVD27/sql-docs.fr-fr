---
title: Exemple de lecture de données volumineuses avec des procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 924bcf388ddf74f3be3f4bb13f83e00789fb8777
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028303"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Exemple de lecture de données volumineuses avec des procédures stockées

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Cet exemple d'application du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] montre comment récupérer un paramètre OUT volumineux à partir d'une procédure stockée.

Le fichier de code de cet exemple, ExecuteStoredProcedure.java, se trouve à l'emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d’application, l’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] est nécessaire. Définissez également le classpath de façon à inclure le fichier jar mssql-jdbc. Pour plus d'informations sur la définition de l'instruction classpath, consultez [Utilisation du pilote JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d'informations sur le fichier JAR à choisir, consultez [Configuration requise pour le pilote JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

Créez la procédure stockée suivante dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] :

```sql
CREATE PROCEDURE GetLargeDataValue
  (@Document_ID int,
   @Document_ID_out int OUTPUT,
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  

AS
BEGIN
   SELECT @Document_ID_out = DocumentID,
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```

## <a name="example"></a>Exemple

Dans l’exemple suivant, le code établit une connexion à la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Il crée ensuite des exemples de données et met à jour la table Production.Document en utilisant une requête paramétrable. Il obtient ensuite le mode de mise en mémoire tampon adaptative avec la méthode [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), puis exécute la procédure stockée GetLargeDataValue. Notez qu'à partir de la version 2.0 du pilote JDBC, la propriété de connexion responseBuffering a la valeur « adaptive » par défaut.

Pour finir, l’exemple de code affiche les données retournées avec les paramètres OUT et montre également comment utiliser les méthodes `mark` et `reset` sur le flux pour relire une partie des données.

[!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>Voir aussi

[Utilisation de données volumineuses](../../../connect/jdbc/code-samples/working-with-large-data.md)
