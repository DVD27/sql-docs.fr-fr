---
title: Modifier le contrôle de code source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- IDD_SCC_CONNECTION_DIALOG
helpviewer_keywords:
- Change Source Control dialog box
ms.assetid: e6a5d83c-5809-4c56-907a-73d0c7ccdd7a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 939e3befd0cbec87dbba7046761637c4b7655e22
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62812743"
---
# <a name="change-source-control"></a>Modifier le contrôle de code source
  Cette boîte de dialogue permet de créer et de gérer les connexions et liaisons entre une solution ou un projet enregistré en local et un dossier de base de données de contrôle de code source.  
  
## <a name="dialog-box-access"></a>Accès à la boîte de dialogue  
 Dans l'Explorateur de solutions de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], sélectionnez un élément. Dans le menu **Fichier** , cliquez sur **Contrôle de code source**, puis sur **Modifier le contrôle de code source**.  
  
> [!NOTE]  
>  Cette boîte de dialogue est également disponible en cliquant avec le bouton droit sur l'élément dans l'Explorateur de solutions.  
  
## <a name="options"></a>Options  
 **Établis**  
 Associe les éléments sélectionnés à un emplacement de serveur de contrôle de code source spécifié. Par exemple, vous pouvez utiliser cette option pour effectuer une liaison vers le dernier dossier et la dernière base de données connus du serveur de contrôle de code source. Si aucun dossier ou base de données récent n'est trouvé, vous devez en spécifier un ou une autre.  
  
 **Parcourir**  
 Permet d'accéder à un autre emplacement de serveur de contrôle de code source pour l'élément sélectionné.  
  
 **Colonnes**  
 Identifie les colonnes à afficher et l'ordre dans lequel elles s'affichent.  
  
 **Connexion**  
 Crée une connexion entre les éléments sélectionnés et le serveur de contrôle de code source.  
  
 **Connecté**  
 Affiche l'état de connexion d'une solution ou d'un projet sélectionné.  
  
 **Connect**  
 Déconnecte la copie locale d'une solution ou d'un projet, sur votre ordinateur personnel, de sa copie principale dans la base de données. Utilisez cette commande avant de déconnecter votre ordinateur du serveur de contrôle de code source (par exemple, en mode hors connexion sur votre ordinateur portable).  
  
 **OK**  
 Enregistre les changements apportés dans la boîte de dialogue.  
  
 **Fournisseur**  
 Affiche le nom de votre plug-in de contrôle de code source.  
  
 **Actualisation**  
 Actualise les informations de connexion relatives à tous les projets répertoriés dans cette boîte de dialogue.  
  
 **Liaison du serveur**  
 Indique la liaison entre l'élément et un serveur de contrôle de code source.  
  
 **Nom du serveur**  
 Affiche le nom du serveur de contrôle de code source auquel la solution ou le projet correspondant est lié.  
  
 **Solution/Projet**  
 Affiche le nom de chaque solution et projet dans la sélection en cours.  
  
 **Trier**  
 Trie les colonnes affichées.  
  
 **État**  
 Identifie l'état de liaison et de connexion d'un élément. Les options possibles sont les suivantes :  
  
|**Option**|**Description**|  
|----------------|---------------------|  
|Valide|L'élément est correctement lié et connecté au dossier de serveur auquel il appartient.|  
|Non valide|L'élément n'est pas correctement lié au dossier de serveur auquel il appartient ou il en est déconnecté. Sélectionnez la commande **Ajouter au contrôle de code source** au lieu de la commande **Lier** pour cet élément.|  
|Unknown|L'état de l'élément sous contrôle de code source n'a pas encore été déterminé.|  
|Pas contrôlé|L'élément n'est pas placé sous contrôle de code source.|  
  
 **Dissoci**  
 Affiche la boîte de dialogue **Contrôle de code source** pour vous permettre de supprimer des éléments du contrôle de code source et de les dissocier de façon permanente de leurs dossiers actuels.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de code source de l'Explorateur de solutions](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
