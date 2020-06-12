---
title: Extension d’OLAP par le biais de personnalisations | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59e63b6be2253c69e0676a0bf33281b441e39b95
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546731"
---
# <a name="extending-olap-through-personalizations"></a>Extension d'OLAP par des personnalisations
  Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] fournit de nombreuses fonctions intrinsèques à utiliser avec les langages MDX (Multidimensional Expressions) et DMX (Data Mining Extensions). Ces fonctions sont conçues pour accomplir toutes les opérations possibles, depuis les calculs statistiques standard jusqu'au parcours des membres d'une hiérarchie. Cependant, comme avec tout autre produit complexe et puissant, il est toujours nécessaire d'étendre les fonctionnalités de ce type d'outil.  
  
 Par conséquent, Analysis Services vous permet d'ajouter des assemblys et des extensions personnalisées à une instance du service, afin de répondre aux besoins de votre entreprise chaque fois que les fonctionnalités standard sont insuffisantes.  
  
## <a name="assemblies"></a>Assemblys  
 Les assemblys vous permettent d'étendre les fonctions d'entreprise de MDX et de DMX. Vous générez les fonctionnalités souhaitées dans une bibliothèque, telle qu'une bibliothèque de liens dynamiques (DLL), puis vous ajoutez cette bibliothèque en tant qu'assembly à une instance d'Analysis Services ou à une base de données Analysis Services. Les méthodes publiques de la bibliothèque sont alors exposées en tant que fonctions définies par l'utilisateur aux expressions, procédures, calculs, actions et applications clientes MDX et DMX.  
  
## <a name="personalized-extensions"></a>Extensions personnalisées  
 Les extensions de personnalisation SQL Server Analysis Services sont la base de l'idée d'implémentation d'une architecture de plug-in. Elles sont une modification simple et élégante de l'architecture d'assembly managée existante et sont exposées partout dans le modèle objet Analysis Services <xref:Microsoft.AnalysisServices.AdomdServer>, la syntaxe MDX (Multidimensional Expressions) et les ensembles de lignes de schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèles multidimensionnels](../multidimensional-model-assemblies-management.md)   
 [Extensions de personnalisation Analysis Services](analysis-services-personalization-extensions.md)  
  
  
