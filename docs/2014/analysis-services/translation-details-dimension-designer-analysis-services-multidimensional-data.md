---
title: Détails des traductions (onglet traductions, concepteur de dimensions) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.translations.translationpane.tranlationdetails.f1
ms.assetid: 0aa61df3-f2b0-4703-a63b-124da672dcc3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f8debb50a798ba46457942e0e79a9d45ab392c1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66065853"
---
# <a name="translation-details-translations-tab-dimension-designer-analysis-services---multidimensional-data"></a>Détails des traductions (onglet Traductions, Concepteur de dimensions) (Analysis Services - données multidimensionnelles)
  Le volet **Détails des traductions** de l’onglet **Traductions** du Concepteur de dimensions permet de définir et de gérer les traductions pour la dimension actuellement sélectionnée.  
  
 **Pour afficher le volet Détails des traductions**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis ouvrez la dimension souhaitée.  
  
2.  Cliquez sur l'onglet **Traductions** .  
  
## <a name="options"></a>Options  
 **Langue par défaut**  
 Définit les noms des objets de dimension dans la langue par défaut.  
  
 **Type d’objet**  
 Permet d'afficher la propriété à traduire. Seuls les objets et les propriétés, pour lesquels vous précisez des valeurs, peuvent être traduits. Les propriétés pouvant être traduites sont les suivantes :  
  
-   Dimension  
  
     Propriétés `Caption` et `AttributeAllMember`  
  
-   Attribut  
  
     Propriétés `Caption`, `AttributeHierarchyDisplayFolder` et `NamingTemplate`  
  
    > [!NOTE]  
    >  La propriété `NamingTemplate` n'est disponible que pour les attributs parents.  
  
-   Hierarchy  
  
     Propriétés `Caption` et `AllMemberName`  
  
-   Level  
  
     `Caption`propriété  
  
 **\<>de langue**  
 Tapez ou sélectionnez la valeur de propriété de l'objet de dimension dans la langue sélectionnée. Des boîtes de dialogue supplémentaires s’ouvrent quand vous cliquez sur le bouton de sélection (**...**), en fonction de la propriété en cours de modification :  
  
-   `NamingTemplate`propriété  
  
     Affiche la [Boîte de dialogue Modèle de nom de niveau &#40;Analysis Services - Données multidimensionnelles&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md).  
  
-   Propriété `Caption` (pour les attributs)  
  
     Affiche la [Boîte de dialogue Traduction de données d’attribut &#40;Analysis Services - Données multidimensionnelles&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="shortcut-menu"></a>Menu contextuel  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche quand vous cliquez avec le bouton droit sur une traduction dans le volet **Détails des traductions** :  
  
 **Nouvelle traduction**  
 Entraîne l’ouverture de la boîte de dialogue **Sélectionnez une langue** où vous pouvez créer une traduction. La traduction s’affiche dans une nouvelle colonne de la grille **Détails des traductions** .  
  
 **Supprimer la traduction**  
 Permet de supprimer la traduction sélectionnée.  
  
> [!NOTE]  
>  Cette option est uniquement activée si vous avez cliqué avec le bouton droit sur une cellule pour supprimer la traduction.  
  
 **Nouvelle colonne de légende**  
 Sélectionnez cette option pour afficher la boîte de dialogue **Traduction de données d’attribut** et définir une nouvelle colonne de légende quand vous modifiez un attribut dans la grille **Détails des traductions** . Pour activer cette option, une cellule d'une colonne de traduction doit être sélectionnée dans la grille des **détails des traductions** .  
  
> [!NOTE]  
>  Cette option est uniquement activée si vous avez cliqué avec le bouton droit sur une cellule pour supprimer la colonne de traduction d'un attribut.  
  
 **Modifier la colonne de légende**  
 Sélectionnez cette option pour afficher la boîte de dialogue **Traduction de données d’attribut** et modifier une colonne de légende existante quand vous modifiez un attribut dans la grille **Détails des traductions** .  
  
> [!NOTE]  
>  Pour que cette option soit activée, une cellule d’une colonne de traduction qui contient une colonne de légende doit être sélectionnée dans la grille des **détails des traductions** .  
  
 **Supprimer la colonne de légende**  
 Sélectionnez cette option pour supprimer la colonne de légende pour l’attribut sélectionné dans la grille **Détails des traductions** .  
  
> [!NOTE]  
>  Cette option est uniquement activée si vous avez cliqué avec le bouton droit sur une cellule dans une colonne de traduction qui contient une colonne de légende pour un attribut.  
  
 **Afficher tous les attributs**  
 Sélectionnez cette option pour afficher ou masquer tous les attributs définis pour la dimension sélectionnée, notamment les attributs dont les hiérarchies sont désactivées.  
  
## <a name="see-also"></a>Voir aussi  
 [Traductions &#40;concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
