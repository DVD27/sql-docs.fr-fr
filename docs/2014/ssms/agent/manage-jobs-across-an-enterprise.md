---
title: Gérer des travaux à l’échelle d’une entreprise | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f051b3de9ba88354f5fded8cd1f429e3b277747
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63188170"
---
# <a name="manage-jobs-across-an-enterprise"></a>Gérer des travaux à l'échelle d'une entreprise
  Si vous apportez des modifications à des définitions de travaux [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]multiserveur en dehors de, vous devez poster les modifications dans la liste de téléchargement afin que les serveurs cibles puissent télécharger à nouveau le travail mis à jour. Pour vous assurer que les serveurs cibles possèdent les définitions des travaux les plus récentes, publiez une instruction INSERT après avoir mis à jour les travaux multiserveur. Pour ce faire, procédez comme suit :  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 Pour notifier les serveurs cibles qu'un travail multiserveur a été modifié, vous devez appeler la commande précédente après avoir utilisé l'une des procédures suivantes :  
  
-   [sp_add_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_update_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)  
  
-   [sp_delete_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)  
  
-   [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [sp_detach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql)  
  
    > [!NOTE]  
    >  Il n'est pas nécessaire d'appeler **sp_post_msx_operation** après avoir appelé **sp_update_job** ou **sp_delete_job**, car ces procédures stockées publient automatiquement les modifications nécessaires dans la liste de téléchargements.  
  
 Ci-dessous figurent des tâches courantes permettant de gérer les travaux à l'échelle d'une entreprise :  
  
 **Pour vérifier l’état d’un serveur cible**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)  
  
-   [SMO (SQL Server Management Objects)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **Pour modifier les serveurs cibles pour un travail**  
  
-   [SQL Server Management Studio](modify-the-target-servers-for-a-job.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
-   [SMO (SQL Server Management Objects)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **Pour modifier l’emplacement d’un serveur cible**  
  
-   [SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
-   [SMO (SQL Server Management Objects)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **Pour synchroniser les horloges des serveurs cibles**  
  
-   [SQL Server Management Studio](synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)  
  
 **Pour forcer un serveur cible à interroger le serveur maître**  
  
-   [SQL Server Management Studio](force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les événements](manage-events.md)  
  
  
