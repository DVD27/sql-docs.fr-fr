---
title: Classement de serveur du moteur de base de données incompatible (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 235811baf7339416750a5e3795caae55b0ba70aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094751"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>Classement du serveur du moteur de base de données incompatible (Conseiller de mise à niveau)
  Mise à niveau de l’Assistant a détecté [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise une instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui est configuré pour utiliser un classement du serveur incompatible.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Mise à niveau de l’Assistant a détecté [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise une instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui est configuré pour utiliser un classement du serveur incompatible.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] En mode SharePoint utilise l’architecture de services partagés SharePoint. SharePoint ne prend pas en charge le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] configuré pour respecter la casse ou des classements du serveur ou des classements du serveur binaires. Les classements incompatibles incluent les classements qui respectent la casse par défaut ou binaires et un classement de base qui est par défaut compatible, a ont été configuré avec l'un des indicateurs de classement suivants :  
  
-   **Binaire**  
  
-   **Respect de la casse**  
  
-   **Binary-codepoint**  
  
 Étant donné que le classement du serveur du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] actuel est incompatible, la mise à niveau est bloquée.  
  
## <a name="corrective-action"></a>Action corrective  
 La propriété de classement du serveur du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ne peut pas être modifiée. Vous ne pouvez pas effectuer une mise à niveau de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Vous devez migrer votre installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un nouveau serveur qui utilise un classement du serveur compatible. Pour plus d'informations, consultez les documents suivants :  
  
-   [Mettre à niveau et migrer Reporting Services](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [Sélection d’un classement SQL Server](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
