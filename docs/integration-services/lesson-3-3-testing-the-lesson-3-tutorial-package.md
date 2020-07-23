---
title: 'Étape 3 : Tester le package du tutoriel de la leçon 3 | Microsoft Docs'
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8a159e1f1e70fefed181f6f47715201731b63dc
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922180"
---
# <a name="lesson-3-3-test-the-lesson-3-tutorial-package"></a>Leçon 3-3 : Tester le package du tutoriel de la leçon 3

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Au cours de cette tâche, vous allez exécuter le package **Lesson 3.dtsx**. Pendant que le package s’exécute, la fenêtre **Événements de journal** liste les entrées de journal écrites par SSIS dans le fichier journal par le module fournisseur d’informations. Une fois que le package a fini de s’exécuter, vous pouvez voir le contenu du fichier journal.  
  
## <a name="check-the-package-layout"></a>Vérifier la disposition du package  
Avant de tester le package, vérifiez que les flux de contrôle et de données du package de la leçon 3 ressemblent aux objets présentés dans les diagrammes suivants. Le flux de contrôle doit être identique à celui de la leçon 2 et le flux de données doit être le même que dans les leçons 1 et 2.  
  
**Flux de contrôle**  
  
![Flux de contrôle dans le package](../integration-services/media/task4lesson2control.gif "Flux de contrôle dans le package")  
  
**Flux de données**  
  
![Flux de données dans le package](../integration-services/media/task9lesson1data.gif "Flux de données dans le package")  
  
## <a name="run-the-lesson-3-tutorial-package"></a>Exécuter le package du tutoriel de la leçon 3  
  
1.  Dans le menu SSIS, sélectionnez **Événements de journal**.  
  
2.  Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.  
  
3.  Une fois l’exécution du package terminée, dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.  
  
## <a name="examine-the-generated-log-file"></a>Examiner le fichier journal généré  
  
-   Utilisez le Bloc-notes ou un autre éditeur de texte et ouvrez le fichier TutorialLog.log.  
  
-   La description complète des informations générées pour les événements **PipelineExecutionPlan** et **PipelineExecutionTrees** n’entre pas dans le cadre de ce tutoriel.  Dans le fichier journal, vous pouvez voir que la première ligne liste les champs d’informations spécifiés sous l’onglet **Détails** de la boîte de dialogue **Configurer les journaux SSIS**. Vous pouvez également voir que [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] a journalisé les deux événements que vous avez sélectionnés, **PipelineExecutionPlan** et **PipelineExecutionTrees** pour chaque itération de la boucle Foreach.  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 4 : Ajouter une redirection de flux d’erreurs avec SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
