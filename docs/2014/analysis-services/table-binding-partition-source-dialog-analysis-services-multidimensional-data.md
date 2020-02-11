---
title: Détails de la liaison de table (boîte de dialogue source de partition) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f8ea36c8c3d49d4903379ed4450548fc760937a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067871"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Détails de la liaison de table (boîte de dialogue Source de partition) (Analysis Services - Données multidimensionnelles)
  Utilisez l'option **Liaison de table** de la boîte de dialogue **Source de la partition** pour définir la table de faits qui fournit les données de la partition. Vous pouvez afficher ce volet en sélectionnant **Liaison de table** dans l'option **Type de liaison** de la boîte de dialogue **Source de la partition** .  
  
## <a name="options"></a>Options  
 **Groupe de mesures**  
 Affiche le groupe de mesures de la partition.  
  
 **Look in**  
 Permet d'indiquer la source de données ou la vue de source de données contenant les tables source destinées à cette partition. La vue de source de vue de données utilisée par le groupe de mesures sélectionné est sélectionnée par défaut.  
  
 **Filtrer les tables**  
 Permet d’entrer la chaîne utilisée pour restreindre les tables affichées dans **Tables disponibles**d’après leur nom.  
  
 **Rechercher des tables**  
 Permet d’actualiser la liste des tables répertoriées dans **Tables disponibles**, et d’affiner la liste d’après les critères d’une chaîne indiquée dans **Filtrer les tables**, le cas échéant.  
  
 **Tables disponibles**  
 Cliquez pour sélectionner la table à utiliser comme table source pour la partition.  
  
 Si aucun filtre n'est défini dans **Filtrer les tables**, toutes les tables dans la source de données ou la vue de source de données définie dans **Rechercher dans** , qui sont similaires, en terme de structure, à la table des faits utilisée par le groupe de mesures défini dans **Groupe de mesures** , sont affichées.  
  
 Si un filtre est défini dans **Filtrer les tables**, la liste est encore limitée en comparant le filtre aux noms de tables qui répondent aux critères ci-dessous. Ainsi, seules les tables contenant la chaîne spécifiée dans **Filtrer les tables** sont affichées.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue source de partition &#40;Analysis Services-données multidimensionnelles&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
