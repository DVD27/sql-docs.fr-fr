---
title: Imprimer des rapports | Microsoft Docs
description: Vous pouvez afficher et imprimer un rapport à partir du portail web ou d’une application que vous utilisez pour l’afficher. L’ordinateur client effectue le traitement de l’impression à la demande.
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: 4bad1b6e-7d94-4b17-9502-ccd3dce0fdd9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f81be70bf4de9d9f15a3c35d3a3dc4b5c81f2609
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "80290880"
---
# <a name="print-reports---reporting-services-ssrs"></a>Imprimer des rapports - Reporting Services (SSRS)
  Après avoir enregistré un rapport sur un serveur de rapports, vous pouvez l’afficher et l’imprimer à partir du portail web ou de toute application permettant d’afficher un rapport exporté. Avant d'enregistrer un rapport, vous pouvez l'imprimer après avoir affiché son aperçu.  
  
 Toutes les tâches relatives à l'impression sont effectuées à la demande et sur l'ordinateur client. Aucune fonctionnalité d'impression côté serveur ne vous permet d'acheminer un travail d'impression directement depuis un serveur de rapports jusqu'à une imprimante connectée au serveur Web. Les imprimantes et les options d’impression sont sélectionnées par chaque utilisateur de rapport via une boîte de dialogue **Imprimer** standard.  
  
 Les créateurs de rapports qui conçoivent des rapports destinés spécifiquement à être imprimés peuvent utiliser des sauts de page, des en-têtes et des pieds de page, des expressions, ainsi que des images d'arrière-plan pour créer une structure d'impression. À titre d'exemple, les termes et conditions qui doivent figurer au dos de chaque rapport ainsi que les éléments de texte ou graphiques qui constituent un en-tête sont des éléments de conception de rapport destinés spécifiquement à l'impression.  
  
 En raison de la façon dont la pagination est implémentée pour les différents formats de rendu, vous risquez de ne pas obtenir un résultat optimal identique à l’impression selon les rapports et les formats de rendu. La liste suivante fournit des exemples :  
  
1.  Les pages des rapports sont conçues pour contenir des quantités variables de données. Par exemple, les rapports qui comprennent une matrice peuvent entraîner l'agrandissement d'une page à la fois horizontalement et verticalement, si un utilisateur active de manière interactive les lignes et les colonnes. À l'inverse, un utilisateur qui ne développe pas une matrice obtiendra des résultats différents lors de l'impression.  
  
2.  Vous ne pouvez pas associer des pages en mode paysage et en mode portrait dans un même rapport ; vous ne pouvez pas non plus de créer une structure d'impression qui remplace ou complète la structure d'un rapport rendu dans un navigateur ou une autre application.  
  
3.  Pour la plupart des rapports exportés, les rapports imprimés incluent tout ce qui est visible sur les rapports, tel que l'utilisateur peut les voir sur un moniteur d'ordinateur. L'espace blanc de l'aire de conception du rapport est conservé. Pour ajouter ou supprimer des pages vierges supplémentaires horizontalement, modifiez la largeur de page de rapport.  
  
> [!NOTE]  
>  L'impression des rapports HTML ne montre que le contenu de leur première page, si vous utilisez la commande Imprimer du navigateur. Vous pouvez obtenir de meilleurs résultats si vous imprimez les rapports HTML à l'aide de la fonctionnalité d'impression côté client de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez [Imprimer des rapports à partir d’un navigateur à l’aide du contrôle d’impression &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a>Dans cette section  
 [Imprimer des rapports à partir d’un navigateur à l’aide du contrôle d’impression &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)  
 Décrit l’utilisation de l’impression côté client pour imprimer des rapports à partir du portail web.  
  
 [Imprimer des rapports à partir d’autres applications &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/print-reports-from-other-applications-report-builder-and-ssrs.md)  
 Explique comment imprimer des rapports exportés vers une autre application.  
  
 [Imprimer un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/print-a-report-report-builder-and-ssrs.md)  
 Explique pas à pas comment imprimer un rapport, contrôler les marges sur une page et spécifier le format du papier des rapports qui seront affichés par les convertisseurs de saut de page manuel : PDF, image ou impression.  
  
## <a name="see-also"></a>Voir aussi  
 [Exporter des rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)   
 [Images &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)  
  
  
