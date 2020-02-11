---
title: Analyser des requêtes avec des résultats SHOWPLAN dans SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], Showplan
- Profiler [SQL Server Profiler], Showplan results
- SQL Server Profiler, Showplan results
ms.assetid: 6a2f7727-141c-4f59-8613-2e452bc78467
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0eb13d2997c9b2b29c85489f30a161a96f64c70c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211107"
---
# <a name="analyze-queries-with-showplan-results-in-sql-server-profiler"></a>Analyser des requêtes avec des résultats SHOWPLAN dans SQL Server Profiler
  Vous pouvez ajouter des classes d'événements Showplan à une définition de trace afin que [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] rassemble et affiche les informations de plan de requête dans la trace. Vous pouvez également extraire les événements Showplan des autres événements collectés dans la trace et les enregistrer dans un fichier XML distinct.  
  
 Chacune des procédures suivantes permet d'extraire les événements Showplan de la trace :  
  
-   Au moment de la configuration de la trace, à l’aide de l’onglet **paramètres d’extraction des événements** . Notez que cet onglet n’apparaît pas tant que vous n’avez pas sélectionné l’un des événements Showplan sous l’onglet sélection des **événements** .  
  
-   À l’aide de l’option **Extraire les événements SQL Server** du menu **Fichier** .  
  
-   En extrayant et en enregistrant un événement donné en cliquant avec le bouton droit dessus et en choisissant **Extraire les données d’événement**.  
  
## <a name="showplan-events"></a>Événements Showplan  
 Le tableau suivant répertorie et décrit les événements de trace Showplan.  
  
|Nom d'événement|Description|  
|----------------|-----------------|  
|**Statistiques de performances**|Indique la première mise en cache d'un plan d'exécution compilé, à quel moment il est recompilé et à quel moment il est supprimé de la mémoire cache de plans. La colonne **TextData** contient le plan d’exécution au format XML. Pour plus d’informations, consultez [Classe d’événements Performance Statistics](../../relational-databases/event-classes/performance-statistics-event-class.md).|  
|**Showplan All**|Affiche le plan de requête avec le détail complet des informations de compilation de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutée. Par exemple, il peut afficher des estimations de coût et des listes de colonnes. Pour plus d’informations, consultez [Classe d’événements Showplan All](../../relational-databases/event-classes/showplan-all-event-class.md).|  
|**Showplan All pour la compilation des requêtes**|Générée lorsqu'une requête est compilée ou recompilée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il s’agit de l’équivalent de compilation de l’événement **Showplan All** . **Showplan All** se produit lorsqu’une requête est exécutée. **Showplan All pour la compilation de requête** se produit lorsqu’une requête est compilée. Pour plus d’informations, consultez [Classe d’événements Showplan All for Query Compile](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md).|  
|**Profil Showplan Statistics**|Affiche le plan de requête avec le détail complet des informations de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] en cours d'exécution, dont le nombre réel de lignes traitées dans chaque opération. Pour plus d’informations, consultez [Classe d’événements Showplan Statistics Profile](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md).|  
|**Texte Showplan**|Affiche, sous forme de données binaires, l'arborescence du plan de requête de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] en cours d'exécution. Pour plus d’informations, consultez [Classe d’événements Showplan Text](../../relational-databases/event-classes/showplan-text-event-class.md).|  
|**Showplan Text (non codé)**|Affiche, sous forme de texte, l'arborescence du plan de requête de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] en cours d'exécution. Cette classe d'événements affiche les mêmes informations que la classe Showplan Text, à la différence que celle-ci affiche du texte au lieu de données binaires. Pour plus d’informations, consultez [Classe d’événements Showplan Text &#40;non encodée&#41;](../../relational-databases/event-classes/showplan-text-unencoded-event-class.md).|  
|**Showplan XML**|Affiche le plan de requête avec les données complètes collectées au cours de l'optimisation de la requête. Cet événement est généré seulement quand un plan de requête est optimisé. Pour plus d’informations, consultez [Classe d’événements Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md).|  
|**Showplan XML for Query Compile**|Affiche le plan de requête lorsque la requête est compilée. Pour plus d’informations, consultez [Classe d’événements Showplan XML for Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md).|  
|**Profil Showplan XML Statistics**|Affiche le plan de requête avec le détail complet des informations d'exécution au format XML. Par exemple, cette classe d'événements capture le nombre de lignes traitées par chaque opérateur de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutée. Pour plus d’informations, consultez [Classe d’événements Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie d'événements Performance](../../relational-databases/event-classes/performance-event-category.md)  
  
  
