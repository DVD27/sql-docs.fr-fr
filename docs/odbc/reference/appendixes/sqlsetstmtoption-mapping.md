---
title: SQLSetStmtOption, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc4ed430b301f2b191c0586c0a54af19a2d2d526
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091668"
---
# <a name="sqlsetstmtoption-mapping"></a>SQLSetStmtOption, mappage
Lorsqu’une application appelle **SQLSetStmtOption** via une application ODBC *3.x* pilote, l’appel à  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 entraîne comme suit :  
  
-   Si *fOption* indique un attribut d’instruction définie par ODBC est une chaîne, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Si *fOption* indique un attribut d’instruction définie par ODBC qui retourne une valeur d’entier 32 bits, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Si *fOption* indique un attribut d’instruction définis par le pilote, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 Dans les trois cas précédents, le **au paramètre StatementHandle** argument est défini à la valeur de *hstmt*, le *attribut* argument est défini à la valeur de *fOption* et le *ValuePtr* argument est défini sur la valeur en tant que *vParam*.  
  
 Étant donné que le Gestionnaire de pilotes ne sait pas si l’attribut d’instruction définis par le pilote a besoin d’une chaîne ou une valeur entière 32 bits, il doit passer une valeur valide pour le *StringLength* argument de **SQLSetStmtAttr**. Si le pilote a défini une sémantique spéciale pour les attributs d’instruction définis par le pilote et doit être appelée à l’aide de **SQLSetStmtOption**, il doit prendre en charge **SQLSetStmtOption**.  
  
 Si une application appelle **SQLSetStmtOption** pour définir une option d’instruction spécifiques au pilote dans une application ODBC *3.x* pilote et l’option a été défini dans une application ODBC *2.x* version de la pilote, une nouvelle constante de manifeste doit être définie pour l’option dans le système ODBC *3.x* pilote. Si la constante de manifeste ancien est utilisée dans l’appel à **SQLSetStmtOption**, appelle le Gestionnaire de pilotes **SQLSetStmtAttr** avec la *StringLength* argument la valeur 0.  
  
 Lorsqu’une application appelle **SQLSetStmtAttr** à la valeur SQL_ATTR_USE_BOOKMARKS SQL_UB_ON dans une application ODBC *3.x* pilote, l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a la valeur SQL_UB_FIXED. SQL_UB_ON est la même constante en tant que SQL_UB_FIXED. Le Gestionnaire de pilotes passe SQL_UB_FIXED par le biais du pilote. SQL_UB_FIXED a été déconseillée dans ODBC *3.x*, mais une application ODBC *3.x* pilote doit implémenter qu’il fonctionne avec ODBC *2.x* les applications qui utilisent des signets de longueur fixe.  
  
 Pour une application ODBC *3.x* pilote, le Gestionnaire de pilotes ne sont plus vérifie si *Option* est comprise entre SQL_STMT_OPT_MIN et SQL_STMT_OPT_MAX, ou est supérieure à SQL_CONNECT_OPT_DRVR_START.
