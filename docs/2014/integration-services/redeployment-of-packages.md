---
title: Redéploiement des packages | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 33eb116ec2824af31eae236a8efd4038a9cbbb68
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964579"
---
# <a name="redeployment-of-packages"></a>Redéploiement de packages
  Après qu'un projet a été déployé, vous pouvez avoir besoin de mettre à jour ou d'étendre les fonctionnalités du package, puis de redéployer le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient les packages mis à jour. Au cours du processus de redéploiement des packages, vous devez vérifier les propriétés de configuration incluses dans l'utilitaire de déploiement. Par exemple, vous pouvez décider de ne pas autoriser les modifications de configuration après le redéploiement du package.  
  
## <a name="process-for-redeployment"></a>Processus de redéploiement  
 Après avoir mis à jour les packages, vous recréez le projet, vous copiez le dossier de déploiement sur l'ordinateur cible et vous réexécutez l'Assistant Installation de package.  
  
 Si vous ne mettez à jour que quelques packages dans le projet, vous ne souhaitez pas forcément redéployer le projet tout entier. Pour ne déployer que quelques packages, vous pouvez créer un nouveau projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , ajouter les packages mis à jour au nouveau projet, puis créer et déployer le projet. Les configurations de package sont automatiquement copiées avec le package lorsque vous l'ajoutez à un autre projet.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Déployer des packages à l’aide de l’utilitaire de déploiement](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
