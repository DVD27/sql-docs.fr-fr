---
title: Nouveautés de&#39;(Moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5e51cda61bb44d1f143cab50901276b927cca73a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176080"
---
# <a name="what39s-new-database-engine"></a>Nouveautés de&#39;(Moteur de base de données)
  Cette nouvelle version du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] intègre de nouvelles fonctionnalités et des améliorations qui augmentent la puissance et la productivité des architectes, des développeurs et des administrateurs qui conçoivent, développent et maintiennent des systèmes de stockage de données. Vous trouverez ci-dessous les domaines d'amélioration du [!INCLUDE[ssDE](../includes/ssde-md.md)] .  
  
##  <a name="Feature"></a>Améliorations des fonctionnalités de Moteur de base de données  
  
###  <a name="MemoryOpt"></a>Tables optimisées en mémoire  
 L'OLTP en mémoire est un moteur de base de données mémoire optimisé intégré au moteur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . L'OLTP en mémoire est optimisé pour OLTP. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
 
  
###  <a name="DataFiles"></a>SQL Server de fichiers de données dans Azure  
 [SQL Server fichiers de données dans Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) permet la prise [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en charge native des fichiers de base de données stockés en tant qu’objets BLOB Azure. Cette fonctionnalité vous permet de créer une base de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] données en cours d’exécution localement ou dans une machine virtuelle dans Azure à l’aide d’un emplacement de stockage dédié pour vos données dans le stockage d’objets BLOB Azure.  
  
  
###  <a name="AzureVM"></a>Héberger une base de données SQL Server sur une machine virtuelle Azure  
 Utilisez l’Assistant [déployer une base de données SQL Server sur une machine virtuelle Azure](https://msdn.microsoft.com/library/dn195938\(v=sql.120\).aspx) pour héberger une base de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] données à partir d’une instance de dans une machine virtuelle Azure.  
  
  
###  <a name="Backup"></a>Améliorations de la sauvegarde et de la restauration  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]contient les améliorations suivantes pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la sauvegarde et la restauration :  
  
-   **Sauvegarde SQL Server vers une URL**  
  
     La fonctionnalité Sauvegarde [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers une URL a été présentée dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] SP1 CU2 et n'est prise en charge que par [!INCLUDE[tsql](../includes/tsql-md.md)], PowerShell et SMO. Dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] , vous pouvez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] utiliser pour effectuer une sauvegarde ou une restauration à partir du service de stockage d’objets BLOB Azure. La nouvelle option est disponible pour les tâches de sauvegarde et les plans de maintenance à la fois. Pour plus d’informations, consultez [utilisation de la tâche de sauvegarde dans SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#BackupTaskSSMS), [SQL Server sauvegarde vers une URL à l’aide de l’Assistant Plan de maintenance](../relational-databases/backup-restore/sql-server-backup-to-url.md#MaintenanceWiz)et [restauration à partir d’Azure storage à l’aide de SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS).  
  
-   **Sauvegarde managée de SQL Server vers Azure**  
  
     Reposant sur la fonctionnalité Sauvegarde [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers une URL, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est un service fourni par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour gérer et planifier les sauvegardes de base de données et de journaux. Dans cette version, seule la sauvegarde dans le stockage Azure est prise en charge. La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] peut être configurée au niveau de la base de données ou de l'instance, ce qui permet un contrôle granulaire au niveau de la base de données, et l'automatisation au niveau de l'instance. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]peut être configuré sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] des instances s’exécutant sur site [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sur des instances s’exécutant sur des machines virtuelles Azure. Elle est recommandée pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] les instances exécutées sur des machines virtuelles Azure. Pour plus d’informations, consultez [SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
-   **Chiffrement pour les sauvegardes**  
  
     Vous pouvez maintenant choisir de chiffrer le fichier de sauvegarde pendant l'opération de sauvegarde.  Plusieurs algorithmes de chiffrement sont pris en charge, dont AES 128, AES 192, AES 256, et Triple DES. Vous devez utiliser un certificat ou une clé asymétrique pour effectuer un chiffrement pendant une sauvegarde. Pour plus d'informations, consultez [Chiffrement de sauvegarde](../relational-databases/backup-restore/backup-encryption.md).  
  
  
###  <a name="CE"></a>Nouvelle conception pour l’estimation de la cardinalité  
 La logique d'estimation de la cardinalité, appelée estimateur de cardinalité, est remodelée dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] afin d'améliorer la qualité des plans de requête, et par conséquent, améliorer les performances des requêtes. Le nouvel estimateur de cardinalité incorpore des hypothèses et des algorithmes qui fonctionnent sur les charges de travail OLTP et de stockage de données modernes. Il repose sur la recherche détaillée des estimations de cardinalité sur les charges de travail modernes et sur nos connaissances acquises au cours des 15 dernières années sur l'amélioration de l'estimateur de cardinalité SQL Server. Les commentaires des clients indiquent que bien que la plupart des requêtes tirent parti des modifications ou demeurent inchangées, un petit nombre d'entre elles présente des régressions par rapport à l'estimateur de cardinalité précédent. Pour obtenir des recommandations sur le réglage et le test des performances, consultez estimation de la [cardinalité &#40;SQL Server&#41;](../relational-databases/performance/cardinality-estimation-sql-server.md).  
   
  
###  <a name="Durability"></a>Durabilité retardée  
 
  [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] offre la possibilité de réduire la latence en désignant tout ou partie des transactions en tant que transactions durables différées. Une transaction durable différée restitue le contrôle au client avant l'écriture de l'enregistrement du journal des transactions sur le disque. La durabilité peut être contrôlée au niveau de la base de données, de COMMIT ou d'un bloc ATOMIC.  
  
 Pour plus d’informations, consultez la rubrique contrôle de la [durabilité des transactions](../relational-databases/logs/control-transaction-durability.md).  
  
  
###  <a name="AlwaysOn"></a>Améliorations AlwaysOn  
 
  [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] contient les améliorations suivantes pour les instances de cluster de basculement AlwaysOn et les groupes de disponibilité AlwaysOn :  
  
-   L'Assistant Ajouter un réplica Windows Azure simplifie la création de solutions hybrides pour les groupes de disponibilité AlwaysOn. Pour plus d’informations, consultez [utiliser l’Assistant Ajout d’un réplica Azure &#40;SQL Server&#41;](availability-groups/windows/use-the-add-azure-replica-wizard-sql-server.md).  
  
-   Le nombre maximal de réplicas secondaires est augmenté de 4 à 8.  
  
-   Une fois déconnectés du réplica principal ou lors de la perte de quorum du cluster, les réplicas secondaires accessibles en lecture restent disponibles pour les charges de travail en lecture.  
  
-   Les instances de cluster de basculement utilisent maintenant les volumes partagés de cluster (CSV) comme disques partagés dans le cluster. Pour plus d’informations, consultez [Always on des instances de cluster de basculement](../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
-   Une nouvelle fonction système, [sys.fn_hadr_is_primary_replica](/sql/relational-databases/system-functions/sys-fn-hadr-is-primary-replica-transact-sql), et une nouvelle vue de gestion dynamique (DMV), [sys.dm_io_cluster_valid_path_names](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql), sont disponible.  
  
-   Les vues de gestion dynamique suivantes ont été améliorées et retournent maintenant les informations de l'instance de cluster de basculement : [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), et [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql).  
  
  
###  <a name="OIR"></a>Basculement et indexation de partitions  
 Les partitions individuelles de tables partitionnées peuvent maintenant être reconstruites. Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Lock"></a>Gestion de la priorité de verrouillage des opérations en ligne  
 L'option `ONLINE = ON` contient maintenant une option `WAIT_AT_LOW_PRIORITY` qui vous permet de spécifier la durée pendant laquelle le processus de reconstruction doit attendre les verrous nécessaires. L'option `WAIT_AT_LOW_PRIORITY` vous permet également de configurer la fin des processus de blocage liés à cette instruction de reconstruction. Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) et [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql). Des informations de dépannage sur les nouveaux types d’États de verrou sont disponibles dans [sys. dm_tran_locks &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) et [sys. dm_os_wait_stats &#40;transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).  
 
  
###  <a name="CCI"></a>Index ColumnStore  
 Nouvelles fonctionnalités disponibles pour les index columnstore :  
  
-   **Index ColumnStore en cluster**  
  
     Utilisez un index columnstore cluster pour améliorer la compression de données et les performances des requêtes pour les charges de travail de stockage des données qui exécutent principalement des chargements en masse et des requêtes en lecture seule. Étant donné que l'index columnstore cluster est modifiable, la charge de travail peut exécuter certaines insertions, mises à jour, et suppressions. Pour plus d’informations, consultez [index ColumnStore décrits](../relational-databases/indexes/columnstore-indexes-described.md) et [utilisation d’index cluster ColumnStore](../relational-databases/indexes/indexes.md).  
  
-   **SHOWPLAN**  
  
     SHOWPLAN affiche des informations à propos des index columnstore. Les propriétés **EstimatedExecutionMode** et **ActualExecutionMode** ont deux valeurs possibles : **Batch** ou **Row**.  La propriété **Storage** a deux valeurs possibles : **RowStore** et **ColumnStore**.  
  
-   **Compression des données d'archive**  
  
     MODIFIER L’INDEX... Rebuild offre une nouvelle COLUMNSTORE_ARCHIVE option de compression des données qui compresse davantage les partitions spécifiées d’un index COLUMNSTORE. Utilisez cette option pour l'archivage ou dans d'autres situations qui nécessitent une plus petite taille de stockage des données et qui supportent un temps de stockage et de récupération plus long. Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Buffer"></a>Extension du pool de mémoires tampons  
 L'option [Extension du pool de mémoires tampons](configure-windows/buffer-pool-extension.md) permet l'intégration transparente de disques SSD en tant qu'extension NvRAM (nonvolatile random access memory) du pool de mémoires tampons du [!INCLUDE[ssDE](../includes/ssde-md.md)] pour améliorer considérablement le débit d'E/S.  
   
  
###  <a name="Stats"></a>Statistiques incrémentielles  
 CREATE STATISTICS et les instructions statistiques connexes permettent désormais de créer des statistiques par partition à l'aide de l'option INCREMENTAL. Les instructions connexes autorisent ou signalent des statistiques incrémentielles. La syntaxe concernée comprend UPDATE STATISTICs, sp_createstats, CREATe INDEX, ALTER INDEX, ALTER DATABASE SET options, DATABASEPROPERTYEX, sys. databases et sys. stats. Pour plus d’informations, consultez [create statistics &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
  
###  <a name="RG"></a>Resource Governor améliorations du contrôle d’e/s physique  
 Le gouverneur de ressources vous permet de spécifier des limites sur la quantité d'UC, les E/S physiques et la mémoire que les demandes d'application entrantes peuvent utiliser avec le pool de ressources. Dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], vous pouvez utiliser les nouveaux paramètres MIN_IOPS_PER_VOLUME et MAX_IOPS_PER_VOLUME pour contrôler les entrées/sorties physiques des threads utilisateur pour un pool de ressources spécifique. Pour plus d’informations, consultez [Resource Governor pool de ressources](../relational-databases/resource-governor/resource-governor-resource-pool.md) et [créer un pool de ressources &#40;&#41;Transact-SQL ](/sql/t-sql/statements/create-resource-pool-transact-sql).  
  
 Le paramètre MAX_OUTSTANDING_IO_PER_VOLUME de ALTER RESOURCE GOVENOR correspond aux opérations d'E/S en attente maximales par volume disque. Utilisez-le pour ajuster la gouvernance des ressources d'E/S aux spécifications d'E/S d'un volume disque et pour limiter le nombre d'entrées/sorties émises à la limite de l'instance de SQL Server. Pour plus d’informations, consultez [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql).  
  
  
###  <a name="OnlineEvent"></a>Online index Operation (classe d’événements)  
 Le rapport de progression de la classe d'événements d'opération d'index en ligne présente désormais deux nouvelles colonnes de données : **PartitionId** et **PartitionNumber**. Pour plus d'informations, consultez [Progress Report: Online Index Operation Event Class](../relational-databases/event-classes/progress-report-online-index-operation-event-class.md).  
  
  
###  <a name="Compat"></a>Niveau de compatibilité de la base de données  
 Le niveau de compatibilité 90 n'est pas pris en charge dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]. Pour plus d’informations, consultez [niveau de compatibilité ALTER database &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
##  <a name="TSQL"></a>Améliorations de Transact-SQL  
  
### <a name="inline-specification-of-clustered-and-nonclustered"></a>Spécification incluse d'index CLUSTERED et NONCLUSTERED  
 La spécification incluse des index `CLUSTERED` et `NONCLUSTERED` n'est pas autorisée dans les tables sur disque. Créer une table contenant des index intégrés revient à émettre une instruction create table suivie des instructions `CREATE INDEX` correspondantes. Les colonnes incluses et les conditions de filtre ne sont pas prises en charge par les index intégrés.  
  
### <a name="select--into"></a>SÉLECTIONNER... DANS  
 L'instruction `SELECT ... INTO` est améliorée et peut maintenant se produire simultanément. Le niveau de compatibilité de la base de données doit être au moins 110.  
  
### <a name="includetsqlincludestsql-mdmd-enhancements-for-in-memory-oltp"></a>Améliorations [!INCLUDE[tsql](../includes/tsql-md.md)] pour l'OLTP en mémoire  
 Pour plus d'informations sur les modifications [!INCLUDE[tsql](../includes/tsql-md.md)] pour la prise en charge de l'OLTP en mémoire, consultez [Transact-SQL Support for In-Memory OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md).  
  
  
##  <a name="SystemTable"></a>Améliorations des vues système  
  
### <a name="sysxml_indexes"></a>sys.xml_indexes  
 [sys. xml_indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-xml-indexes-transact-sql) contient 3 nouvelles colonnes : `xml_index_type`, `xml_index_type_description`et `path_id`.  
  
### <a name="sysdm_exec_query_profiles"></a>sys.dm_exec_query_profiles  
 [sys. dm_exec_query_profiles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql) surveille la progression des requêtes en temps réel pendant l’exécution d’une requête.  
  
### <a name="syscolumn_store_row_groups"></a>sys.column_store_row_groups  
 [sys. column_store_row_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql) fournit des informations d’index ColumnStore en cluster sur une base par segment pour aider l’administrateur à prendre des décisions de gestion du système.  
  
### <a name="sysdatabases"></a>sys.databases  
 [sys. databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) contient 3 nouvelles colonnes : `is_auto_create_stats_incremental_on`, `is_query_store_on`et `resource_pool_id`.  
  
### <a name="system-view-enhancements-for-in-memory-oltp"></a>Améliorations des vues système pour l'OLTP en mémoire  
 Pour plus d’informations sur les améliorations de la vue système pour la prise en charge de l’OLTP en mémoire, consultez [vues système, procédures stockées, DMV et types d’attente pour l’OLTP en mémoire](../../2014/database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md).  
   
  
##  <a name="Security"></a>Améliorations de la sécurité  
  
### <a name="connect-any-database-permission"></a>Autorisation CONNECT ANY DATABASE  
 Nouvelle autorisation au niveau serveur. Accordez l'autorisation **CONNECT ANY DATABASE** à une connexion qui doit se connecter à toutes les bases de données existantes et à celles qui pourront être créées. N'accorde pas d'autorisation dans une base de données au-delà de la connexion. Combinez avec **Sélectionner tous les éléments sécurisables** de l’utilisateur ou `VIEW SERVER STATE` pour autoriser un processus d’audit à afficher toutes les données ou tous les [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]États de la base de données sur l’instance de.  
  
### <a name="impersonate-any-login-permission"></a>Autorisation IMPERSONATE ANY LOGIN  
 Nouvelle autorisation au niveau serveur. Lorsque cette autorisation est accordée, elle permet à un processus de niveau intermédiaire d'emprunter l'identité du compte des clients qui se connectent, à mesure qu'il se connecte aux bases de données. Si cette autorisation est refusée, une connexion dotée de privilèges élevés peut être bloquée à partir de l'emprunt d'identité d'autres connexions. Par exemple, une connexion dotée de l'autorisation **CONTROL SERVER** peut être bloquée à partir de l'emprunt d'identité d'autres connexions.  
  
### <a name="select-all-user-securables-permission"></a>Autorisation SELECT ALL USER SECURABLES  
 Nouvelle autorisation au niveau serveur. Lorsque cette autorisation est accordée, une connexion telle qu'un auditeur peut afficher les données de toutes les bases de données auxquelles l'utilisateur se connecte.  
  
  
##  <a name="Deployment"></a>Améliorations du déploiement  
### <a name="azure-vm"></a>Azure VM
[Déployer une base de données SQL Server sur une machine virtuelle Microsoft Azure](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) permet le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] déploiement d’une base de données sur une machine virtuelle Azure.  

### <a name="refs"></a>ReFS
Le déploiement de bases de données sur ReFS est désormais pris en charge.   
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
   
