---
title: Ajouter une référence d’assembly à un rapport (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23dda0c65589e55849f906c621e42ce70f0d7ab5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106759"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>Ajouter une référence d'assembly à un rapport (SSRS)
  Quand vous incorporez du code personnalisé qui contient [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] des références à des classes <xref:System.Math> qui <xref:System.Convert>ne sont pas dans ou, vous devez fournir une référence d’assembly au rapport afin que le processeur de rapports puisse résoudre les noms. Pour plus d’informations, consultez [Ajouter du code à un rapport &#40;SSRS&#41;](add-code-to-a-report-ssrs.md).  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>Pour ajouter une référence d'assembly à un rapport  
  
1.  En mode **Conception** , cliquez avec le bouton droit sur l’aire de conception à l’extérieur de la bordure du rapport et cliquez sur **Propriétés du rapport**.  
  
2.  Cliquez sur **Références**.  
  
3.  Dans **Ajouter ou supprimer des assemblys**, cliquez sur **Ajouter** , puis sur le bouton de sélection pour accéder à l’assembly.  
  
4.  Dans **Ajouter ou supprimer des classes**, cliquez sur **Ajouter** , puis tapez le nom de la classe et fournissez le nom d’une instance à utiliser dans le rapport.  
  
    > [!NOTE]  
    >  Spécifiez une classe et un nom d'instance uniquement pour les membres basés sur une instance. Ne spécifiez pas de membres statiques dans la liste **Classes** . Pour plus d’informations, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’assemblys personnalisés avec des rapports](../custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Boîte de dialogue Propriétés du rapport, Références](../report-properties-dialog-box-references.md)  
  
  
