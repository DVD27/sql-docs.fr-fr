---
title: Enregistrements d’État | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6ed360c39b87efe851bcbbb5c60762288ea1719
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114280"
---
# <a name="status-records"></a>Enregistrements d’état
Les champs des enregistrements d’État contiennent des informations sur des erreurs ou des avertissements spécifiques retournés par le gestionnaire de pilotes, le pilote ou la source de données, y compris le SQLSTATE, le numéro d’erreur natif, le message de diagnostic, le numéro de colonne et le numéro de ligne. Les enregistrements d’État ne peuvent être créés que si la fonction retourne SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA ou SQL_STILL_EXECUTING. Pour obtenir la liste complète des champs dans les enregistrements d’État, consultez la description de la fonction [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .  
  
 Cette section contient les rubriques suivantes :  
  
-   [Séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Codes SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messages de diagnostic](../../../odbc/reference/develop-app/diagnostic-messages.md)
