---
title: Utiliser la fenêtre Propriétés dans Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 831d4bd07619ee7542ab520e076ff7a5580d13e6
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68252927"
---
# <a name="use-the-properties-window-in-management-studio"></a>Utiliser la fenêtre Propriétés dans Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La fenêtre Propriétés décrit l'état d'un élément dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], tel qu'une connexion ou un opérateur Showplan, et fournit des informations sur les objets de base de données tels que les tables, les vues et les concepteurs.  
  
 Vous pouvez également utiliser la fenêtre Propriétés pour afficher les propriétés de la connexion active. La plupart des propriétés sont en lecture seule dans la fenêtre Propriétés. Toutefois, elles peuvent être modifiées à d'autres emplacements dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Par exemple, la propriété Database d'une requête est en lecture seule dans la fenêtre Propriétés mais elle peut être modifiée dans la barre d'outils.  
  
### <a name="to-view-properties-using-the-properties-window"></a>Pour afficher des propriétés dans la fenêtre Propriétés  
  
1.  Si la fenêtre Propriétés n'est pas visible, cliquez sur **Fenêtre Propriétés** dans le menu **Affichage** ou appuyez sur F4.  
  
2.  Activez l'objet dont vous souhaitez afficher les propriétés.  
  
3.  Recherchez une propriété spécifique dans la fenêtre Propriétés.  
  
### <a name="to-view-connection-properties-of-a-query-window"></a>Pour afficher les propriétés de connexion d'une fenêtre de requête  
  
1.  Si la fenêtre Propriétés n'est pas visible, cliquez sur **Fenêtre Propriétés** dans le menu **Affichage** ou appuyez sur F4.  
  
2.  Dans la fenêtre Propriétés, vous pouvez voir toutes les propriétés de connexion.  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a>Pour afficher les propriétés d'un opérateur Showplan  
  
1.  Dans le menu **Requête** , cliquez sur **Inclure le plan d'exécution réel**.  
  
2.  Dans l'Éditeur de requête SQL, tapez une requête, puis exécutez-la.  
  
3.  Si la fenêtre Propriétés n'est pas visible, cliquez sur **Fenêtre Propriétés** dans le menu **Affichage** ou appuyez sur F4.  
  
4.  Sous l'onglet **Plan d'exécution** de l'Éditeur de requête SQL, cliquez sur les icônes des opérateurs pour afficher des informations sur ces derniers dans la fenêtre Propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre Propriétés &#40;Management Studio&#41;](https://msdn.microsoft.com/library/6a9a1389-df8d-4cfc-928b-eccbf884a22d)  
  
  
