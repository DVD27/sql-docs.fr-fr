---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b013811054647a05dbb7298955ebc2f8c203d38
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101463"
---
# <a name="mssqlserver_8621"></a>MSSQLSERVER_8621
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|8621|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|OPTIMIZER_STACK_OVERFLOW_ERR|  
|Texte du message|Espace de pile du processeur de requêtes insuffisant lors de l'optimisation de la requête. Simplifiez la requête.|  
  
## <a name="explanation"></a>Explication  
La taille de la requête développée est la cause la plus probable de l'erreur. La requête développée substitue dans la requête d'origine les définitions de toutes les vues, colonnes calculées, fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] et expressions de table commune auxquelles elle fait référence, ainsi que les actions en cascade telles que la mise à jour des index secondaires, des vues et des déclencheurs.  
  
La requête possède probablement une dimension importante ; par exemple, le nombre de tables référencées par les définitions de vues ou une expression scalaire très importante.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Simplifiez la requête en la divisant en plusieurs requêtes le long de la dimension la plus importante. Commencez par supprimer tous les éléments de la requête qui ne sont pas réellement nécessaires, puis essayez d'ajouter une table temporaire et de diviser la requête en deux.  Le simple déplacement d'une partie de la requête vers une sous-requête, une fonction ou une expression de table commune ne suffit pas, car ces éléments sont réassociés par le compilateur [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
