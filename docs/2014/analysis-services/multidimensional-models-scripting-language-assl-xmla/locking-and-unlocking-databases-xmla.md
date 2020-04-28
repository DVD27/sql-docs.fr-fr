---
title: Verrouillage et déverrouillage des bases de données (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 290f1e5fe7efb876ab6c24004c7465cf109de0d0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62702233"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Verrouillage et déverrouillage de bases de données (XMLA)
  Vous pouvez verrouiller et déverrouiller des bases de données à l’aide, respectivement, des commandes de [verrouillage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) et de [déverrouillage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) dans XML for Analysis (XMLA). En règle générale, les autres commandes XMLA verrouillent et déverrouillent automatiquement les objets, selon le cas, pour faire aboutir la commande pendant l'exécution. Vous pouvez verrouiller ou déverrouiller explicitement une base de données pour exécuter plusieurs commandes au sein d’une même transaction, par exemple une commande [batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) , tout en empêchant d’autres applications de valider une transaction d’écriture dans la base de données.  
  
## <a name="locking-databases"></a>Verrouillage de bases de données  
 La commande `Lock` verrouille un objet, pour un usage partagé ou exclusif, dans le contexte de la transaction actuellement active. Un verrou sur un objet empêche la validation des transactions aussi longtemps que le verrou n'est pas supprimé. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge deux types de verrous, les verrous partagés et les verrous exclusifs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour plus d’informations sur les types de verrous pris en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez élément de [Mode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] autorise uniquement le verrouillage des bases de données. La commande [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) doit contenir une référence d'objet à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Si l'élément `Object` n'est pas spécifié ou si cet élément `Object` fait référence à un objet autre qu'une base de données, une erreur survient.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande `Lock` de manière explicite.  
  
 D'autres commandes permettent d'émettre une commande `Lock` dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de manière implicite. Toutes les opérations permettant de lire les données ou les métadonnées d'une base de données (par exemple, n'importe quelle méthode [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) ou une méthode [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) exécutant une commande [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) ) émettent implicitement un verrou partagé dans la base de données. Toute transaction qui valide les modifications apportées aux données ou aux métadonnées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d’un objet dans une `Execute` base de données, telle qu’une méthode exécutant une commande [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) , émet implicitement un verrou exclusif sur la base de données.  
  
## <a name="unlocking-objects"></a>Déverrouillage d'objets  
 La commande `Unlock` supprime un verrou établi dans le contexte de la transaction actuellement active.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de base de données ou les administrateurs `Unlock` de serveur peuvent émettre explicitement une commande.  
  
 Tous les verrous sont conservés dans le contexte de la transaction en cours. Lors de la validation ou de la restauration de la transaction en cours, tous les verrous définis dans celle-ci sont libérés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Lock &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Déverrouiller l’élément &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
