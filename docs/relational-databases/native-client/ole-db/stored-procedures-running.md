---
title: Exécution de procédures stockées (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b139200b9c4e574fe79ab4a0306368a88b191d4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031845"
---
# <a name="stored-procedures---running"></a>Procédures stockées - Exécution
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Lorsque vous exécutez des instructions, appeler une procédure stockée sur la source de données (au lieu d'exécuter ou de préparer directement une instruction dans l'application cliente) peut fournir :  
  
-   des performances accrues ;  
  
-   une charge réseau réduite ;  
  
-   une cohérence améliorée ;  
  
-   une précision améliorée ;  
  
-   des fonctionnalités supplémentaires.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge trois des mécanismes qui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisent des procédures stockées pour retourner des données :  
  
-   Chaque instruction SELECT dans la procédure génère un jeu de résultats.  
  
-   La procédure peut retourner des données par l'intermédiaire de paramètres de sortie.  
  
-   La procédure peut avoir un code de retour de type entier.  
  
 L'application doit être en mesure de gérer toutes ces sorties provenant de procédures stockées.  
  
 Des fournisseurs OLE DB différents retournent des paramètres de sortie et des valeurs de retour à des moments différents pendant le traitement des résultats. Dans le cas de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif, les paramètres de sortie et les codes de retour ne sont pas fournis tant que le consommateur a récupéré ou annulé les jeux de résultats retournés par la procédure stockée. Les codes de retour et les paramètres de sortie sont retournés dans le dernier paquet TDS provenant du serveur.  
  
 Les fournisseurs utilisent la propriété DBPROP_OUTPUTPARAMETERAVAILABILITY pour signaler quand les paramètres de sortie et les valeurs de retour sont retournés. Cette propriété figure dans le jeu de propriétés DBPROPSET_DATASOURCEINFO.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif définit la propriété DBPROP_OUTPUTPARAMETERAVAILABILITY sur DBPROPVAL_OA_ATROWRELEASE pour indiquer que codes de retour et les paramètres de sortie ne sont pas retournées jusqu'à ce que le jeu de résultats est traité ou libéré.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
  
