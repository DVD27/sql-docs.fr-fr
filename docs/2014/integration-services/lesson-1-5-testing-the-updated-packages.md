---
title: 'Étape 5 : Test des packages mis à jour | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 979c2b792d7c56dcdb9fadde112c7e6bff789c15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767623"
---
# <a name="step-5-testing-the-updated-packages"></a>Étape 5 : Test des packages mis à jour
  Avant d'aborder la leçon suivante où vous allez créer l'application de déploiement qui sert à installer les packages sur l'ordinateur de destination, vous devez tester les packages. A cours de cette tâche, vous allez exécuter les packages DataTransfer.dtsx et LoadXMLData que vous avez ajoutés au projet Didacticiel de déploiement puis étendus avec des configurations.  
  
 Lors de l'exécution des packages, chaque exécutable du package prend la couleur vert au terme de son exécution correcte. Lorsque tous les exécutables sont vert, le package s'est achevé correctement. Vous pouvez aussi consulter la progression de l'exécution du package sous l'onglet **Progression** .  
  
 Si les packages ne s'exécutent pas correctement, vous devez les corriger avant d'aborder la leçon suivante.  
  
### <a name="to-run-the-datatransfer-package"></a>Pour exécuter le package DataTransfer  
  
1.  Dans l'Explorateur de solutions, cliquez sur DataTransfer.dtsx.  
  
2.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
3.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
### <a name="to-run-the-loadxmldata-package"></a>Pour exécuter le package LoadXMLData  
  
1.  Dans l'Explorateur de solutions, cliquez sur LoadXMLData.dtsx.  
  
2.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
3.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Création de l'application de déploiement](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
![Icône de Integration Services (petite)](media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
