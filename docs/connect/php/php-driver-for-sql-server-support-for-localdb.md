---
title: Prise en charge de la base de données locale | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6da7f1aed956c8b2f5c71496c9c121f6006eabb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935956"
---
# <a name="support-for-localdb"></a>Prise en charge de la base de données locale

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

La base de données locale est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une version allégée de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]qui est disponible depuis. Cette rubrique explique comment se connecter à une base de données dans une instance LocalDB.

## <a name="remarks"></a>Notes

Pour plus d’informations sur la base de données locale, notamment sur l’installation de la base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données locale et la [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] configuration de votre instance de base de données locale, consultez la rubrique de la documentation en ligne sur Express

En bref, la base de données locale vous permet d’effectuer les opérations suivantes:

-   Utiliser **sqllocaldb.exe i** pour déterminer le nom de l'instance par défaut.

-   Utiliser le mot clé de chaîne de connexion **AttachDBFilename** pour spécifier le fichier de base de données auquel le serveur doit se rattacher. Lorsque vous utilisez **AttachDBFilename**, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion **Database** , la base de données est supprimée de l'instance LocalDB lorsque l'application se ferme.

-   Spécifiez une instance LocalDB dans votre chaîne de connexion. Par exemple, voici un exemple de chaîne de connexion SQLSRV:

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    Next est un exemple de chaîne de connexion PDO_SQLSRV:  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

Si nécessaire, vous pouvez créer une instance LocalDB avec sqllocaldb.exe. Vous pouvez également utiliser sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB. Par exemple, `sqlcmd -S (localdb)\v11.0`. (En cas d’exécution dans IIS, vous devez exécuter sous le compte approprié pour obtenir les mêmes résultats que lorsque vous exécutez à partir de la ligne de commande. pour plus d’informations [, consultez Utilisation de la base de données locale avec IIS complet, partie 2: propriété de l’instance](https://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx) .)

Voici des exemples de chaînes de connexion utilisant le pilote SQLSRV qui se connectent à une base de données dans une instance nommée de base de données locale appelée myInstance:

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Voici des exemples de chaînes de connexion utilisant le pilote PDO_SQLSRV qui se connectent à une base de données dans une instance nommée de base de données locale appelée myInstance:  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Pour obtenir des instructions sur l’installation de la base de données locale, consultez la documentation sur le [document](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). Si vous utilisez sqlcmd. exe pour modifier des données dans votre instance de base de données locale, vous aurez besoin de l' [utilitaire sqlcmd](../../tools/sqlcmd-utility.md).

## <a name="see-also"></a>Voir aussi

[Connexion au serveur](../../connect/php/connecting-to-the-server.md)
