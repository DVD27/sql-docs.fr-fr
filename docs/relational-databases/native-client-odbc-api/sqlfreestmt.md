---
title: SQLFreeStmt | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b985db3cb58a7029a3b5ec489d2e23b0c1292919
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73786727"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Recommandé   
      **SQLFreeStmt** n’est pas recommandé dans ODBC 3,0 et versions ultérieures. Toutefois, si l’application doit réutiliser l’instruction, vous devez toujours utiliser **SQLFreeStmt** avec les options **SQL_RESET_PARAMS** et **SQL_UNBIND** ). Vous pouvez également utiliser [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)et [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) pour remplacer ou dupliquer la fonction de **SQLFreeStmt** et les utiliser à la place.  
  
 En général, il est plus efficace de réutiliser des instructions que de les supprimer et d’en allouer de nouvelles. Toutefois, dans certaines situations, comme la réutilisation des instructions, SQLFreeStmt doit toujours être utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeStmt fonction)](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
