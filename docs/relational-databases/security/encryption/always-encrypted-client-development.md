---
title: Always Encrypted (développement client) | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2018
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 475a030972819515a2f8f346b5644139dd7fdf90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086903"
---
# <a name="always-encrypted-client-development"></a>Always Encrypted (développement client)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) est une technologie de chiffrement côté client qui garantit que les données sensibles (et les clés de chiffrement liées) ne soient jamais révélées à SQL Server et à Azure SQL Database. Grâce à Always Encrypted, un pilote client peut chiffrer des données sensibles de manière transparente avant de les transmettre au moteur de base de données, et peut déchiffrer de manière transparente des données récupérées à partir de colonnes de base de données chiffrées.

Pour plus d’informations sur le développement d’applications qui utilisent des bases de données protégées par Always Encrypted, et sur les pilotes clients et les versions de pilotes prises en charge par Always Encrypted, consultez :

- [Utilisation d’Always Encrypted avec le fournisseur de données .NET Framework pour SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Utilisation du chiffrement intégral avec le pilote JDBC](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Utilisation d’Always Encrypted avec ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Utilisation d’Always Encrypted avec les pilotes PHP](../../../connect/php/using-always-encrypted-php-drivers.md)

> [!NOTE]
> Actuellement, Always Encrypted n’est pas pris en charge dans [.NET CORE](https://docs.microsoft.com/dotnet/core/).

## <a name="see-also"></a>Voir aussi

[Always Encrypted (moteur de base de données)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

