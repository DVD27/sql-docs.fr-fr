---
title: Ajouter des colonnes à des requêtes
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- queries [SQL Server], columns
- adding columns
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: b6638a8b5a749c833d2d50ca0dc6fba78d61038c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75244186"
---
# <a name="add-columns-to-queries-visual-database-tools"></a>Ajouter des colonnes à des requêtes (Visual Database Tools)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Pour pouvoir utiliser une colonne dans une requête, vous devez l'ajouter à cette requête. Vous pouvez ajouter une colonne pour l'afficher dans le résultat d'une requête, l'utiliser à des fins de tri, y effectuer des recherches ou encore totaliser ses données. Vous pouvez spécifier les colonnes de la requête qui doivent être comprises dans le volet Résultats lors de l'exécution de la requête. Pour plus d’informations, consultez [Supprimer des colonnes des résultats d’une requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/remove-columns-from-query-results-visual-database-tools.md).  
  
> [!NOTE]  
> Pour afficher le type de données d’une colonne dans le Concepteur de requêtes et de vues, sélectionnez la table ou l’objet table dans le **Volet Schéma** puis cliquez sur Liste des colonnes dans la fenêtre de propriétés. Ensuite, cliquez sur le **bouton de sélection (...)** pour ouvrir la boîte de dialogue **Liste des colonnes**.  
  
Chaque fois que vous utilisez une colonne dans une requête, vous pouvez également utiliser une expression composée de toute association de colonnes, de littéraux, d'opérateurs et de fonctions.  
  
### <a name="to-add-an-individual-column"></a>Pour ajouter une colonne individuelle  
  
-   Dans le **Volet Schéma**, cochez la case située à côté de la colonne que vous souhaitez ajouter.  
  
    -ou-  
  
-   Dans le **Volet Critères**, accédez à la première ligne vierge de la grille, cliquez sur le champ de la colonne **Colonne** et sélectionnez un nom de colonne dans la liste déroulante.  
  
### <a name="to-add-all-columns-for-one-table-or-table-valued-object"></a>Pour ajouter toutes les colonnes d'une table ou d'un objet table  
  
-   Dans le **Volet Diagramme**, cochez la case située en regard de **&#42;(Toutes les colonnes)** .  
  
### <a name="to-add-all-columns-for-all-tables-and-table-structured-objects"></a>Pour ajouter toutes les colonnes de l'ensemble des tables ou des objets structurés comme des tables  
  
1.  Vérifiez qu’aucune ligne de jointure n’est sélectionnée dans le volet **Table Operations** (Opérations sur les tables).  
  
2.  Cliquez avec le bouton droit dans l’espace vide de la fenêtre Design et sélectionnez **Propriétés** dans le menu contextuel.  
  
3.  Dans la fenêtre Propriétés, cliquez sur **Sélectionne toutes les colonnes** et choisissez **Oui** ou **Non** dans la liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
[Supprimer des colonnes des résultats d’une requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/remove-columns-from-query-results-visual-database-tools.md)  
[Supprimer des colonnes des requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/remove-columns-from-queries-visual-database-tools.md)  
[Spécifier des critères de recherche &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Résumer les résultats de la requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
