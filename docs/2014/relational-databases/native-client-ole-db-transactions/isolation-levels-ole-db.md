---
title: Niveaux d’isolation (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a18986af71f652a833f413ee1fa62ca2fd44ba06
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63215992"
---
# <a name="isolation-levels-ole-db"></a>Niveaux d'isolation (OLE DB)
  Les clients [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent contrôler les niveaux d'isolation des transactions pour une connexion. Pour contrôler le niveau d’isolation des transactions, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur de fournisseur OLE DB Native Client utilise :  
  
-   Propriété DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mode de validation automatique de valeur par défaut de fournisseur OLE DB Native Client.  
  
     Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valeur par défaut du fournisseur OLE DB Native Client pour le niveau est DBPROPVAL_TI_READCOMMITTED.  
  
-   Le paramètre *isoLevel* de la méthode **ITransactionLocal::StartTransaction** pour les transactions de validation manuelle locales.  
  
-   Le paramètre *isoLevel* de la méthode **ITransactionDispenser::BeginTransaction** pour les transactions distribuées coordonnées par MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autorise l'accès en lecture seule au niveau d'isolation de lecture erronée. Tous les autres niveaux restreignent la concurrence en appliquant des verrous aux objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Comme le client a besoin de niveaux d'accès concurrentiel supérieurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applique des restrictions supérieures sur l'accès concurrentiel aux données. Pour maintenir le niveau le plus élevé d’accès concurrentiel aux données, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client doit contrôler intelligemment ses demandes pour les niveaux d’accès concurrentiel spécifique.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a introduit le niveau d'isolement d'instantané. Pour plus d’informations, consultez [Utilisation du niveau d’isolement d’instantané](../native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](transactions.md)  
  
  
