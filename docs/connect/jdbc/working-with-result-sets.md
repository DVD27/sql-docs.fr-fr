---
title: Utiliser des jeux de résultats | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f29e7e101a0a295266ee5cfa96fbaa84f515e776
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923897"
---
# <a name="working-with-result-sets"></a>Utilisation des jeux de résultats

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Quand vous travaillez sur les données contenues dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une méthode de manipulation des données consiste à utiliser un jeu de résultats. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l’utilisation des jeux de résultats par le biais de l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Grâce à l’objet SQLServerResultSet, vous pouvez extraire les données retournées à partir d’une instruction SQL ou d’une procédure stockée, mettre à jour les données si nécessaire, puis remettre ces données dans la base de données.  
  
En outre, l’objet SQLServerResultSet fournit des méthodes de navigation dans ses lignes de données, d’obtention ou de définition des données qu’il contient et d’établissement de plusieurs niveaux de sensibilité aux modifications apportées à la base de données sous-jacente.  
  
> [!NOTE]  
> Pour plus d’informations sur la gestion des jeux de résultats, et notamment leur sensibilité aux modifications, consultez [Gérer les jeux de résultats avec le pilote JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
Les rubriques de cette section décrivent différentes façons d’utiliser un jeu de résultats pour manipuler les données contenues dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
| Rubrique                                                                                        | Description                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Exemple de récupération des données d'un jeu de résultats](../../connect/jdbc/retrieving-result-set-data-sample.md) | Décrit l’utilisation d’un jeu de résultats pour extraire des données à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les afficher.                                                         |
| [Exemple de modification des données d'un jeu de résultats](../../connect/jdbc/modifying-result-set-data-sample.md)   | Décrit l’utilisation d’un jeu de résultats pour insérer, extraire et modifier des données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                      |
| [Exemple de mise en cache des données d'un jeu de résultats](../../connect/jdbc/caching-result-set-data-sample.md)       | Décrit l’utilisation d’un jeu de résultats pour extraire de grandes quantités de données à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et pour contrôler la manière dont ces données sont mises en cache sur le client. |
  
## <a name="see-also"></a>Voir aussi

 [Exemples d'applications du pilote JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
