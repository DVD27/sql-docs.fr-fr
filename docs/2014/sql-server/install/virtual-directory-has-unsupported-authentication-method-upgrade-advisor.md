---
title: Méthode d’authentification (Conseiller de mise à niveau) du répertoire virtuel a non pris en charge | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 992e0f125d80a4735a356a853dab55439149e7ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66091054"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>Le répertoire virtuel a une méthode d'authentification non prise en charge (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté une méthode d'authentification non prise en charge dans le répertoire virtuel du Gestionnaire de rapports ou du serveur de rapports. Anonyme, Digest et .NET Passport. font partie des méthodes d'authentification non prises en charge par la mise à niveau.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le programme d'installation ne peut pas mettre à niveau une installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui utilise l'une des méthodes d'authentification suivantes  
  
-   Anonyme  
  
-   Digest  
  
-   .NET Passport  
  
 Pour continuer, vous pouvez modifier la méthode d'authentification spécifiée pour les répertoires virtuels de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans les services Internet (IIS), ou vous pouvez migrer votre installation. Pour plus d'informations sur la migration de votre installation, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Pour continuer la mise à niveau, modifiez la méthode d'authentification dans IIS pour les répertoires virtuels ReportServer et Reports. Pour plus d'informations sur la modification de méthodes d'authentification dans IIS, consultez la documentation relative à IIS. Après avoir modifié la méthode d'authentification pour les répertoires virtuels de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], relancez le Conseiller de mise à niveau pour confirmer qu'il n'y a pas d'autres problèmes de mise à niveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
