---
title: Configurer PolyBase pour accéder à des données externes dans Oracle | Microsoft Docs
description: Cet article montre comment utiliser PolyBase pour créer une source de données externes afin d’accéder aux données Oracle.
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 09899bf161289e87e7bb15b9084335bbb4bc6180
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062297"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Configurer PolyBase pour accéder à des données externes dans Oracle

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’article explique comment utiliser PolyBase sur une instance SQL Server pour interroger des données externes dans Oracle.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md).

  La [clé principale](../../t-sql/statements/create-master-key-transact-sql.md) doit être créée avant les informations d’identification incluses dans l’étendue de la base de données. 

## <a name="configure-an-oracle-external-data-source"></a>Configurer une source de données externes Oracle

Pour interroger les données d’une source de données Oracle, vous devez créer des tables externes pour référencer les données externes. Cette section fournit un exemple de code pour créer ces tables externes.

Les commandes Transact-SQL suivantes sont utilisées dans cette section :

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)


1. Créez des informations d’identification incluses dans l’étendue de la base de données pour accéder à la source Oracle.

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source. 
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'password';
    ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

    ```sql
    /* 
    * LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    * PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    * CONNECTION_OPTIONS: Specify driver location
    * CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = 'oracle://<server address>[:<port>]',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = credential_name)
    ```

1. **Facultatif :** Créez des statistiques sur une table externe.

    Pour des performances de requêtes optimales, nous vous recommandons de créer des statistiques sur les colonnes de table externe, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT] 
>Une fois que vous avez créé une source de données externes, vous pouvez utiliser la commande [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) afin de créer une table requêtable sur cette source. 

Pour plus d’informations et pour obtenir des exemples, consultez les articles suivants :

- [CRÉER UNE TABLE EXTERNE](../../t-sql/statements/create-external-table-transact-sql.md).
- [Vue d’ensemble de Polybase SQL Server](polybase-guide.md).
