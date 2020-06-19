---
title: 'Étape 3 : Test du package de la leçon 6 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c78ccd21b39cd882c037f44c0b37c5deb3bc06d8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84951479"
---
# <a name="step-3-testing-the-lesson-6-package"></a>Étape 3 : Test du package de la leçon 6
  Au moment de l'exécution, votre package obtient la valeur de la propriété Directory à partir du paramètre VarFolderName.  
  
 Pour vérifier si le package met à jour la propriété Directory avec la nouvelle valeur lors de l'exécution, exécutez tout simplement le package. Étant donné que seuls trois fichiers de données exemple ont été copiés dans le nouveau répertoire, le flux de données ne sera exécuté que trois fois au lieu de parcourir les 14 fichiers du dossier d'origine.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
 Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 6 contiennent les objets affichés dans les diagrammes suivants. Le flux de contrôle doit être identique au flux de contrôle de la leçon 5. Le flux de données doit être identique au flux de données de la leçon 5.  
  
 **Workflow de contrôle**  
  
 ![Workflow de contrôle](../../2014/tutorials/media/task3lesson6control.jpg "Flux de contrôle")  
  
 **Flux de données**  
  
 ![Flux de données](../../2014/tutorials/media/task3lesson6data.jpg "Data Flow")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>Pour tester le package du didacticiel de la leçon 6  
  
1.  Dans le menu Déboguer, cliquez sur Démarrer le débogage.  
  
2.  Une fois l'exécution du package terminée, dans le menu Déboguer, cliquez sur Arrêter le débogage.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 4 : Déploiement du package de la leçon 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
