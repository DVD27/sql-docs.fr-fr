---
title: Affichage du journal des erreurs SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cycling SQL Server error log
- viewing SQL Server error log
- errors [SQL Server], logs
- SQL Server error log
- displaying SQL Server error log
- logs [SQL Server], SQL Server error logs
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 54ceec989d9bb35807391f39beff543407a0c6f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058263"
---
# <a name="viewing-the-sql-server-error-log"></a>Consultation du journal des erreurs de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Consultez le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier que l’exécution des processus a réussi (par exemple les opérations de sauvegarde et de restauration, les commandes de traitement ou d’autres scripts et processus). Cela peut s’avérer utile pour détecter tout problème en cours ou potentiel, y compris les messages de récupération automatique (surtout si une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été arrêtée, puis redémarrée), les messages du noyau ou d’autres messages d’erreur de niveau serveur.  
  
 Consultez le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de n'importe quel éditeur de texte. Pour plus d'informations sur l'affichage du journal des erreurs, consultez [Open Log File Viewer](../../relational-databases/logs/open-log-file-viewer.md). Par défaut, le journal des erreurs se trouve dans les fichiers `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` et `ERRORLOG.`*n* .  
  
 Un journal des erreurs est créé à chaque démarrage d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , bien que la procédure stockée système [sp_cycle_errorlog](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md) puisse être utilisée pour recycler les fichiers du journal des erreurs sans devoir redémarrer l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En principe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve une copie de sauvegarde des six derniers journaux des erreurs, attribuant l'extension .1 au plus récent, l'extension .2 à celui qui le précède, et ainsi de suite. Le journal des erreurs en cours n'a aucune extension.  
  
 Soyez informé que vous pouvez également consulter le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est hors connexion ou ne peut pas démarrer. Pour plus d’informations, consultez [Afficher les fichiers journaux hors connexion](../../relational-databases/logs/view-offline-log-files.md).  
  
  
