---
title: Appliquer immédiatement des autorisations de membre
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 82ad2fad9645d3d8277abac6328d23c7b18a0c94
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729216"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a>Appliquer immédiatement des autorisations de membre (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], au lieu d'attendre que la sécurité des membres s'applique à intervalles réguliers, vous pouvez appliquer immédiatement des autorisations de membre.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'exécuter la procédure stockée mdm.udpSecurityMemberProcessRebuildModel dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Sécurité de l’objet de base de données &#40;Master Data Services&#41;](../master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a>Pour appliquer immédiatement des autorisations de membres de la hiérarchie  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Créez une requête.  
  
3.  Tapez le texte suivant, en remplaçant *database* par le nom de votre base de données et *Model_Name* par le nom du modèle.  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  Exécute la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Autorisations des membres de la hiérarchie &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
