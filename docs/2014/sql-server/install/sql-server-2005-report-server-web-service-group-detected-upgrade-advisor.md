---
title: SQL Server groupe de services Web du serveur de rapports 2005 détecté (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: bfeff5eae569b481edfcc1cacc89c26e44edaece
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952374"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a>Le groupe de service Web du serveur de rapports SQL Server 2005 a été détecté (Conseiller de mise à niveau)
  Le conseiller de mise à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] niveau a détecté que l' [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] instance est associée à un groupe de service Web Report Server.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n’utilise pas le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Groupe de service Web Report Server. Lorsque vous effectuez une mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce groupe de service est supprimé et les listes de contrôle d'accès personnalisées pour ce groupe ou les utilisateurs qui appartiennent au groupe ne sont pas conservés pendant la mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de procéder à la mise à niveau, sauvegardez toutes les listes de contrôle d'accès personnalisées ou tous les utilisateurs qui appartiennent au groupe de service Web Report Server [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour ce faire, vous pouvez utiliser l’outil en ligne de commande **icacls. exe** dans [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 et versions ultérieures ou l’outil en ligne de commande cacls. exe dans les [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] systèmes d’exploitation Windows antérieurs à SP2. Pour plus d'informations sur la syntaxe utilisée dans ces outils, consultez la documentation produit de Windows. Une fois l'installation terminée, appliquez les listes de contrôle d'accès personnalisées ou les utilisateurs au groupe Windows Report Server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour votre instance du serveur de rapports. Le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] groupe Windows du serveur de rapports prend la forme de\<SQLServerReportServerUser $*computer_name*>$\<*instance_name*>.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Reporting Services &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
