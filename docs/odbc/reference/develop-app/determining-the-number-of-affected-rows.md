---
title: Détermination du nombre de lignes affectées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a6a1bebf7d5cfb85e49fb0e382dacc4f4464054e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039983"
---
# <a name="determining-the-number-of-affected-rows"></a>Détermination du nombre de lignes affectées
Une fois une application met à jour, supprime ou insère des lignes, elle peut appeler **SQLRowCount** pour déterminer combien de lignes ont été affectés. **SQLRowCount** retourne cette valeur déterminant si les lignes ont été mis à jour, supprimées ou insérées en exécutant un **mise à jour**, **supprimer**, ou **insérer** instruction, en exécutant un positionnées mettre à jour ou supprimer l’instruction ou en appelant **SQLSetPos**.  
  
 Si un lot d’instructions SQL est exécuté, le nombre de lignes affectées peut être un nombre total de toutes les instructions dans le lot ou des nombres individuels pour chaque instruction du lot. Pour plus d’informations, consultez [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md) et [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Le nombre de lignes affectées est également retourné dans le champ d’en-tête diagnostic SQL_DIAG_ROW_COUNT dans la zone de diagnostic associé au handle d’instruction. Toutefois, les données dans ce champ sont réinitialisées après l’appel de chaque fonction sur le même descripteur d’instruction, tandis que la valeur retournée par **SQLRowCount** reste le même qu’un appel à **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, ou **SQLSetPos**.
