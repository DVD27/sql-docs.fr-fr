---
title: Ouvrir un modèle
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dd59b435c1c0fbd3461333305824aca61c68d296
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75245690"
---
# <a name="open-a-template"></a>Ouvrir un modèle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Vous pouvez ouvrir un modèle dans l'Explorateur de modèles.  
  
## <a name="to-open-a-template-from-template-explorer"></a>Pour ouvrir un modèle dans l'Explorateur de modèles  
Vous pouvez ouvrir des modèles dans l'Explorateur de modèles.  
  
1.  Pour ouvrir l’Explorateur de modèles, dans le menu **Affichage** , cliquez sur **Explorateur de modèles**.  
  
2.  Dans la liste des catégories de modèles, développez la catégorie contenant le modèle que vous souhaitez ouvrir.  
  
3.  Il existe trois manières d'ouvrir le modèle :  
  
    1.  Double-cliquez sur le modèle pour l'ouvrir dans une fenêtre d'éditeur de code.  
  
    2.  Cliquez avec le bouton droit sur le modèle et sélectionnez **Ouvrir** pour l’ouvrir dans une fenêtre d’éditeur de code.  
  
    3.  Faites glisser le modèle dans une fenêtre d'éditeur de code pour ajouter le code du modèle au contenu de la fenêtre de l'éditeur.  
  
Une fois que le modèle est ouvert, utilisez la boîte de dialogue **Remplacer les paramètres de modèle** pour remplacer les paramètres du modèle par vos valeurs.  
  
Si l'ouverture d'un modèle lance une nouvelle fenêtre d'éditeur, la fenêtre s'ouvre avec les informations d'identification de la connexion active actuelle. Par exemple, si le focus se trouve sur une instance du [!INCLUDE[ssDE](../../includes/ssde_md.md)] dans l'Explorateur d'objets lorsque vous ouvrez le modèle CREATE DATABASE, une nouvelle fenêtre d'éditeur est ouverte à l'aide d'une connexion à cette instance. S'il n'y a aucune connexion active, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] présente une boîte de dialogue de connexion.  
  
## <a name="see-also"></a>Voir aussi  
[l’Explorateur de modèles](../../ssms/template/template-explorer.md)  
[Remplacer les paramètres de modèle](../../ssms/template/replace-template-parameters.md)  
  
