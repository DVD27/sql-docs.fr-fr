---
title: Enlever ou supprimer un élément ou un projet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dd6d04b186c68b128ad35ec5e5bd8b92ad1541c0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63035667"
---
# <a name="remove-or-delete-an-item-or-project"></a>Enlever ou supprimer un élément ou un projet
  Les éléments de projet des projets [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sont les requêtes, les connexions et les fichiers divers. Vous pouvez enlever des requêtes et des fichiers divers de projet d'une solution sans effacer du support de stockage les fichiers. Supprimez un projet ou un élément lorsqu'il n'est plus utile dans la solution en cours mais que vous souhaitez l'insérer dans une autre solution.  
  
### <a name="to-remove-a-project-item"></a>Pour supprimer un élément de projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez l'élément de projet à enlever.  
  
2.  Dans le menu **Edition** , cliquez sur **Enlever**.  
  
3.  Dans la boîte de dialogue de confirmation, cliquez sur **Enlever** pour enlever l’élément du projet.  
  
 Un élément enlevé existe toujours dans le système de fichiers. Par conséquent, après avoir enlevé un élément, vous pouvez toujours l'ajouter à sa solution initiale ou à une autre solution.  
  
#### <a name="to-remove-a-project"></a>Pour enlever un projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet à enlever.  
  
2.  Dans le menu **Edition** , cliquez sur **Enlever**.  
  
3.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**pour enlever le projet de la solution.  
  
 Vous pouvez supprimer de façon permanente un projet, mais vous devez d'abord enlever les références au projet des solutions [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis utiliser l'Explorateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows pour supprimer définitivement du système de stockage les fichiers associés.  
  
#### <a name="to-delete-a-project"></a>Pour supprimer un projet  
  
1.  Dans l'Explorateur de solutions, enlevez le projet que vous souhaitez supprimer de la solution.  
  
2.  Dans l'Explorateur Windows, recherchez et sélectionnez les fichiers associés au projet ou à l'élément que vous souhaitez supprimer.  
  
3.  Dans le menu **Fichier** , cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de solutions](solution-explorer.md)   
 [Ajouter de nouveaux éléments à un projet](add-new-items-to-a-project.md)   
 [Ajouter des éléments existants à un projet](add-existing-items-to-a-project.md)  
  
  
