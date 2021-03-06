---
title: Synthétiser ou regrouper des valeurs à l’aide d’expressions personnalisées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5a5ba3f3022e39bc9fb4db7c7af3d62ab9fbe430
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267422"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a>Synthétiser ou regrouper des valeurs à l'aide d'expressions personnalisées (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Si vous pouvez utiliser des fonctions d'agrégation pour agréger des données, vous pouvez également créer des expressions personnalisées afin de générer des valeurs agrégées. Il est possible d'utiliser des expressions personnalisées à la place de fonctions d'agrégation dans une requête Agrégation.  
  
Imaginons que, dans la table `titles` , vous souhaitiez créer une requête qui affiche non seulement le prix moyen mais aussi ce même prix assorti d'une ristourne.  
  
Il est impossible d'inclure une expression basée sur des calculs portant sur des lignes individuelles de la table ; l'expression doit être fondée sur une valeur agrégée dans la mesure où seules les valeurs agrégées sont disponibles au moment du calcul de l'expression.  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a>Pour spécifier une expression personnalisée pour une valeur de synthèse  
  
1.  Spécifiez les groupes de votre requête. Pour plus d’informations, consultez [Regrouper des lignes dans les résultats de requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/group-rows-in-query-results-visual-database-tools.md).  
  
2.  Placez-vous dans une ligne vide du volet Critères et tapez ensuite l’expression dans la colonne **Colonnes**.  
  
    Le [Concepteur de requêtes et de vues](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) assigne automatiquement un alias de colonne à l’expression afin de créer un en-tête de colonne pertinent dans le résultat de la requête. Pour plus d’informations, consultez [Créer des alias de colonnes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md).  
  
3.  Dans la colonne **Grouper par** de l’expression, sélectionnez **Expression**.  
  
4.  Exécute la requête.  
  
## <a name="see-also"></a>Voir aussi  
[Trier et regrouper des résultats de requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Résumer les résultats de la requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
  
