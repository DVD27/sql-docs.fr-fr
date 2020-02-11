---
title: Créer et gérer des partitions de modèles tabulaires (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72c5b69aee10d8ac1342b3f037d76ab6ef5fc36c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067402"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a>Créer et gérer des partitions de modèles tabulaires (SSAS Tabulaire)
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les partitions définies pour un modèle au cours de la création de modèles sont dupliquées dans un modèle déployé. Une fois le déploiement terminé, vous pouvez gérer ces partitions à l'aide de la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou à l'aide d'un script. Les tâches fournies dans cette rubrique décrivent comment créer et gérer des partitions pour un modèle déployé.  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour créer une nouvelle partition](#bkmk_create_new)  
  
-   [Pour copier une partition](#bkmk_copy)  
  
-   [Pour fusionner deux ou plusieurs partitions](#bkmk_merge)  
  
-   [Pour supprimer une partition](#bkmk_delete)  
  
## <a name="tasks"></a>Tâches  
 Pour créer et gérer des partitions d'une base de données de modèle tabulaire déployée, vous utiliserez la boîte de dialogue **Partitions** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour afficher la boîte de dialogue **Partitions** , dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur une table, puis cliquez sur **Partitions**.  
  
###  <a name="bkmk_create_new"></a>Pour créer une nouvelle partition  
  
1.  Dans la boîte de dialogue **Partitions** , cliquez sur le bouton **Nouveau** .  
  
2.  Dans **Nom de la partition**, tapez un nom pour la partition. Par défaut, le nom de la partition par défaut est numéroté de manière incrémentielle pour chaque nouvelle partition.  
  
3.  Dans **Instruction SQL**, tapez ou collez une instruction de requête SQL qui définit les colonnes et toutes les clauses que vous souhaitez inclure à la partition dans la fenêtre de requête.  
  
4.  Pour valider l'instruction, cliquez sur **Vérifier la syntaxe**.  
  
###  <a name="bkmk_copy"></a>Pour copier une partition  
  
1.  Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , sélectionnez la partition à copier, puis cliquez sur le bouton **Copier** .  
  
2.  Dans **Nom de la partition**, tapez un nouveau nom pour la partition.  
  
3.  Dans **Instruction SQL**, modifiez l'instruction de requête SQL.  
  
###  <a name="bkmk_merge"></a>Pour fusionner deux ou plusieurs partitions  
  
-   Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , utilisez Ctrl+clic pour sélectionner les partitions à fusionner, puis cliquez sur le bouton **Fusionner** .  
  
> [!IMPORTANT]  
>  Le fait de fusionner les partitions ne met pas à jour les métadonnées des partitions. Les administrateurs doivent modifier l'instruction SQL pour la partition obtenue afin de veiller à ce que les opérations de traitement traitent toutes les données dans la partition fusionnée.  
  
###  <a name="bkmk_delete"></a>Pour supprimer une partition  
  
-   Dans la boîte de dialogue **Partitions** , dans la liste **Partitions** , sélectionnez la partition à supprimer, puis cliquez sur le bouton **Supprimer** .  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions de modèles tabulaires &#40;&#41;SSAS tabulaire](partitions-ssas-tabular.md)   
 [Traiter les partitions de modèles tabulaires &#40;les&#41;tabulaires SSAS](process-tabular-model-partitions-ssas-tabular.md)  
  
  
