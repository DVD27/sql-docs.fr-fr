---
title: Enregistrer des packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: janinezhang
ms.author: janinez
ms.openlocfilehash: de8ff0e5d263ce432c431bfc4d9751620355f0a8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964315"
---
# <a name="save-packages"></a>Enregistrer des packages
  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , vous créez des packages à l’aide du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et vous les enregistrez dans le système de fichiers sous forme de fichiers XML (fichiers .dtsx). Vous pouvez également enregistrer des copies du fichier XML des packages dans la base de données msdb dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans le magasin de packages. Le magasin de packages représente les dossiers de l’emplacement du système de fichiers gérés par le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Si vous enregistrez un package dans le système de fichiers, vous pouvez utiliser par la suite le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour importer le package dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans le magasin de packages. Pour plus d’informations, consultez [Importer et exporter des packages &#40;Service SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md).  
  
 Vous pouvez également utiliser un utilitaire d’invite de commandes, **dtutil**, pour copier un package entre le système de fichiers et msdb. Pour plus d’informations, consultez [dtutil Utility](dtutil-utility.md).  
  
### <a name="to-save-a-package"></a>Pour enregistrer un package  
  
-   [Enregistrer un package dans le système de fichiers](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [Enregistrer une copie d'un package](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  
