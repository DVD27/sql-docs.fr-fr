---
title: Définir des points d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0c2c543343bd602be75d600a489edfd84663790b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62911401"
---
# <a name="set-breakpoints"></a>Définir des points d’arrêt
  Utilisez la boîte de dialogue **Définir des points d'arrêt** pour spécifier les événements pour lesquels activer des points d'arrêt et pour gérer le contrôle du point d'arrêt.  
  
## <a name="options"></a>Options  
 **Activé**  
 Sélectionnez cette option pour activer un point d'arrêt sur un événement.  
  
 **Condition d'arrêt**  
 Affichez la liste des événements disponibles sur lesquels définir des points d'arrêt.  
  
 **Type du nombre d'accès**  
 Spécifiez le moment où le point d'arrêt entre en vigueur.  
  
|Value|Description|  
|-----------|-----------------|  
|**Always**|L'exécution est toujours suspendue lorsque le point d'arrêt est atteint.|  
|**Égal au nombre d'accès**|L'exécution est suspendue lorsque le nombre de fois où s'est produit le point d'arrêt est égal au nombre d'accès.|  
|**Supérieur ou égal au nombre d'accès**|L'exécution est suspendue lorsque le nombre de fois où s'est produit le point d'arrêt est supérieur ou égal au nombre d'accès.|  
|**Multiple du nombre d'accès**|L'exécution est suspendue lorsqu'un multiple du nombre d'accès est atteint. Par exemple, si vous définissez cette option sur 5, l'exécution est suspendue une fois toutes les cinq fois.|  
  
 **Nombre d'accès**  
 Spécifiez le nombre d'accès à partir duquel déclencher un arrêt. Cette option n'est pas disponible si le point d'arrêt est constamment en vigueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du flux de contrôle](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
