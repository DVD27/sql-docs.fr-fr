---
title: Afficher un journal d’audit SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9bc987034cde54d5c90392876f223ef5cf428562
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "72903796"
---
# <a name="view-a-sql-server-audit-log"></a>Afficher un journal d'audit SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment afficher un journal d'audit SQL Server dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher un journal d'audit SQL Server, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert l’autorisation **CONTROL SERVER** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>Pour afficher un journal d'audit SQL Server  
  
1.  Dans l'Explorateur d'objets, développez le dossier **Sécurité** .  
  
2.  Développez le dossier **Audits** .  
  
3.  Cliquez avec le bouton droit sur le journal d’audit que vous souhaitez afficher et sélectionnez **Afficher les journaux d’audit**. La boîte de dialogue **Visionneuse du fichier journal -** _nom\_serveur_ s’ouvre alors. Pour plus d'informations, consultez [Log File Viewer F1 Help](../../../relational-databases/logs/log-file-viewer-f1-help.md).  
  
4.  Lorsque vous avez terminé, cliquez sur **Fermer**.  

 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande d'afficher le journal d'audit à l'aide de la visionneuse du fichier journal. Toutefois, si vous créez un système de surveillance automatisé, les informations contenues dans le fichier d’audit peuvent être lues directement à l’aide de la fonction [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Si le fichier est lu directement, les données sont retournées dans un format légèrement différent (non traité). Pour plus d’informations, consultez **sys.fn_get_audit_file** .  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Audit &#40moteur de base de données&#41;](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Écrire des événements d’audit SQL Server dans le journal de sécurité](../../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md)  
  
  
