---
title: Conformité de SQL-92 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5d8ed2818b466d16591be8b70478221d7ac84df
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063370"
---
# <a name="sql-92-compliance"></a>Conformité à SQL-92
Les pilotes de base de données ODBC Desktop et le moteur Microsoft Jet sous-jacente ne sont pas conformes SQL-92. Ils prennent en charge de nombreuses fonctionnalités qui ont été définies dans SQL-92. Certaines fonctionnalités prises en charge dans le pilote ne sont pas pris en charge dans SQL-92. Pour plus d’informations, consultez le *-Guide du programmeur moteur Microsoft Jet de base de données*. Voici les principales différences entre les deux :  
  
-   Le SQL utilisé par les pilotes de base de données Desktop prend en charge des expressions plus puissantes que ceux spécifiés par SQL-92.  
  
-   Différentes règles s’appliquent au prédicat BETWEEN.  
  
-   Le SQL utilisé par les pilotes de base de données de bureau et ANSI SQL prend en charge les mots clés différents.  
  
 Les fonctionnalités de SQL-92 suivantes ne sont pas pris en charge par Microsoft Jet SQL :  
  
-   Instructions de sécurité, telles que GRANT et de verrouillage.  
  
-   DISTINCT avec des références de la fonction d’agrégation.  
  
 Les fonctionnalités suivantes sont des améliorations dans le SQL utilisé par les pilotes de base de données de bureau qui ne sont pas spécifiées par SQL-92 :  
  
-   L’instruction de transformation prise en charge pour les requêtes d’analyse croisée.  
  
-   Fonctions d’agrégation supplémentaires (**StDev** et **VarP**).  
  
> [!NOTE]  
>  Les pilotes de base de données Desktop prend en charge la syntaxe ANSI standard (pourcentage) et _ (caractère de soulignement) pas * (astérisque) et ? (point d’interrogation).
