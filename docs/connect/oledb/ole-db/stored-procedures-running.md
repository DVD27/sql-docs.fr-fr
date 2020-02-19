---
title: Exécution de procédures stockées (OLE DB) | Microsoft Docs
description: Exécution de procédures stockées (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 4297feae08376871c68ffab2aa9b977e034c6364
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67993804"
---
# <a name="stored-procedures---running"></a>Procédures stockées - Exécution
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Lorsque vous exécutez des instructions, appeler une procédure stockée sur la source de données (au lieu d'exécuter ou de préparer directement une instruction dans l'application cliente) peut fournir :  
  
-   des performances accrues ;  
  
-   une charge réseau réduite ;  
  
-   une cohérence améliorée ;  
  
-   une précision améliorée ;  
  
-   des fonctionnalités supplémentaires.  
  
 Le fournisseur OLE DB Driver pour SQL Server prend en charge trois des mécanismes que les procédures stockées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisent pour retourner des données :  
  
-   Chaque instruction SELECT dans la procédure génère un jeu de résultats.  
  
-   La procédure peut retourner des données par l'intermédiaire de paramètres de sortie.  
  
-   La procédure peut avoir un code de retour de type entier.  
  
 L'application doit être en mesure de gérer toutes ces sorties provenant de procédures stockées.  
  
 Des fournisseurs OLE DB différents retournent des paramètres de sortie et des valeurs de retour à des moments différents pendant le traitement des résultats. Dans le cas du pilote OLE DB pour SQL Server, les paramètres de sortie et les codes de retour ne sont pas fournis tant que le consommateur n’a pas extrait ou annulé les jeux de résultats retournés par la procédure stockée. Les codes de retour et les paramètres de sortie sont retournés dans le dernier paquet TDS provenant du serveur.  
  
 Les fournisseurs utilisent la propriété DBPROP_OUTPUTPARAMETERAVAILABILITY pour signaler quand les paramètres de sortie et les valeurs de retour sont retournés. Cette propriété figure dans le jeu de propriétés DBPROPSET_DATASOURCEINFO.  
  
 Le pilote OLE DB pour SQL Server définit la propriété DBPROP_OUTPUTPARAMETERAVAILABILITY sur DBPROPVAL_OA_ATROWRELEASE pour indiquer que les codes de retour et les paramètres de sortie ne sont pas retournés tant que le jeu de résultats n’est pas traité ou libéré.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées](../../oledb/ole-db/stored-procedures.md)  
  
  
