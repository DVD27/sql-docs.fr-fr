---
title: Utilisation de points d'enregistrement | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d860e368fe66ce926687fd343fe9f23704cfc7d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69026132"
---
# <a name="using-savepoints"></a>Utilisation de points de sauvegarde

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les points d'enregistrement constituent un mécanisme permettant d'annuler certaines parties de transactions. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez créer un point de sauvegarde à l’aide de l’instruction SAVE TRANSACTION savepoint_name. Par la suite, vous pourrez exécuter une instruction ROLLBACK TRANSACTION nom_point_enregistrement pour revenir au point d'enregistrement au lieu de revenir au début de la transaction.

Les points d'enregistrement sont utiles dans les situations où des erreurs sont susceptibles de se produire. L'utilisation d'un point d'enregistrement pour annuler une partie d'une transaction en cas d'erreur non fréquente peut s'avérer plus efficace que de tester chaque transaction afin de voir si une mise à jour est valide avant de l'implémenter. Les mises à jour et les restaurations étant des opérations coûteuses, les points d'enregistrement ne sont efficaces que si la probabilité de rencontrer l'erreur est faible et si le coût de vérification préalable de la validité d'une mise à jour est relativement élevé.

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l’utilisation de points de sauvegarde à l’aide de la méthode [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La méthode setSavepoint permet de créer un point de sauvegarde nommé ou non à l’intérieur de la transaction en cours et retourne un objet [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md). Il est possible de créer plusieurs points d'enregistrement à l'intérieur d'une transaction. Pour annuler une transaction jusqu’à un point de sauvegarde donné, vous pouvez transmettre l’objet SQLServerSavepoint à la méthode [rollback (java.sql.Savepoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md).

Dans l’exemple suivant, un point de sauvegarde est utilisé lors de l’exécution d’une transaction locale composée de deux instructions distinctes dans le bloc `try`. Les instructions sont exécutées sur la table Production.ScrapReason de l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], et un point de sauvegarde est utilisé pour restaurer la deuxième instruction. Cela a pour effet que seule la première instruction est validée dans la base de données.

[!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]

## <a name="see-also"></a>Voir aussi

[Réalisation de transactions avec le pilote JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
