---
title: Gérer des instructions complexes | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6b807a45-a8b5-4b1c-8b7b-d8175c710ce0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ebd2aee0990b744df1420e88f8cc79870b350f2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027990"
---
# <a name="handling-complex-statements"></a>Gestion des instructions complexes
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] peut amener à gérer des instructions complexes, notamment des instructions générées de façon dynamique à l’exécution. Les instructions complexes effectuent souvent une série de tâches, telles que des mises à jour, des insertions et des suppressions. Ces types d'instructions peuvent également retourner plusieurs jeux de résultats et paramètres de sortie. Dans ce cas, le code Java exécutant les instructions pourrait ne pas connaître à l'avance les types et le nombre d'objets, ainsi que les données retournées.  
  
 Pour traiter efficacement des instructions complexes, le pilote JDBC offre plusieurs méthodes permettant d'interroger les objets et les données retournées, de façon à ce que votre application puisse les traiter correctement. La clé pour traiter des instructions complexes est la méthode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Cette méthode retourne une valeur **booléenne**. Si la valeur est « true », le premier résultat retourné par les instructions est un jeu de résultats. Si la valeur est « false », le premier résultat retourné est un nombre de mises à jour.  
  
 Si vous connaissez le type d’objet ou de données retourné, vous pouvez utiliser la méthode [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) ou la méthode [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) pour traiter ces données. Pour traiter l’objet ou les données suivants parmi ceux qui ont été retournés par l’instruction complexe, vous pouvez appeler la méthode [getMoreResults](../../connect/jdbc/reference/getmoreresults-method.md).  
  
 Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, une instruction complexe qui combine un appel de procédure stockée à une instruction SQL est générée, les instructions sont exécutées, puis une boucle `do` est utilisée pour traiter tous les jeux de résultats et nombres mis à jour retournés.  
  
 [!code[JDBC#HandlingComplexStatements1](../../connect/jdbc/codesnippet/Java/handling-complex-statements_1.java)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'instructions avec le pilote JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
