---
title: Afficher la liste des packages sur le serveur Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 67d877d0ce4ea137c36a12a28140de85d2b527c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074671"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Afficher la liste des packages sur le serveur Integration Services

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Vous pouvez afficher la liste des packages stockés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de deux façons :  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Accès Transact-SQL  
 Pour afficher la liste des packages stockés sur le serveur, interrogez la vue [catalog.packages &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md).  
  
 Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
 Pour afficher les packages stockés sur le serveur à l’aide de l’Explorateur d’objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], procédez comme indiqué ci-dessous.  
  
### <a name="to-view-packages-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>Pour afficher les packages à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Autrement dit, connectez-vous à l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  Dans l'Explorateur d'objets, développez l'arborescence pour afficher le nœud **Integration Services Catalogues** .  
  
3.  Développez le nœud **Catalogues Integration Services** pour afficher le nœud **SSISDB** .  
  
4.  Développez le nœud **SSISDB** pour afficher une liste d'un ou de plusieurs dossiers. Chaque dossier contient un ou plusieurs projets dans le dossier **Projets** et chaque projet contient un ou plusieurs packages dans le dossier **Packages** .  
  
  
