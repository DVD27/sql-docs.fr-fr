---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fb60bfa05e75c06b7da04042aa1abfbd42b756c0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62761908"
---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7915|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Texte du message|Réparation : Chaîne IAM pour l’ID d’objet O_ID, ID d’index I_ID, ID de partition PN_ID, unité d’allocation ID A_ID (type TYPE), a été tronquée avant la page P_ID et sera reconstruite.|  
  
## <a name="explanation"></a>Explication  
 Ceci est un message d'information envoyé par REPAIR, qui indique que la chaîne IAM (Index Allocation Map) spécifiée a été corrigée afin de pouvoir être reconstruite. Cette correction peut avoir requis l'allocation d'une nouvelle tête de la chaîne IAM ou la suppression de pages incorrectes de la chaîne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 None  
  
  
