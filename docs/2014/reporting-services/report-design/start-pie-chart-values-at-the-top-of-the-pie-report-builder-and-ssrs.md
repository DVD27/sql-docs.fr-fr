---
title: Démarrer des valeurs de graphique à secteurs en haut du graphique à secteurs (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2610534159be781e2719034b41276be5f0d7d473
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104817"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>Démarrer des valeurs de graphique à secteurs en haut du graphique à secteurs (Générateur de rapports et SSRS)
  Par défaut dans les graphiques à secteurs, la première valeur du dataset démarre à 90 degrés à partir du haut du graphique à secteurs. Vous souhaiterez peut-être que la première valeur démarre en haut.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>Pour démarrer le graphique à secteurs en haut  
  
1.  Cliquez sur les secteurs.  
  
2.  Si le volet **Propriétés** n'est pas ouvert, cliquez sur **Propriétés** sous l'onglet **Affichage**.  
  
3.  Dans le volet **Propriétés** , sous **attributs personnalisés**, changez **piestartangle définie sur** de **0** à **270**.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 La première valeur démarre à présent en haut du graphique à secteurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Graphiques à secteurs (Générateur de rapports et SSRS)](charts-report-builder-and-ssrs.md)  
  
  
