---
title: Enregistrer les événements Showplan XML Statistics Profile séparément (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: df393f13-d538-4d94-8155-9c2fdf5f755d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 79f3f41d4224baacd485c7d2151db0f3f2059f86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150626"
---
# <a name="save-showplan-xml-statistics-profile-events-separately-sql-server-profiler"></a>Enregistrer les événements Showplan XML Statistics Profile séparément (SQL Server Profiler)
  Cette rubrique décrit comment enregistrer dans des fichiers .SQLPlan séparés les événements **Showplan XML Statistics Profile** capturés dans les traces à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous pouvez ouvrir les fichiers des événements **Showplan XML Statistics Profile** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], qui vous permet d'afficher le plan d'exécution graphique de chaque événement.  
  
### <a name="to-save-showplan-xml-statistics-events-separately"></a>Pour enregistrer séparément les événements de statistiques XML du plan d'exécution  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace** s'affiche.  
  
    > [!NOTE]  
    >  Si la case à cocher **Démarrer le suivi juste après avoir établi la connexion**est activée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et la trace démarre. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace** de la boîte de dialogue **Propriétés de la trace** , entrez le nom de la trace.  
  
3.  Dans la liste **Utiliser le modèle** , sélectionnez un modèle sur lequel baser la trace ou sélectionnez **Vide** pour ne pas utiliser de modèle.  
  
4.  Procédez de l'une des manières suivantes :  
  
    -   Cliquez sur**Enregistrer dans le fichier**pour capturer la trace dans un fichier. Spécifiez une valeur dans **Définir la taille de fichier maximale**.  
  
         Éventuellement, sélectionnez **Activer la substitution de fichiers** et **Données de traces des processus serveur**.  
  
    -   Cliquez sur**Enregistrer dans la table** pour capturer la trace dans une table de base de données.  
  
         Éventuellement, spécifiez une valeur dans **Définir le nombre de lignes maximal**.  
  
5.  Éventuellement, activez la case à cocher **Activer l'heure d'arrêt de la trace** pour indiquer une date et une heure d'arrêt.  
  
6.  Cliquez sur l’onglet **Sélection des événements**.  
  
7.  Dans la zone **Events**, développez la catégorie d’événements **Performances**, puis activez la case à cocher **Showplan XML Statistics Profile**. Si la catégorie d'événements **Performance** n'est pas visible, activez la case à cocher **Afficher tous les événements** pour l'afficher.  
  
     La boîte de dialogue **Paramètres d’extraction des événements**est ajouté à la boîte de dialogue **Propriétés de la trace**.  
  
8.  Dans le menu **Paramètres d’extraction des événements**, cliquez sur **Enregistrer les événements Showplan XML séparément**.  
  
9. Dans la boîte de dialogue **Enregistrer sous** , entrez le nom du fichier qui stocke les événements **Showplan XML Statistics Profile** .  
  
10. Cliquez sur **Tous les traitements Showplan XML dans un seul fichier** pour enregistrer tous les événements **Showplan XML Statistics Profile** dans un même fichier XML ou sur **Chaque traitement Showplan XML dans un fichier différent**pour créer un nouveau fichier XML pour chaque événement **Showplan XML Statistics Profile** .  
  
11. Pour afficher le fichier des événements **Showplan XML Statistics Profile** dans SQL Server Management Studio, dans le menu **Fichier** , pointez sur **Ouvrir**et cliquez sur **Fichier**. Placez-vous dans le répertoire où vous avez enregistré le ou les fichiers des événements **Showplan XML Statistics Profile** pour en sélectionner un et l'ouvrir. Les fichiers des événements**Showplan XML Statistics Profile** possèdent l'extension .SQLPlan.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser des requêtes avec des résultats SHOWPLAN dans SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
