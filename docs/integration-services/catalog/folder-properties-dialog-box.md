---
title: Boîte de dialogue Propriétés du dossier | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.isfolderprop.permissions.f1
- sql13.ssis.ssms.iscreatefolder.f1
- sql13.ssis.ssms.isfolderprop.general.f1
ms.assetid: d9a2bfae-fcc8-46be-b588-4a9db03f7e45
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 302d529f062b31eed4c4cbda583c06b86d1a8c1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070572"
---
# <a name="folder-properties-dialog-box"></a>Propriétés du dossier, boîte de dialogue

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un dossier contient des projets et des environnements dans le catalogue **SSISDB** . Chaque dossier définit des autorisations qui s'appliquent au contenu du dossier. Pour plus d’informations sur les autorisations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , consultez [catalog.grant_permission &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md).  
  
## <a name="to-set-folder-description-and-permissions"></a>Pour définir la description et les autorisations d'un dossier  
  
1.  Cliquez avec le bouton droit sur le dossier et sélectionnez **Propriétés**.  
  
2.  Dans la page **Général** , sélectionnez **Description** sous **Général** , puis entrez une description facultative.  
  
3.  Dans la page **Autorisations** , cliquez sur **Parcourir**, sélectionnez un ou plusieurs principaux de base de données, puis cliquez sur **OK**.  
  
4.  Sélectionnez un nom sous **Connexions ou rôles** et spécifiez les autorisations appropriées sous **Autorisations**.  
  
5.  Cliquez sur **OK** pour accepter les modifications et fermer la boîte de dialogue **Propriétés du dossier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur Integration Services &#40;SSIS&#41;](../integration-services-ssis-packages.md)   
 [catalog.grant_permission &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)  
  
  
