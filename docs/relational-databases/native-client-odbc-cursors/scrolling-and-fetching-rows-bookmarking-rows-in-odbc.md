---
title: Bookmarking Rows à ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0c1a4216d57d4f8178e55c54f7b0bcf61b8624c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303998"
---
# <a name="scrolling-and-fetching-rows---bookmarking-rows-in-odbc"></a>Défilement et récupération (fetch) de lignes - Ajout de signets aux lignes dans ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Un signet est une valeur utilisée pour identifier une ligne de données. La signification de la valeur du signet est connue uniquement du pilote ou de la source de données. Par exemple, il peut être aussi simple qu'un numéro de ligne ou aussi complexe qu'une adresse disque. Dans ODBC, l'application demande un signet pour une ligne particulière, le stocke, puis le passe au curseur à retourner à la ligne.  
  
 Lorsque vous allez chercher des rangées avec [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md), une application peut utiliser un signet comme base pour sélectionner la ligne de départ. Il s'agit d'une forme d'adressage absolu qui ne dépend pas de la position actuelle du curseur. Pour faire défiler vers une rangée de signets, l’application appelle **SQLFetchScroll** avec une *fetchOrientation* de SQL_FETCH_BOOKMARK. Cette opération utilise le signet vers lequel pointe l'attribut d'option SQL_ATTR_FETCH_BOOKMARK_PTR. Elle retourne l'ensemble de lignes démarrant à la ligne identifiée par ce signet. Une demande peut spécifier une compensation pour cette opération dans l’argument *FetchOffset* de l’appel à **SQLFetchScroll**. Lorsqu'un décalage est spécifié, la première ligne de l'ensemble de lignes retourné est déterminée par l'ajout du nombre présent dans l'argument FetchOffset au numéro de la ligne identifiée par le signet. Le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge uniquement les signets sur les curseurs statiques et les curseurs de jeu de clés. Si un curseur dynamique est demandé lorsque les signets sont définis, un curseur de jeu de clés est ouvert à la place.  
  
 Les signets peuvent également être utilisés avec la fonction **SQLBulkOperations** pour effectuer des opérations sur un ensemble de rangées à partir du signet.  
  
## <a name="see-also"></a>Voir aussi  
 [Défilement et récupération (fetch) de lignes](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
  
