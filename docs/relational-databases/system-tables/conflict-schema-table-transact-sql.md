---
title: conflict_&lt;schéma&gt;_&lt;table&gt; (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- conflict_
- conflict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- conflict_<schema>_<table>
ms.assetid: 15ddd536-db03-454e-b9b5-36efe1f756d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4725da28e9cd83df4979d1cc476cd60a488c0aa4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084768"
---
# <a name="conflictltschemagtlttablegt-transact-sql"></a>conflict_&lt;schéma&gt;_&lt;table&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table conflict_\<schéma > _\<table > table contient des informations sur les lignes en conflit dans la réplication d’égal à égal. Il existe une table de conflits pour chaque table répliquée dans une publication, où le nom de la table de conflits est ajouté au nom du schéma et à celui de l'article. Ces tables de conflits spécifiques aux articles existent dans chaque base de données de publication.  
  
 Pour la réplication d'égal à égal, par défaut, l'Agent de distribution échoue lorsqu'il détecte un conflit. Une erreur de conflit est enregistrée dans le journal des erreurs, mais aucune donnée de conflit n'est enregistrée dans la table de conflits ; par conséquent, la consultation de cette erreur n'est pas possible. Si l'Agent de distribution est autorisé à continuer, un conflit est enregistré localement sur chaque nœud où il a été détecté. Pour plus d'informations, consultez « Gestion des conflits » dans [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|__$originator_id|**int**|ID du nœud d'où provient la modification conflictuelle Pour obtenir la liste des ID, exécutez [sp_help_peerconflictdetection](../../relational-databases/system-stored-procedures/sp-help-peerconflictdetection-transact-sql.md).|  
|__$origin_datasource|**int**|Nœud d'où provient la modification conflictuelle.|  
|__$tranid|**nvarchar (40)**|Numéro séquentiel dans le journal (LSN) de la modification en conflit appliquée à __$origin_datasource.|  
|__$conflict_type|**int**|Type de conflit qui s'est produit, qui peut être l'une des valeurs suivantes :<br /><br /> 1 : Une mise à jour a échoué, car la ligne locale a été modifiée par une autre mise à jour ou si elle a été supprimée et puis réinsérée.<br /><br /> 2 : Une mise à jour a échoué, car la ligne locale a déjà été supprimée.<br /><br /> 3 : Une suppression a échoué, car la ligne locale a été modifiée par une autre mise à jour ou si elle a été supprimée et puis réinsérée.<br /><br /> 4 : Une suppression a échoué, car la ligne locale a déjà été supprimée.<br /><br /> 5 : Une insertion a échoué parce que la ligne locale a déjà été insérée ou elle a été insérée puis mise à jour.|  
|__$is_winner|**bit**|Indique si la ligne dans cette table était le vainqueur du conflit, ce qui signifie qu'elle a été appliquée au nœud local.|  
|__$pre_version|**varbinary (32)**|Version de la base de données d'où provient la modification conflictuelle.|  
|__$reason_code|**int**|Code de résolution du conflit. Peut avoir l'une des valeurs suivantes :<br /><br /> 0<br /><br /> 1<br /><br /> 2<br /><br /> <br /><br /> Pour plus d’informations, consultez **__ $reason_text**.|  
|__$reason_text|**nvarchar (720)**|Résolution du conflit. Peut avoir l'une des valeurs suivantes :<br /><br /> Résolu (1)<br /><br /> Non résolu (2)<br /><br /> Inconnu (0)|  
|__$update_bitmap|**varbinary (** *n* **)** . La taille varie selon le contenu.|Bitmap qui indique quelles colonnes ont été mises à jour en cas de conflit mise à jour-mise à jour.|  
|__$inserted_date|**datetime**|Date et heure d'insertion de la ligne en conflit dans cette table.|  
|__$row_id|**timestamp**|Valeur de version associée à la ligne source du conflit.|  
|__$change_id|**binary (8)**|Pour une ligne locale, cette valeur est égale au __$row_id de la ligne entrante qui a été en conflit avec la ligne locale. Cette valeur est NULL pour une ligne entrante.|  
|\<les noms de colonnes de table de base >|\<types de colonne de table de base >|La table en conflit contient une colonne pour chaque colonne dans la table de base.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
