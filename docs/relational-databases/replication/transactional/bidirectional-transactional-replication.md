---
title: Réplication transactionnelle bidirectionnelle | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: b588710d2cd8b74474814a130f8f5b16ec98467e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768258"
---
# <a name="bidirectional-transactional-replication"></a>réplication transactionnelle bidirectionnelle
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Une réplication transactionnelle bidirectionnelle est une topologie de réplication transactionnelle spécifique qui permet à deux serveurs d'échanger des modifications : chaque serveur publie des données puis s'abonne à une publication contenant les mêmes données provenant de l'autre serveur. Le paramètre **@loopback_detection** de [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) a la valeur TRUE pour garantir que les modifications sont uniquement envoyées à l’Abonné et ne renvoient pas la modification au serveur de publication.  
  
 Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et les versions ultérieures, cette topologie est également prise en charge par la réplication transactionnelle d'égal à égal, mais la réplication bidirectionnelle peut contribuer à améliorer les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
