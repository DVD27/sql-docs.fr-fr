---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f137d859fa6f6233e14bc34c6bf50797a4360a98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123291"
---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41333|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Texte du message|Les transactions suivantes doivent accéder à des tables mémoire optimisées et à des procédures stockées compilées en mode natif dans un isolement d’instantané : transactions RepeatableRead, transactions Serializable et transactions qui accèdent aux tables non mémoire optimisées dans l’isolement RepeatableRead ou Serializable.|  
  
## <a name="explanation"></a>Explication  
Des restrictions s'appliquent à l'utilisateur pour des niveaux d'isolement plus élevés, entre des transactions sur disque et des transactions XTP.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Ne tentez pas des opérations de haut niveau d'isolement sur les tables optimisées en mémoire (et les procédures compilées en mode natif) et les tables sur disque.  
  
Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
