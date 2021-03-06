---
title: Décharger les sauvegardes prises en charge vers des réplicas secondaires d’un groupe de disponibilité
description: Découvrez les différents types de sauvegardes prises en charge lors du déchargement de sauvegardes vers un réplica secondaire d’un groupe de disponibilité Always On.
ms.custom: seodec18
ms.date: 09/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccaf0091472ed0b7c87dbb790228024d0224e91a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67991692"
---
# <a name="offload-supported-backups-to-secondary-replicas-of-an-availability-group"></a>Décharger les sauvegardes prises en charge vers des réplicas secondaires d’un groupe de disponibilité
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Les fonctions secondaires actives [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] incluent la prise en charge des opérations de sauvegarde sur les réplicas secondaires. Les opérations de sauvegarde peuvent solliciter de manière significative les E/S et l'UC (avec la compression de sauvegarde). Le déchargement des sauvegardes vers un réplica secondaire synchronisé ou en cours de synchronisation vous permet d'utiliser les ressources sur l'instance de serveur qui héberge le réplica principal pour vos charges de travail de niveau 1.  

> [!NOTE]  
>  Les instructions RESTORE ne sont pas autorisées sur les bases de données primaire ou secondaire d'un groupe de disponibilité.  
  
 
##  <a name="SupportedBuTypes"></a> Types de sauvegardes pris en charge sur les réplicas secondaires  
  
-   **BACKUP DATABASE** prend en charge uniquement la copie seule des sauvegardes complètes de la base de données, des fichiers ou des groupes de fichiers lorsqu’elle est exécutée sur les réplicas secondaires. Notez que les sauvegardes de type copie seule n'affectent pas la séquence de journaux de transactions consécutifs ou n'effacent pas la bitmap différentielle.  
  
-   Les sauvegardes différentielles ne sont pas prises en charge sur les réplicas secondaires.  
  
-   **BACKUP LOG** prend uniquement en charge les sauvegardes de journaux régulières (l’option COPY_ONLY n’est pas prise en charge pour les sauvegardes de fichiers journaux sur des réplicas secondaires).  
  
     Une séquence de journaux de transactions consécutifs cohérente est garantie sur les sauvegardes des journaux effectuées sur les réplicas (principaux ou secondaires), quel que soit leur mode de disponibilité (avec validation synchrone ou validation asynchrone).  
  
-   Pour sauvegarder une base de données secondaire, un réplica secondaire doit pouvoir communiquer avec le réplica principal et doit être **SYNCHRONIZED** ou **SYNCHRONIZING**.  

Dans un groupe de disponibilité distribué, les sauvegardes peuvent être effectuées sur les réplicas secondaires dans le même groupe de disponibilité que le réplica principal actif, ou sur le réplica principal d’un groupe de disponibilité secondaire. Les sauvegardes ne peuvent pas être effectuées sur un réplica secondaire dans un groupe de disponibilité secondaire, car les réplicas secondaires communiquent uniquement avec le réplica principal dans leur propre groupe de disponibilité. Seuls les réplicas qui communiquent directement avec le réplica principal global peuvent effectuer des opérations de sauvegarde.

##  <a name="WhereBuJobsRun"></a> CConfiguration de l'emplacement d'exécution des travaux de sauvegarde  
 L'exécution de sauvegardes sur un réplica secondaire pour décharger la charge de travail de sauvegarde du serveur de production principal constitue un énorme avantage. Cependant, les sauvegardes sur des réplicas secondaires compliquent considérablement la détermination de l'emplacement d'exécution des travaux de sauvegarde. Pour résoudre ce problème, configurez l'emplacement d'exécution des travaux de sauvegarde comme suit :  
  
1.  Configurez le groupe de disponibilité pour spécifier les réplicas de disponibilité de votre choix pour effectuer les sauvegardes. Pour plus d’informations, consultez les paramètres *AUTOMATED_BACKUP_PREFERENCE* et *BACKUP_PRIORITY* dans [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md) ou [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
2.  Créez les travaux de sauvegarde par script pour chaque base de données de disponibilité sur chaque instance de serveur qui héberge un réplica de disponibilité candidat pour effectuer des sauvegardes. Pour plus d’informations, consultez la section « Suivi : Après la configuration de la sauvegarde sur les réplicas secondaires » de [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour configurer la sauvegarde sur les réplicas secondaires**  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
 **Pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](../../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md)  
  
 **Pour créer un travail de sauvegarde**  
  
-   [Utiliser l'Assistant Plan de maintenance](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [Implémenter des travaux](../../../ssms/agent/implement-jobs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Sauvegardes de type copie seule &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
