---
title: Créer et gérer des rôles (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.rolemanager.f1
- sql12.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 10e5e26142cd1819e4f2c5f884af9c2f2af10812
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67284902"
---
# <a name="create-and-manage-roles-ssas-tabular"></a>Créer et gérer des rôles (SSAS Tabulaire)
  Les rôles, dans les modèles tabulaires, définissent des autorisations de membre pour un modèle. Les rôles sont définis pour un projet de modèle à l'aide de la boîte de dialogue Gestionnaire de rôles de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Lorsqu'un modèle est déployé, les administrateurs de base de données peuvent gérer les rôles à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Les tâches de cette rubrique expliquent comment créer et gérer les rôles pendant la création du modèle à l'aide de la boîte de dialogue Gestionnaire de rôles de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations sur la gestion des rôles dans une base de données model déployée, consultez [Rôles de modèles tabulaires &#40;SSAS Tabulaire&#41;](roles-ssas-tabular.md).  
  
## <a name="tasks"></a>Tâches  
 Pour créer, modifier, copier et supprimer des rôles, utilisez la boîte de dialogue **Gestionnaire de rôles** . Pour consulter la boîte de dialogue **Gestionnaire de rôles** , dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Gestionnaire de rôles**.  
  
###  <a name="bkmk_new_role"></a>Pour créer un nouveau rôle  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Gestionnaire de rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
     Un nouveau rôle en surbrillance est ajouté à la liste de rôles.  
  
3.  Dans la liste **Rôles** , dans le champ **Nom** , tapez un nom pour le rôle.  
  
     Par défaut, le nom du rôle par défaut est numéroté de manière incrémentielle pour chaque nouveau rôle. Il est recommandé de taper un nom qui identifie sans ambiguïté le type de membre, par exemple, Directeurs financiers ou Responsables des ressources humaines.  
  
4.  Dans le champ **Autorisations** , cliquez sur la flèche Bas, puis sélectionnez un des types d'autorisation suivants :  
  
    |Autorisation|Description|  
    |----------------|-----------------|  
    |**Aucun**|Les membres ne peuvent pas apporter de modifications au schéma de modèle et ne peuvent pas interroger les données.|  
    |**Lire**|Les membres sont autorisés à interroger des données (selon les filtres de lignes) mais ne peuvent pas apporter de modifications au schéma de modèle.|  
    |**Lire et traiter**|Les membres sont autorisés à interroger des données (selon les filtres au niveau de la ligne) et à exécuter toutes les opérations Traiter et Traiter tout, mais ils ne peuvent pas apporter de modifications au schéma de modèle.|  
    |**Procédure**|Les membres peuvent exécuter des processus et traiter toutes les opérations. Ils ne peuvent pas modifier le schéma de modèle et ne peuvent pas interroger les données.|  
    |**Il**|Les membres peuvent apporter des modifications au schéma de modèle et peuvent interroger toutes les données.|  
  
5.  Pour entrer une description du rôle, cliquez sur le champ **Description** et tapez une description.  
  
6.  Si le rôle que vous créez dispose d'autorisations de lecture ou de lecture et traitement, vous pouvez ajouter des filtres de lignes à l'aide d'une formule DAX. Pour ajouter des filtres de lignes, cliquez sur l'onglet **Filtres de lignes** , sélectionnez une table, cliquez sur le champ **Filtre DAX** , puis tapez une formule DAX.  
  
7.  Pour ajouter des membres au rôle, cliquez sur l'onglet **Membres** , puis sur **Ajouter**.  
  
    > [!NOTE]  
    >  Les membres du rôle peuvent également être ajoutés à un modèle déployé à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Gérer les rôles à l’aide de SSMS &#40;SSAS Tabulaire&#41;](manage-roles-by-using-ssms-ssas-tabular.md).  
  
8.  Dans la boîte de dialogue **Sélectionner les utilisateurs ou les groupes** , entrez des objets utilisateur ou de groupe Windows comme membres.  
  
9. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles &#40;&#41;tabulaire SSAS](roles-ssas-tabular.md)   
 [Perspectives &#40;&#41;tabulaire SSAS](perspectives-ssas-tabular.md)   
 [Analyser dans Excel &#40;la&#41;tabulaire SSAS](analyze-in-excel-ssas-tabular.md)   
 [Fonction USERNAME &#40;&#41;DAX](/dax/username-function-dax)   
 [Fonction CUSTOMDATA &#40;&#41;DAX](/dax/customdata-function-dax)  
  
  
