---
title: Gestionnaire de connexions de nettoyage DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: faa1eedd-db14-41e5-8e58-8f0f6f561e42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 204fe65afa6684a3090c226d2fc5a028aa5f4079
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71294439"
---
# <a name="dqs-cleansing-connection-manager"></a>Gestionnaire de connexions de nettoyage DQS

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un gestionnaire de connexions de nettoyage DQS permet à un package de se connecter à un serveur [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] . La transformation de nettoyage DQS utilise le gestionnaire de connexions de nettoyage DQS.  
  
 Pour plus d’informations sur Data Quality Services, consultez [Concepts Data Quality Services](../../data-quality-services/data-quality-services-concepts.md).  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions de nettoyage DQS prend en charge uniquement l'authentification Windows.  
  
## <a name="related-tasks"></a>Tâches associées  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation. Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur de transformation de nettoyage DQS](../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez la documentation de la classe <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> dans le Guide du développeur.  
  
  
