---
title: Prise en charge des Types de données (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2d23ddc5fdd00db45aee235e96f13a8cf08082a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080784"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Types de données pris en charge (pilote ODBC Visual FoxPro)
La liste des types de données pris en charge par le pilote sont présentées via l’API ODBC et dans Microsoft Query.  
  
## <a name="data-types-in-c-applications"></a>Types de données dans les Applications C  
 Vous pouvez obtenir une liste des types de données pris en charge par le pilote ODBC Visual FoxPro à l’aide de la [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) fonction dans les applications C ou C++.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Types de données dans les Applications à l’aide de Microsoft Query  
 Si votre application utilise Microsoft Query pour créer une nouvelle table sur une source de données Visual FoxPro, Microsoft Query affiche le **nouvelle définition de Table** boîte de dialogue. Sous **Description du champ**, le **Type** zone listes [types de données Visual FoxPro](../../odbc/microsoft/visual-foxpro-field-data-types.md), représenté par les caractères uniques.
