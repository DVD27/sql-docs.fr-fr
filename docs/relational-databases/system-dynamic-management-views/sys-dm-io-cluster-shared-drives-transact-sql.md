---
title: Sys.dm_io_cluster_shared_drives (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_cluster_shared_drives_TSQL
- sys.dm_io_cluster_shared_drives
- dm_io_cluster_shared_drives_TSQL
- dm_io_cluster_shared_drives
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_cluster_shared_drives dynamic management view
ms.assetid: c8fcced8-c780-49dc-99bd-6beb3ca532c4
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d6633988bf660de8225b201266a4f2ef7ebea55e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900387"
---
# <a name="sysdmioclustershareddrives-transact-sql"></a>sys.dm_io_cluster_shared_drives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Cette vue retourne le nom de chaque lecteur partagé si l'instance de serveur active est un serveur cluster. Si l'instance de serveur active n'est pas une instance cluster, un ensemble de lignes vides est renvoyé.  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_io_cluster_shared_drives**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**DriveName**|**nchar(2)**|Nom (ou lettre) du lecteur qui représente un disque individuel appartenant au groupe de disques partagés en clusters. Colonne n'acceptant pas la valeur NULL.|  
|**pdw_node_id**|**Int**|**S’applique à**: ssPDW<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="remarks"></a>Notes  
 Lorsque le clustering est activé, il est nécessaire pour l'instance de cluster de basculement que les fichiers journaux et de données se trouvent sur des disques partagés afin de pouvoir y accéder une fois que l'instance a basculé vers un autre nœud. Chaque ligne de cette vue représente l'un des disques partagés qui sont utilisés par cette instance cluster de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Seuls les disques répertoriés par cette vue peuvent être utilisés pour stocker des fichiers journaux ou de données pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les disques figurant dans cette vue sont ceux qui font partie du groupe de ressources de cluster associé à l'instance.  
  
> [!NOTE]  
>  Cette vue sera abandonnée dans une version ultérieure. Nous vous recommandons d’utiliser [sys.dm_io_cluster_valid_path_names &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) à la place.  
  
## <a name="permissions"></a>Autorisations  
 L'utilisateur doit disposer de l'autorisation VIEW SERVER STATE pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise sys.dm_io_cluster_shared_drives pour déterminer les lecteurs partagés d'une instance de serveur cluster :  
  
```  
SELECT * FROM sys.dm_io_cluster_shared_drives;  
```  
  
 L'ensemble de résultats est le suivant :  
  
 DriveName  
  
 --------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.dm_io_cluster_valid_path_names &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [Sys.dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys.fn_servershareddrives &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  
