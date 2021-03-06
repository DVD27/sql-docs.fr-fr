---
title: Compatibilité JDBC 4,3 pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20cefb029a126b0a262d86a2dc0a0791959085bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956366"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Conformité à JDBC 4.3 pour le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Les versions antérieures à Microsoft JDBC Driver 6.4 pour SQL Server sont conformes uniquement aux spécifications de l’API Java Database Connectivity (JDBC) 4.2. Cette section ne s’applique pas aux versions qui contiennent la version 6.4 et antérieures à celle-ci.

Depuis la version 6,4, le pilote JDBC Microsoft pour SQL Server est compatible avec Java 9 et `SQLFeatureNotSupportedException` lève une nouvelle API JDBC 4,3 qui a des méthodes non implémentées.

Avec le pilote Microsoft JDBC 7,0 pour la version SQL Server, le pilote est désormais compatible avec JAVA 10 et prend en charge les API mentionnées ci-dessous. Le pilote lève une `SQLFeatureNotSupportedException` exception pour d’autres méthodes non implémentées des spécifications JDBC 4,3.

|Nouvelle API|Description|Implémentation intéressante|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Indications sur le pilote qu’une demande, une unité de travail indépendante, commence sur cette connexion. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Enregistre les valeurs des champs de connexion qui peuvent être modifiés par le biais de méthodes `databaseAutoCommitMode`d’API publiques: `sendTimeAsDatetime`, `statementPoolingCacheSize` `transactionIsolationLevel`, `disableStatementPooling` `networkTimeout`, `serverPreparedStatementDiscardThreshold` `holdability`, `enablePrepareOnFirstPreparedStatementCall`,,,,, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Indications sur le pilote qu’une demande, une unité de travail indépendante, est terminée. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Ferme les instructions créées pendant l’unité de travail et restaure toutes les transactions ouvertes. La méthode rétablit également les modifications apportées aux champs de connexion répertoriés ci-dessus.|
