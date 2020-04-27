---
title: Autorisations d'entité
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: db9187a5a30a740e8d790a8b84b5dae597de8bfd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728178"
---
# <a name="entity-permissions-master-data-services"></a>Autorisations d'entité (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Les autorisations d'entité s'appliquent à :  
  
-   Les attributs de l’entité, y compris **Nom** et **Code**, pour les membres feuille et les membres consolidés.  
  
-   Les collections de l’entité.  
  
-   Appartenances et relations de hiérarchie explicites.  
  
 Lorsque vous avez une autorisation sur une entité, vous pouvez ajouter et supprimer des membres de l'entité, ses hiérarchies explicites et ses collections.  
  
> [!NOTE]  
>  Ces autorisations s’appliquent à la zone fonctionnelle **Explorateur** de l’interface utilisateur uniquement.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**En lecture**|L’utilisateur peut lire des membres, des attributs, des appartenances hiérarchiques ou des appartenances aux collections.|  
|**Créer**|L’utilisateur peut créer des membres et affecter des valeurs d’attribut lors de la création.|  
|**Mise à jour**|L’utilisateur peut mettre à jour des membres, des attributs, des appartenances hiérarchiques ou des appartenances aux collections.|  
|**Supprimer**|Un utilisateur peut supprimer des membres.|  
|**Deny**|Refusez tous les accès à l’entité.|  
  
 Vous pouvez aussi combiner les autorisations d’accès pour la lecture, la création, la mise à jour et la suppression. Lorsque les autorisations de création, de mise à jour et de suppression sont attribuées, l’autorisation d’accès en lecture est attribuée automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Entités &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
