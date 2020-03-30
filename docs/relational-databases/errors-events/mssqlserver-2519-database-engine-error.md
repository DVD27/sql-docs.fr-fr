---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 233d7d3a6ae29fe2e83272f36ed3e952e8bdd1dc
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68138483"
---
# <a name="mssqlserver_2519"></a>MSSQLSERVER_2519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2519|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_NO_EXPRESSION_EVALUATOR|  
|Texte du message|Impossible de vérifier les colonnes calculées et les types définis par l'utilisateur pour l'ID d'objet O_ID (objet « O_NAME ») car l'évaluateur d'expression interne n'a pas pu être initialisé.|  
  
## <a name="explanation"></a>Explication  
Ce message d'information indique que le processeur de requêtes n'a pas pu fournir à DBCC un objet interne pour permettre l'évaluation de colonnes calculées et de types clr (common language runtime) définis par l'utilisateur. Cela signifie que l'exactitude des colonnes calculées et des types clr définis par l'utilisateur ne sera pas vérifiée et que ceux-ci ne seront pas utilisés lorsque DBCC vérifiera la cohérence entre les index et les tables de base.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
## <a name="see-also"></a>Voir aussi  
[MSSQLSERVER_2518](~/relational-databases/errors-events/mssqlserver-2518-database-engine-error.md)  
  
