---
title: SQLNumResultCols | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 965b04d609053dabae694b2409677d0499497186
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85788040"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Pour les instructions exécutées, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client n'accède pas au serveur pour indiquer le nombre de colonnes d'un jeu de résultats. **SQLNumResultCols** ne provoque alors pas de boucle de serveur. À l'instar de [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) et [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), l'appel de **SQLNumResultCols** sur des instructions préparées mais non exécutées génère une boucle de serveur.  
  
 Lorsqu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ou un lot d'instructions retourne plusieurs ensembles de lignes de résultat, il est possible que le nombre de colonnes de jeu de résultats soit différent d'un ensemble de lignes à un autre. **SQLNumResultCols** doit être appelé pour chaque ensemble. Lorsque le nombre de colonnes change, l'application doit réassocier les valeurs de données avant d'extraire les résultats de ligne. Pour plus d'informations sur la gestion de plusieurs retours de jeux de résultats, consultez [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Les améliorations apportées au moteur de base de données à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permettent à SQLNumResultCols d’obtenir des descriptions plus précises des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par SQLNumResultCols dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLNumResultCols fonction)](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
