---
title: Ajouter une bordure à un rapport (Générateur de rapports) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7790d44cc4160d7f61562cf470da43bb49a82cf2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77080784"
---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a>Ajouter une bordure à un rapport (Générateur de rapports et SSRS)
  Vous pouvez entourer un rapport paginé [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] d’une bordure en plaçant celle-ci dans les en-têtes, les pieds de page et le corps du rapport, sans ajouter de lignes ou de rectangles.    
    
 Si vous ajoutez une bordure de rapport apparaissant dans l'en-tête et le pied de page, ne supprimez pas l'en-tête et le pied de page des première et dernière pages du rapport. Sans cela, la bordure pourra être coupée partiellement, en haut et en bas des première et dernières pages du rapport. Pour plus d’informations, consultez [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md).    
    
## <a name="to-add-a-border-to-a-report"></a>Pour ajouter une bordure à un rapport    
    
1.  Cliquez avec le bouton droit dans l’en-tête en dehors de tout élément de l’en-tête, puis cliquez sur **Propriétés d’en-tête**. Sous l'onglet **Bordure** , ajoutez une bordure gauche, supérieure et droite avec le style souhaité.    
    
    > [!NOTE]    
    >  Si votre rapport n’a pas d’en-têtes, vous pouvez placer des bordures uniquement autour du corps du rapport ; sinon, vous pouvez ajouter des en-têtes à partir de l’onglet **Insérer** .    
    
2.  Cliquez avec le bouton droit dans le corps en dehors de tout élément de l’aire de conception, puis cliquez sur **Propriétés du corps**. Sous l'onglet **Bordure** , ajoutez une bordure gauche et droite avec le style souhaité.    
    
3.  Cliquez avec le bouton droit dans le pied de page en dehors de tout élément du pied de page, puis cliquez sur **Propriétés du pied de page**. Sous l'onglet **Bordure** , ajoutez une bordure gauche, inférieure et droite avec le style souhaité.    
    
## <a name="see-also"></a>Voir aussi    
 [Rectangles et lignes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md)    
    
  
