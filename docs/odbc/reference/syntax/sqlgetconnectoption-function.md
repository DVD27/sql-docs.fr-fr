---
title: Sqlgetconnectoption, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7461304a9aa015eac223dc726e669ad5c4ecd4ce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103833"
---
# <a name="sqlgetconnectoption-function"></a>SQLGetConnectOption, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : Déconseillé  
  
 **Résumé**  
 Dans ODBC *3.x*, ODBC *2.x* fonction **SQLGetConnectOption** a été remplacé par **SQLGetConnectAttr**. Pour plus d’informations, consultez [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md).  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Gestionnaire de pilotes mappe cette fonction lorsqu’une application ODBC *2.x* application fonctionne avec une application ODBC *3.x* pilote, consultez [mappage de fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)dans l’annexe g : Instructions de pilote pour la compatibilité descendante.  
> 
> [!NOTE]
>  Ne prend pas en charge l’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE introduite dans ODBC 3.8 **SQLGetConnectOption**. Applications qui utilisent l’opération asynchrone sur un handle de connexion doivent utiliser **SQLGetConnectAttr**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
