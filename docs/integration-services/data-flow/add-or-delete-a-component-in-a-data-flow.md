---
title: Ajouter ou supprimer un composant dans un flux de données | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6123a670053f5e6fa4b9c7196c9bc503b97c855b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71293507"
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a>Ajouter ou supprimer un composant dans un flux de données

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Les composants de flux de données sont des sources, des destinations et des transformations dans un flux de données. Pour que vous puissiez ajouter des composants à un flux de données, le flux de contrôle du package doit inclure une tâche de flux de données.  
  
 Les procédures ci-dessous montrent comment ajouter ou supprimer un composant dans le flux de données d'un package.  
  
### <a name="to-add-a-component-to-a-data-flow"></a>Pour ajouter un composant à un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données qui contient le flux de données auquel vous voulez ajouter un composant.  
  
4.  Dans la boîte à outils, développez **Sources de flux de données**, **Transformations du flux de données**ou **Destinations du flux de données**, puis faites glisser un élément de flux de données sur l’aire de conception de l’onglet **Flux de données** .  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-delete-a-component-from-a-data-flow"></a>Pour supprimer un composant d'un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données contenant le flux de données duquel vous voulez supprimer un composant.  
  
4.  Cliquez avec le bouton droit sur le composant du flux de données, puis cliquez sur **Supprimer**.  
  
5.  Confirmez la suppression.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Connecter des composants dans un flux de données](../../integration-services/data-flow/connect-components-in-a-data-flow.md)   
 [Débogage d’un flux de données](../../integration-services/troubleshooting/debugging-data-flow.md)   
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  
