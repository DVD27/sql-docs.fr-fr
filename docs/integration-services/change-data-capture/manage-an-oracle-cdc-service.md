---
title: Gérer un service Oracle CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 50de6cd55b2dcd916967e241ae9b62a2a960df06
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101694"
---
# <a name="manage-an-oracle-cdc-service"></a>Gérer un Service de capture de données modifiées Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Vous pouvez utiliser la console de configuration du service de capture de données modifiées pour gérer un service de capture de données modifiées spécifique.  
  
 **Pour sélectionner le service de capture de données modifiées à utiliser**  
  
1.  Dans le volet gauche de la console de configuration du service de capture de données modifiées, développez **Services de capture de données modifiées locaux**.  
  
2.  Sélectionnez le service de capture de données modifiées à utiliser.  
  
     Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées que vous souhaitez utiliser et sélectionner l'action souhaitée. Consultez [Opérations possibles avec un service de capture de données modifiées](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
 **OR**  
  
1.  Sélectionnez **Services de capture de données modifiées locaux** dans le volet gauche de la console de configuration du service de capture de données modifiées.  
  
2.  Dans la section centrale de la console de configuration du service de capture de données modifiées, sélectionnez le service que vous souhaitez utiliser.  
  
     Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées que vous souhaitez utiliser et sélectionner l'action souhaitée. Consultez [Opérations possibles avec un service de capture de données modifiées](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> Que pouvez-vous faire avec un Service de capture de données modifiées  
 Vous pouvez effectuer les actions suivantes lorsque vous utilisez un service de capture de données modifiées.  
  
### <a name="delete-the-service"></a>Supprimer le service  
 Dans le volet **Actions** à droite de la console de configuration du service de capture de données modifiées, cliquez sur **Supprimer** pour supprimer le service.  
  
 Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées à supprimer et sélectionner **Supprimer**.  
  
 **Remarque** : Si le service est en cours d'exécution lors de sa suppression, il est arrêté avant d'être supprimé.  
  
 Pour supprimer la définition de service Windows de capture de données modifiées Oracle, le programme doit disposer d'un accès de mise à jour à la base de données MSXDBCDC dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associée. Lorsque vous cliquez sur OK pour supprimer le service, le programme tente de supprimer l'inscription du service de capture de données modifiées Oracle dans la base de données MSXDBCDC. Si le programme ne peut pas supprimer l'inscription du service de capture de données modifiées Oracle, car il ne dispose pas des autorisations appropriées, il invite l'utilisateur à entrer une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec des autorisations de mise à jour de la base de données MSXDBCDC.  
  
 Pour plus d'informations sur les données que vous devez taper dans la boîte de dialogue Connexion à SQL Server, consultez [Connection to SQL Server for Delete](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md).  
  
### <a name="edit-the-cdc-service-properties"></a>Modifier les propriétés de service de capture de données modifiées  
 Dans le volet **Actions** à droite de la console de configuration du service de capture de données modifiées, cliquez sur **Propriétés**.  
  
 Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées où vous souhaitez modifier les propriétés et sélectionner **Propriétés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour gérer un service CDC local](../../integration-services/change-data-capture/how-to-manage-a-local-cdc-service.md)  
  
  
