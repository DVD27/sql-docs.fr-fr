---
title: Gérer des fichiers avec encodage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22b1c18cba793d5845e2adf92b1dca300911a72f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62823796"
---
# <a name="manage-files-with-encoding"></a>Gérer des fichiers avec encodage
  Pour faciliter l'affichage de votre code dans un langage particulier ou sur une plateforme spécifique, vous pouvez associer un encodage de caractères déterminé à un fichier.  
  
## <a name="opening-files"></a>Ouverture de fichiers  
 Vous pouvez choisir l'éditeur que vous souhaitez utiliser pour modifier le fichier.  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a>Pour ouvrir un fichier avec un éditeur spécifique  
  
1.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier**.  
  
2.  Dans la boîte de dialogue **Ouvrir un fichier** , sélectionnez le nom du fichier.  
  
3.  Cliquez sur la flèche en regard du bouton **Ouvrir** , puis sur**Ouvrir avec** dans le menu qui s’affiche.  
  
4.  Dans la liste **Sélectionnez le programme à ouvrir** , sélectionnez un éditeur, puis cliquez sur **Ouvrir**. Pour ouvrir le fichier à l'aide d'un encodage particulier, sélectionnez un éditeur prenant en charge l'encodage, tel que l'Éditeur de requête SQL avec encodage ou l'Éditeur XML avec encodage.  
  
## <a name="saving-files"></a>Enregistrement de fichiers  
 Vous pouvez également enregistrer votre code avec un encodage Unicode ou une autre page de codes pour prendre en charge plusieurs langues, par exemple Europe de l'Ouest ou Europe de l'Est. Vous pouvez associer un encodage de caractères particulier à un fichier pour faciliter l'affichage de votre code dans cette langue, ainsi qu'un type de fin de ligne pour prendre en charge un système d'exploitation déterminé. De plus, certains caractères, lorsqu'ils sont utilisés dans des noms de fichiers, ne peuvent pas être enregistrés autrement qu'avec un encodage Unicode.  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a>Pour enregistrer un fichier avec un encodage ou un type de fin de ligne différent  
  
1.  Sur le **fichier** menu, cliquez sur **enregistrer \<filename > comme**.  
  
2.  Dans la boîte de dialogue **Enregistrer le fichier sous** , développez le bouton **Enregistrer** , puis cliquez sur **Enregistrer avec l’encodage**.  
  
3.  Dans la boîte de dialogue **Options d’enregistrement avancées** , sélectionnez l’encodage de votre choix dans la liste **Encodage** .  
  
4.  Dans la liste **Fins de ligne**, sélectionnez le type de fin de ligne souhaité.  
  
    > [!NOTE]  
    >  Si vous enregistrez votre fichier avec un encodage Unicode, il doit être archivé dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] comme un fichier binaire, car cette application ne prend pas en charge la fusion, la comparaison et l'affichage des différences entre les fichiers enregistrés au format Unicode.  
  
 Si vous utilisez Visual SourceSafe pour stocker des fichiers ANSI, UTF-8 ou Unicode, gardez à l'esprit les limites suivantes relatives à chacun de ces formats :  
  
-   Les fichiers ANSI acceptent uniquement les caractères qui sont pris en charge dans la page de codes en cours, ce qui limite l'usage international.  
  
-   Les fichiers Unicode ne peuvent pas utiliser les fonctionnalités d'extraction en mode partagé, de contrôle des différences ou de fusion, car ils sont traités en tant que fichiers binaires. Vous pouvez utiliser ce format dans les fichiers internationaux.  
  
-   Les fichiers UTF8 ne fonctionnent pas de façon fiable avec Visual SourceSafe, car les modifications doivent être apportées pendant l'archivage, l'extraction, le contrôle des différences et la fusion, ce qui provoque des problèmes pour les éditeurs de fichier UTF8.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers gérant les Solutions et projets](files-that-manage-solutions-and-projects.md)   
 [Associer des extensions de fichier à un éditeur de code](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
  
  
