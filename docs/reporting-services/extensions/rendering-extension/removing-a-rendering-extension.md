---
title: Suppression d’une extension de rendu | Microsoft Docs
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0ee3563074e2379061006b72f55dab99f80094cd
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "63193454"
---
# <a name="removing-a-rendering-extension"></a>Suppression d'une extension de rendu
  Pour supprimer une extension de rendu [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], supprimez simplement l’élément **Extension** pour votre extension de rendu du fichier rsreportserver.config, situé dans le dossier **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<nom_instance>\Reporting Services\ReportServer**. Si vous avez créé des entrées pour un Concepteur de rapports et un serveur de rapports, supprimez l’élément **Extension** du [fichier de configuration RSReportDesigner](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md) également. Une fois les informations de configuration supprimées, l'extension de rendu n'est plus accessible au composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Implémentation d’une extension de rendu](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Vue d’ensemble des extensions de rendu](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Mise en œuvre de l’interface IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Considérations sur la sécurité pour les extensions](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Déploiement d'une extension de rendu](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
