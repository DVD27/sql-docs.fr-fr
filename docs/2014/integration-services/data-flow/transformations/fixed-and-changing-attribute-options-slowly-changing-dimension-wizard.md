---
title: Options des attributs fixes et variables (Assistant Dimension à variation lente) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9e9e18d251335ea10721fa1d159d63530d973581
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939520"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>Options des attributs fixes et variables (Assistant Dimension à variation lente)
  Utilisez la boîte de dialogue **Options des attributs fixes et variables** pour spécifier comment répondre aux modifications apportées aux attributs fixes et variables.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Options  
 **Attributs fixes**  
 Pour les attributs fixes, indiquez si la tâche doit échouer lorsqu'un changement est détecté dans un attribut fixe.  
  
 **Modification des attributs**  
 Pour les attributs variables, spécifiez si la tâche doit modifier les enregistrements obsolètes ou expirés, en plus des enregistrements actuels, lorsqu'un changement est détecté dans un attribut variable. Un enregistrement expiré est un enregistrement qui a été remplacé par un enregistrement plus récent par une modification d'un attribut d'historique (modification de Type 2). La sélection de cette option peut imposer des exigences de traitement supplémentaires sur un objet multidimensionnel construit sur l'entrepôt de données relationnelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
