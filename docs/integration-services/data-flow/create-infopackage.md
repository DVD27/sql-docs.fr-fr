---
title: Créer un Infopackage| Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: acae1d88d7bfd6e61eeeca582444f6be5627414c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68110558"
---
# <a name="create-infopackage"></a>Créer un InfoPackage

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Utilisez la boîte de dialogue **Créer un InfoPackage** pour créer un InfoPackage dans le système SAP Netweaver BW.  
  
 Vous pouvez ouvrir la boîte de dialogue **Créer un InfoPackage** depuis la page **Gestionnaire de connexions** de **l’Éditeur de destination SAP BW**. Pour en savoir plus sur la destination SAP BW, consultez [Destination SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Créer un InfoPackage**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la destination SAP BW.  
  
3.  Dans l' **Éditeur de destination SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la page **Gestionnaire de connexions** , dans la zone de groupe **Créer des objets SAP BW** , sélectionnez **InfoPackage**, puis cliquez sur **Créer**.  
  
## <a name="options"></a>Options  
 **InfoSource**  
 Entrez le nom de l'InfoSource sur lequel le nouvel InfoPackage doit être basé.  
  
 **Description courte**  
 Entrez une description pour le nouvel InfoPackage.  
  
 **Système source**  
 Sélectionnez le système source auquel le nouvel InfoPackage doit être associé.  
  
 **Attributs**  
 Indique que l'InfoPackage chargera les données d'attribut.  
  
 **Textes**  
 Indique que l'InfoPackage chargera les données de texte.  
  
 **Transaction**  
 Indique que l'InfoPackage chargera les données de transaction.  
  
 **Enregistrer et activer**  
 Enregistrez et activez le nouvel InfoPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
