---
title: Quand utiliser SQL Server Native Client (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4340b1a5e79c17e1b7e8bf6dcff69d2a5789572d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305010"
---
# <a name="when-to-use-sql-server-native-client"></a>Quand utiliser SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est une technologie que vous pouvez utiliser pour accéder aux données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Pour en savoir plus sur les différentes technologies d’accès aux données, consultez [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Lorsque vous décidez s'il faut utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client comme technologie d'accès aux données de votre application, vous devez considérer plusieurs facteurs.  
  
 Pour les nouvelles applications, si vous utilisez un langage de programmation managé tel que Microsoft Visual C# ou Visual Basic et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qui fait partie du .NET Framework.  
  
 Si vous développez une application COM et que vous devez accéder aux nouvelles fonctionnalités introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Si vous n'avez pas besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC (Windows Data Access Components).  
  
 Pour les applications OLE DB et ODBC existantes, vous devez décider principalement si vous avez besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous possédez une application déjà rodée qui n'a pas besoin des nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC. Mais si vous avez besoin d’accéder à ces nouvelles fonctionnalités, telles que le [type de données xml](../../t-sql/xml/xml-transact-sql.md), vous devriez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client et MDAC prennent en charge l'isolation de la transaction de lecture validée à l'aide du contrôle de version de ligne, mais seul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge l'isolation de la transaction d'instantané. (En termes de programmation, l'isolation des transactions de lecture validée avec le contrôle de version de ligne équivaut à la transaction de lecture validée.)  
  
 Pour obtenir de l’information sur les différences entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client et MDAC, consultez La mise à jour [d’une application au client autochtone de SQL Server de MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programme des clients autochtones DE SQL Server](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [ODBC Comment faire sur les sujets](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Rubriques de procédures OLE DB](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
