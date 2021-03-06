---
title: Gestion des packages et des dossiers par programmation | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: janinezhang
ms.author: janinez
ms.openlocfilehash: eb313fa34500cb9ae2d6f49bd930bd96e407bd2b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028460"
---
# <a name="managing-packages-and-folders-programmatically"></a>Gestion des packages et des dossiers par programme

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


<a name="top"></a> Quand vous travaillez par programmation avec des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez avoir besoin de déterminer si un package ou un dossier individuel existe, ou de gérer les dossiers dans lesquels les packages sont stockés. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit différentes méthodes pour répondre à ces impératifs.    
    
##  <a name="exists"></a> Détermination de l’existence d’un package ou dossier    
 Pour déterminer par programmation si un package enregistré existe, appelez l’une des méthodes suivantes avant de tenter de le charger et l’exécuter :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 Pour déterminer par programme si un dossier existe, appelez l'une des méthodes suivantes avant de tenter de répertorier les packages stockés dans ce dossier :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [Retour au début](#top)    
    
##  <a name="managing"></a> Gestion des packages et des dossiers    
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit des méthodes supplémentaires pour gérer les packages et les dossiers dans lesquels ils sont stockés.    
    
###  <a name="managing_rempkg"></a> Suppression d’un package    
 Pour supprimer un package enregistré par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|    
    
 [Retour au début](#top)    
    
###  <a name="managing_create"></a> Création d’un dossier    
 Pour créer un dossier de stockage par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|    
    
 [Retour au début](#top)    
    
###  <a name="managing_remfldr"></a> Suppression d’un dossier    
 Pour supprimer un dossier de stockage par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|    
    
 [Retour au début](#top)    
    
###  <a name="managing_rename"></a> Renommage d’un dossier    
 Pour renommer un dossier de stockage par programme, appelez l'une des méthodes suivantes :    
    
|Emplacement de stockage|Méthode à appeler|    
|----------------------|--------------------|    
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|    
    
 [Retour au début](#top)    
    
## <a name="see-also"></a>Voir aussi    
 [Gestion de packages &#40;Service SSIS&#41;](../../integration-services/service/package-management-ssis-service.md)     
 [Énumération des packages disponibles par programmation](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)    
    
  
