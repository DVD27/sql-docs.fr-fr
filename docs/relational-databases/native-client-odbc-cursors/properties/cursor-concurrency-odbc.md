---
title: Accès concurrentiel au curseur (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 809fbb485e18093b3f9e3e68d6ab6cf084787692
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760691"
---
# <a name="cursor-concurrency-odbc"></a>Accès concurrentiel au curseur (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Les opérations de curseur, comme les types de curseurs, sont affectées par les options d'accès concurrentiel définies par l'application. Les options d’accès concurrentiel sont définies à l’aide de l’option SQL_ATTR_CONCURRENCY de [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Les types d'accès concurrentiel sont :  
  
-   Lecture seule (SQL_CONCUR_READONLY)  
  
-   Valeurs (SQL_CONCUR_VALUES)  
  
-   Version de ligne (SQL_CONCUR_ROWVER)  
  
-   Verrou (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
