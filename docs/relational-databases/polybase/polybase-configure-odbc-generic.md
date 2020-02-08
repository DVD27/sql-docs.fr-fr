---
title: 'Accéder aux données externes : Types génériques ODBC - PolyBase'
ms.date: 12/13/2019
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 5017dc54a1e7858786413b2fcc164e4949f77646
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75255420"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Configurer PolyBase pour accéder à des données externes dans SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

PolyBase dans SQL Server 2019 vous permet de vous connecter à des sources de données compatibles avec ODBC par le biais du connecteur ODBC. 

## <a name="prerequisites"></a>Conditions préalables requises

Notez que la fonctionnalité = peut être utilisée uniquement sur SQL Server pour Windows. 

Si vous n’avez pas installé PolyBase, consultez [Installation de PolyBase](polybase-installation.md).

 La [clé principale](../../t-sql/statements/create-master-key-transact-sql.md) doit être créée avant les informations d’identification incluses dans l’étendue de la base de données. 

Commencez par télécharger et installer le pilote ODBC de la source de données à laquelle vous souhaitez vous connecter, sur chacun des nœuds PolyBase. Une fois que le pilote est correctement installé, vous pouvez tester le pilote dans « Administrateur de sources de données ODBC ».

![Groupes de scale-out PolyBase](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

> **IMPORTANT !**
> 
> Pour améliorer les performances des requêtes, vérifiez que le regroupement des connexions est activé pour le pilote. Vous pouvez activer cette option sous « Administrateur de sources de données ODBC ».
> 
> **Remarque**
> 
> Le nom du pilote (entouré ci-dessus) doit être spécifié lors de la création de la source de données externe (étape 3 ci-dessous).

## <a name="create-an-external-table"></a>Créer une table externe

Pour interroger les données d’une source de données ODBC, vous devez créer des tables externes afin de référencer les données externes. Cette section fournit un exemple de code pour créer des tables externes.

Les commandes Transact-SQL suivantes sont utilisées dans cette section :

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Créez des informations d’identification incluses dans l’étendue de la base de données pour accéder à la source ODBC.

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source. 
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'password';
    ```

1. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

    ```sql
    /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'Driver={<Name of Installed Driver>};
    ServerNode = <name of server  address>:<Port>',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = credential_nam );
    ```

1. **Facultatif :** Créez des statistiques sur une table externe.

Pour des performances de requêtes optimales, nous vous recommandons de créer des statistiques sur les colonnes de table externe, en particulier celles utilisées pour les jointures, les filtres et les agrégats.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT] 
>Une fois que vous avez créé une source de données externes, vous pouvez utiliser la commande [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) afin de créer une table requêtable sur cette source. 

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PolyBase, consultez [Vue d’ensemble de SQL Server PolyBase](polybase-guide.md).
