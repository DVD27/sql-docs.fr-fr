---
title: sys.external_libraries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 78923a0eb1404c1437c6e1144888261e542ebc5a
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471102"
---
# <a name="sysexternallibraries-transact-sql"></a>sys. external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Prend en charge la gestion des bibliothèques de packages relatives aux runtimes externes tels que R, Python et Java.

> [!NOTE]
> Dans SQL Server 2017, le langage R et la plateforme Windows sont pris en charge. R, Python et Java sur les plateformes Windows et Linux sont pris en charge dans SQL Server 2019 CTP 2.4.

## <a name="sysexternallibraries"></a>sys.external_libraries

L’affichage catalogue sys. external_libraries répertorie une ligne pour chaque bibliothèque externe qui a été chargée dans la base de données.

|Nom de la colonne |Type de données | Description|
|------|------|------|
|external_library_id |int | ID de l’objet de bibliothèque externe. |
|name |sysname |Nom de la bibliothèque externe. Est unique dans la base de données par propriétaire.|
|principal_id |int |ID du principal propriétaire de cette bibliothèque externe. |
|langage | sysname | Nom de la langue ou du runtime qui prend en charge la bibliothèque externe. Les valeurs valides sont «R», «Python» et «Java». Des runtimes supplémentaires peuvent être ajoutés à l’avenir.|
|scope |int |0 pour l’étendue publique; 1 pour l’étendue privée |  
|scope_desc |varchar(7) |Indique si le package est public ou privé|

## <a name="see-also"></a>Voir aussi  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Installer de nouveaux packages R sur SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
+ [Installer de nouveaux packages Python sur SQL Server](../../advanced-analytics/python/install-additional-python-packages-on-sql-server.md)  