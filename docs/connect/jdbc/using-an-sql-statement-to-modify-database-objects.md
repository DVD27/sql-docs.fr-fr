---
title: Utilisation d’une instruction SQL pour modifier des objets de base de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 28c71784f8e51600aef111649b12f81b5878b324
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916386"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Utilisation d'une instruction SQL pour modifier les objets de base de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour modifier des objets de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une instruction SQL, vous pouvez appliquer la méthode [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). La méthode executeUpdate transmet l’instruction SQL à la base de données pour traitement, puis retourne une valeur égale à 0 car aucune ligne n’a été affectée.

Pour ce faire, vous devez commencer par créer un objet SQLServerStatement à l’aide de la méthode [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

> [!NOTE]  
> Les instructions SQL qui modifient les objets dans une base de données sont des instructions dites DDL (Data Definition Language, langage de définition de données). Celles-ci incluent des `CREATE TABLE`instructions `DROP TABLE`telles `CREATE INDEX`que, `DROP INDEX`, et. Pour plus d’informations sur les types d’instructions DDL pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction. Une instruction SQL est générée pour créer la TestTable simple dans la base de données, puis l’instruction est exécutée et la valeur retournée est affichée.

[!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]

## <a name="see-also"></a>Voir aussi

[Utilisation d’instructions avec SQL](../../connect/jdbc/using-statements-with-sql.md)
