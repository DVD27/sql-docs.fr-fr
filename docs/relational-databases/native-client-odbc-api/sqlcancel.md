---
title: SQLCancel - France Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2db2c4b66940a81dd65064ee730cd683e2206a58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302636"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  La rubrique [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) indique que dans ODBC 2.x, si une application appelle **SQLCancel** alous qu'aucun traitement n'est en cours sur l'instruction, **SQLCancel** a le même effet que **SQLFreeStmt** avec l'option **SQL_CLOSE** ; ce compoutement est défini uniquement par souci d'exhaustivité et les applications doivent appeler **SQLFreeStmt** ou **SQLCloseCursou** to close cursous. Mais même si votre application [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit 3.5.x ou version ultérieure pour l'API ODBC, la fonction **SQLCancel** utilisera le comportement ODBC 2.x.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
