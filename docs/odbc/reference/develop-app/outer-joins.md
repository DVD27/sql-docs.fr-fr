---
title: Jointures externes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4bf875b3afd21f6b8cb211c999401b0ecb80879
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987816"
---
# <a name="outer-joins"></a>Jointures externes
ODBC prend en charge le SQL-92 left, syntaxe de jointure externe complète, droite et complète. Est la séquence d’échappement pour les jointures externes  
  
 **{oj** _outer-join_ **}**  
  
 où *jointure externe* est  
  
 *référence de table* {**gauche &#124; droite &#124; complète} jointure externe** {*référence de table* &#124; *jointure externe*} **ON**  _condition de recherche_  
  
 *référence de table* spécifie un nom de table, et *condition de recherche* spécifie la condition de jointure entre la *références de table*.  
  
 Une requête de jointure externe doit apparaître après le **FROM** mot clé et avant le **où** clause (le cas échéant). Pour plus d’informations sur la syntaxe complète, consultez [séquence d’échappement de jointure externe](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) dans l’annexe c : Grammaire SQL.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats qui répertorie tous les clients et montre ce qui a des commandes en cours. La première instruction utilise la syntaxe de la séquence d’échappement. La deuxième instruction utilise la syntaxe native pour Oracle et n’est pas interopérable.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Pour déterminer les types de jointures externes qui prennent en charge une source de données et le pilote, une application appelle **SQLGetInfo** avec la SQL_OJ_CAPABILITIES indicateur. Les types de jointures externes qui peuvent être prises en charge sont gauche, droite, complète ou imbriqué des jointures externes ; jointures externes dans lequel les noms des colonnes dans le **ON** clause n’ont pas le même ordre que leurs noms de table concernée dans le **OUTER JOIN** clause ; les jointures internes conjointement avec des jointures externes ; et à l’aide de jointures externes opérateur de comparaison quelconque ODBC. Si le type d’information SQL_OJ_CAPABILITIES retourne 0, aucune clause de jointure externe n’est prise en charge.
