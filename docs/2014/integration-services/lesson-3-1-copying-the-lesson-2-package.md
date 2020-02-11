---
title: 'Étape 1 : Copie du package de la leçon 2 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b4458f8fe198ba3d052bcb21bef38975738b2c23
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767461"
---
# <a name="step-1-copying-the-lesson-2-package"></a>Étape 1 : Copie du package de la leçon 2
  Dans cette tâche, vous allez créer une copie du package Lesson 2.dtsx que vous avez créé à la leçon 2. Vous pouvez également ajouter au projet le package final de la leçon 2 fourni avec le didacticiel, puis le copier à la place. Vous utiliserez cette nouvelle copie tout au long de la leçon 3.  
  
### <a name="to-create-the-lesson-3-package"></a>Pour créer le package de la leçon 3  
  
1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas encore ouvert, dans le menu **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2012**et cliquez sur **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier** , cliquez sur **Ouvrir**, cliquez sur **Projet/Solution**, sélectionnez **Didacticiel SSIS** , cliquez sur **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.  
  
3.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Lesson 2.dtsx**et choisissez **Copier**.  
  
4.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS**et choisissez **Coller**.  
  
     Par défaut, le package copié est nommé Lesson 3.dtsx.  
  
5.  Dans Explorateur de solutions, double-cliquez sur la **leçon 3. dtsx** pour ouvrir le package.  
  
6.  Cliquez avec le bouton droit dans l’arrière-plan de l’onglet **Flux de contrôle** , puis cliquez sur **Propriétés**.  
  
7.  Dans le Fenêtre Propriétés, mettez à `Name` jour la `Lesson 3`propriété avec la valeur.  
  
8.  Cliquez sur la zone de la propriété **ID** , puis dans la liste, cliquez sur ** \<générer un nouvel ID>**.  
  
### <a name="to-add-the-completed-lesson2-package"></a>Pour ajouter le package final de la leçon 2  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , puis le projet SSIS Tutorial.  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS**, puis cliquez sur **Ajouter le package existant**.  
  
3.  Dans la boîte de dialogue **Ajouter une copie des packages existants** , sous **Emplacement du package**, sélectionnez **Système de fichiers**.  
  
4.  Cliquez sur le bouton de navigation **(...)** , accédez à **Lesson 2.dtsx** sur votre ordinateur, puis cliquez sur **Ouvrir**.  
  
     Pour télécharger tous les packages de leçons de ce didacticiel, procédez comme suit.  
  
    1.  Accéder aux [exemples de produits Integration Services](https://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l'onglet **DOWNLOADS** (Téléchargements).  
  
    3.  Cliquez sur le fichier SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiez et collez le package de la leçon 3 selon les étapes 3 à 8 décrites dans la procédure précédente.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Ajout et configuration de la journalisation](lesson-3-2-adding-and-configuring-logging.md)  
  
  
