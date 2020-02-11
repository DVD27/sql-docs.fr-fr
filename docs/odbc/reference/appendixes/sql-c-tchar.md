---
title: SQL_C_TCHAR | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 68a03de54a8a5f63a994578d64c6bce5a1279138
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057038"
---
# <a name="sql_c_tchar"></a>SQL_C_TCHAR
L’identificateur de type SQL_C_TCHAR n’identifie pas réellement un type de données ; Il s’agit d’une macro qui existe dans le fichier d’en-tête pour la conversion Unicode. Elle est remplacée par SQL_C_CHAR ou SQL_C_WCHAR en fonction du paramètre de l' **#define**Unicode. Elle est utile pour une application qui transfère des données de type caractère compilées en tant qu’application ANSI et Unicode.
