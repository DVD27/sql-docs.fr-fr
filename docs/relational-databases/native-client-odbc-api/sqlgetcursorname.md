---
title: SQLGetCursorName | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81fcdac796dcaf185ee2929c5d981a1f88edb26d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73786552"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Si l'application ne spécifie pas de nom de curseur, le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client en génère un pour l'application lors de la génération du curseur. L'application peut utiliser **SQLGetCursorName** pour récupérer le nom du curseur défini par le pilote pour les instructions UPDATE et DELETE positionnées. L'application n'a pas besoin d'appeler **SQLSetCursorName** pour tirer parti des instructions de manipulation de données positionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetCursorName, fonction](https://go.microsoft.com/fwlink/?LinkId=59349)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
