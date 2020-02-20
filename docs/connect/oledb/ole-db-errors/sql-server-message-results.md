---
title: Résultats des messages SQL Server | Microsoft Docs
description: résultats des messages SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 05d731f418bad21f9e8ec32c620b352c5663994a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67994919"
---
# <a name="sql-server-message-results"></a>Résultats des messages SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivantes ne génèrent pas d’ensembles de lignes du pilote OLE DB pour SQL Server ni un nombre de lignes affectées lors de l’exécution :  
  
-   PRINT  
  
-   RAISERROR avec une gravité égale ou inférieure à 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Ces instructions retournent un ou plusieurs messages d'information ou entraînent le renvoi par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de messages d'information au lieu de résultats sous forme d'ensemble de lignes ou de nombre. En cas d'exécution réussie, OLE DB Driver pour SQL Server renvoie S_OK, et les messages sont disponibles pour le consommateur OLE DB Driver pour SQL Server.  
  
 OLE DB Driver pour SQL Server retourne S_OK et possède un ou plusieurs messages d'information disponibles après l'exécution de plusieurs instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou après l'exécution par le consommateur d'une fonction membre OLE DB Driver pour SQL Server.  
  
 Le consommateur du pilote OLE DB pour SQL Server autorisant la spécification dynamique du texte de la requête doit vérifier les interfaces d’erreur après chaque exécution d’une fonction membre, indépendamment de la valeur du code de retour, de la présence ou de l’absence d’une référence d’interface **IRowset** ou **IMultipleResults** retournée, ou d’un nombre de lignes affectées.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../oledb/ole-db-errors/errors.md)  
  
  
