---
title: Appel de SQLCloseCursor | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 447a0892049317813fa9fe6986e6219922a11e28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068693"
---
# <a name="calling-sqlclosecursor"></a>Appel de SQLCloseCursor
Étant donné que **SQLCloseCursor** est presque identique **SQLFreeStmt** avec SQL_CLOSE, le Gestionnaire de pilotes ne mappe pas cette fonction. Fonctions de remplacement sont mappées afin qu’existant ODBC *2.x* applications peuvent facilement déplacer vers ODBC *3.x* à l’aide des nouvelles fonctions. Ce déplacement plus facilement ces applications commencer à utiliser ODBC nouvelle *3.x* fonctionnalités à l’intérieur du code conditionnel de façon modulaire. **SQLCloseCursor** ne représente pas de nouvelles fonctionnalités. Une application ne peut pas accéder tout l’avantage en déplaçant vers **SQLCloseCursor** de **SQLFreeStmt** avec SQL_CLOSE.
