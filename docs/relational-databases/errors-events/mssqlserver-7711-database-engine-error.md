---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bdfc39abde5603287486cd13ed1c67e746640ad7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67951585"
---
# <a name="mssqlserver_7711"></a>MSSQLSERVER_7711
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|7711|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PRT_RANGE_OVERLAP|  
|Texte du message|L’option DATA_COMPRESSION a été spécifiée plusieurs fois pour la table, l’index, ou l’une de leurs partitions.|  
  
## <a name="explanation"></a>Explication  
Une erreur s'est produite dans l'option DATA_COMPRESSION dans l'une des instructions suivantes :  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
Si la table ou l'index cité est partitionné, l'option DATA_COMPRESSION a été répertoriée plusieurs fois pour au moins l'une des partitions. Si la table ou l'index n'est pas partitionné, l'option DATA_COMPRESSION a été citée plusieurs fois.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour une table partitionnée ou un index, assurez-vous que l'option DATA_COMPRESSION n'est spécifiée qu'une seule fois pour chaque partition. Pour une table ou un index qui n'est pas partitionné, utilisez l'option DATA_COMPRESSION une seule fois dans l'instruction.  
  
