---
title: Extraire et mettre à jour des ensembles de lignes (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb0055e8ed8c17679c824fdf6cbf96c1a42c7531
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939589"
---
# <a name="fetch-and-update-rowsets-odbc"></a>Extraire et mettre à jour des ensembles de lignes (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-fetch-and-update-rowsets"></a>Extraire et mettre à jour des ensembles de lignes  
  
1.  Le cas échéant, appelez [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) avec SQL_ROW_ARRAY_SIZE pour modifier le nombre de lignes (R) dans l’ensemble de lignes.  
  
2.  Appelez [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) ou [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) pour obtenir un ensemble de lignes.  
  
3.  Si des colonnes dépendantes sont utilisées, utilisez les valeurs de données et les longueurs de données à présent disponibles dans les tampons de colonnes dépendantes pour l'ensemble de lignes.  
  
     Si des colonnes indépendantes sont utilisées, pour chaque ligne, appelez [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) avec SQL_POSITION pour définir la position du curseur ; ensuite, pour chaque colonne indépendante :  
  
    -   Appelez [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) une ou plusieurs fois pour obtenir les données pour les colonnes indépendantes après la dernière colonne dépendante de l'ensemble de lignes. Les appels à [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) doivent être dans l'ordre croissant des numéros de colonnes.  
  
    -   Appelez plusieurs fois [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) pour obtenir des données à partir d'une colonne text ou image.  
  
4.  Configurez toutes les colonnes image ou text de données en cours d'exécution.  
  
5.  Appelez [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) ou [SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398) pour définir la position du curseur, actualiser, mettre à jour, supprimer ou ajouter une ou des lignes dans l'ensemble de lignes.  
  
     Si des colonnes image ou text de données en cours d'exécution sont utilisées pour une opération de mise à jour ou d'ajout, gérez-les.  
  
6.  Vous pouvez éventuellement exécuter une instruction UPDATE ou DELETE positionnée, en spécifiant le nom de curseur (disponible à partir de [SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md)) et en utilisant un descripteur d'instruction différent sur la même connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des rubriques de procédures de curseurs &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  
