---
title: Niveaux d’isolement (OLE DB) | Microsoft Docs
description: Niveaux d'isolation (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 2c9f3a7cd06f801555ab373e7e54fbf1b620d894
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993975"
---
# <a name="isolation-levels-ole-db"></a>Niveaux d'isolation (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les clients [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent contrôler les niveaux d'isolation des transactions pour une connexion. Pour contrôler le niveau d'isolation des transactions, le consommateur d’OLE DB Driver pour SQL Server utilise :  
  
-   La propriété DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS pour le mode de validation automatique par défaut du pilote OLE DB pour SQL Server.  
  
     La valeur par défaut du pilote OLE DB pour SQL Server pour le niveau est DBPROPVAL_TI_READCOMMITTED.  
  
-   Le paramètre *isoLevel* de la méthode **ITransactionLocal::StartTransaction** pour les transactions de validation manuelle locales.  
  
-   Le paramètre *isoLevel* de la méthode **ITransactionDispenser::BeginTransaction** pour les transactions distribuées coordonnées par MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autorise l'accès en lecture seule au niveau d'isolation de lecture erronée. Tous les autres niveaux restreignent la concurrence en appliquant des verrous aux objets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Comme le client a besoin de niveaux d'accès concurrentiel supérieurs, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applique des restrictions supérieures sur l'accès concurrentiel aux données. Pour maintenir le niveau maximal d’accès concurrentiel aux données, le consommateur du pilote OLE DB pour SQL Server doit contrôler intelligemment ses requêtes pour les niveaux d’accès concurrentiel.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] a introduit le niveau d'isolement d'instantané. Pour plus d’informations, consultez [Utilisation du niveau d’isolement d’instantané](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](../../oledb/ole-db-transactions/transactions.md)  
  
  
