---
title: Éditeur de source SAP BW (page Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 80a3d1d0fa667821616909a327a946a4116d06de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62901042"
---
# <a name="sap-bw-source-editor-advanced-page"></a>Éditeur de source SAP BW (page Avancé)
  Utilisez la page **Avancé** de **l’Éditeur de source SAP BW** pour spécifier la règle de conversion de chaînes et le délai d’attente, et également pour réinitialiser l’état d’un ID de demande particulier.  
  
 Pour en savoir plus sur le composant source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [SAP BW Source](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
 **Pour ouvrir la page Gestionnaire de connexions**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source SAP BW.  
  
3.  Dans **l’Éditeur de source SAP BW**, cliquez sur **Avancé** pour ouvrir la page **Avancé** de l’éditeur.  
  
## <a name="options"></a>Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer la source, adressez-vous à votre administrateur SAP.  
  
 **Conversion de chaîne**  
 Spécifiez la règle à appliquer pour la conversion de chaîne.  
  
|Option|Description|  
|------------|-----------------|  
|**Conversion de chaîne automatique**|Convertissez toutes les chaînes en `nvarchar` lorsque le système SAP Netweaver BW est un système Unicode. Sinon, convertissez toutes les chaînes en `varchar`.|  
|**Convertir les chaînes en varchar**|Convertissez toutes les chaînes en `varchar`.|  
|**Convertir les chaînes en nvarchar**|Convertissez toutes les chaînes en `nvarchar`.|  
  
 **Délai d'attente (secondes)**  
 Spécifiez le nombre maximal de secondes pendant lesquelles la source doit attendre.  
  
> [!NOTE]  
>  Cette option n’est valide que si vous avez sélectionné **A - Attendre la notification** comme valeur du **Mode d’exécution** dans la page **Gestionnaire de connexions** de l’éditeur. Pour plus d’informations, consultez [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md).  
  
 **ID de la demande**  
 Spécifiez l’ID de demande dont vous voulez réinitialiser l’état sur « V - Vert » quand vous cliquez sur **Réinitialiser**.  
  
 **Réinitialiser**  
 Vous permet de réinitialiser l'état de l'ID de demande spécifié sur « V - Vert », après l'invite de confirmation. Ce peut être utile lorsqu'un problème est survenu et que le système SAP Netweaver BW a marqué la demande avec un état jaune ou rouge.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Éditeur de source SAP BW &#40;page Colonnes&#41;](sap-bw-source-editor-columns-page.md)   
 [Éditeur de source SAP BW &#40;page Sortie d’erreur&#41;](sap-bw-source-editor-error-output-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
