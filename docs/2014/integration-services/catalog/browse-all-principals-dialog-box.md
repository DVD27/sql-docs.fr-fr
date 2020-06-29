---
title: Boîte de dialogue Parcourir tous les principaux | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: feff922ac12e46a8b78f30ca46bc02a4fd23b4f6
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439116"
---
# <a name="browse-all-principals-dialog-box"></a>Parcourir tous les principaux, boîte de dialogue
  Utilisez la boîte de dialogue **Parcourir tous les principaux** pour sélectionner un principal de base de données et modifier les autorisations du principal sur le projet sélectionné ou sur tous les projets contenus dans un dossier sélectionné.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir la boîte de dialogue Parcourir tous les principaux](#open_dialog)  
  
-   [Configurer les options](#options)  
  
##  <a name="open-the-browse-all-principals-dialog-box"></a><a name="open_dialog"></a> Ouvrir la boîte de dialogue Parcourir tous les principaux  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Vous devez vous connecter à l’instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge le catalogue SSISDB.  
  
2.  Dans l'Explorateur d'objets, développez l'arborescence pour afficher le nœud **Integration Services Catalogues** .  
  
3.  Développez le nœud **SSISDB** .  
  
4.  Pour changer les autorisations du principal sur tous les projets contenus dans un dossier sélectionné, cliquez avec le bouton droit sur le dossier, puis cliquez sur **Propriétés**.  
  
     Pour changer les autorisations du principal sur un projet sélectionné, développez le dossier qui contient le projet, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.  
  
5.  Sélectionnez la page **Autorisations** , puis cliquez sur **Parcourir**.  
  
##  <a name="configure-the-options"></a><a name="options"></a> Configurer les options  
 Cette page affiche les principaux de la vue catalogue, sys.database_principals, de la base de données SSISDB.  
  
 La sélection de principaux les ajoute à la liste **Connexions ou rôles** dans la page **Autorisations** de la boîte de dialogue parent lorsque vous cliquez sur **OK** et fermez la boîte de dialogue **Parcourir tous les principaux** . Après avoir ajouté des principaux à la liste **Connexions ou rôles** , vous pouvez modifier leurs autorisations sur le projet sélectionné.  
  
 **Sélection de colonne**  
 Sélectionnez cette option pour ajouter le principal à la liste **Connexions ou rôles** dans la page **Autorisations** de la boîte de dialogue parent.  
  
 **Colonne Icône**  
 Icône qui correspond au **Type** du principal.  
  
 **Nom**  
 Nom du principal.  
  
 **Type**  
 Type du principal. Les types courants sont :  
  
-   Utilisateur SQL  
  
-   Utilisateur Windows  
  
-   Rôle de base de données  
  
  
