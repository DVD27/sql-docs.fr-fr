---
title: Découverte des métadonnées | Microsoft Docs
description: Découverte des métadonnées dans OLE DB pilote pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 9891e5708110be83a4ef33cb2a142accaf93ffe2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989064"
---
# <a name="metadata-discovery"></a>Découverte des métadonnées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L’amélioration de la découverte des métadonnées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] permet aux applications OLE DB Driver pour SQL Server de s’assurer que les métadonnées de colonne ou de paramètre retournées par l’exécution d’une requête sont identiques ou conformes au format des métadonnées que vous avez spécifié avant l’exécution de la requête. Vous recevrez une erreur si les métadonnées retournées après l'exécution de la requête ne sont pas compatibles avec le format des métadonnées que vous avez spécifié avant l'exécution de la requête.  
  
 Dans bcp ainsi que dans les interfaces IBCPSession et IBCPSession2, vous pouvez maintenant spécifier une lecture différée (découverte des métadonnées retardée) pour éviter la découverte de métadonnées pour des opérations de requête. Cela améliore la performance et élimine les échecs de découverte des métadonnées.  
  
 Si vous développez une application avec OLE DB Driver pour SQL Server, mais que vous vous connectez à une version du serveur antérieure à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], les fonctionnalités de découverte des métadonnées correspondront à la version du serveur.  
  
## <a name="remarks"></a>Notes   
 Les fonctions membres OLE DB suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] pour fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: GetParameterInfo (pour plus d’informations, consultez [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) )  
  
 Vous noterez également une amélioration des performances lors de la spécification du format de métadonnées avec IBCPSession::BCPSetBulkMode  
  
 L’amélioration de la découverte des métadonnées dans OLE DB pilote pour SQL Server est possible en raison de l’ajout [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]de deux procédures stockées dans:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
