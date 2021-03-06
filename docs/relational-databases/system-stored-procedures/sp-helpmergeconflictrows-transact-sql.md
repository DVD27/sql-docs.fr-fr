---
title: sp_helpmergeconflictrows (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
author: stevestein
ms.author: sstein
ms.openlocfilehash: b72a821c56f35e1ea7f3542b5746c234012c2da0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68137773"
---
# <a name="sphelpmergeconflictrows-transact-sql"></a>sp_helpmergeconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie les lignes de la table de conflits spécifiée. Cette procédure stockée est exécutée sur l'ordinateur qui héberge la table de conflits.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergeconflictrows [ [ @publication = ] 'publication' ]  
        , [ @conflict_table = ] 'conflict_table'  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publsher_db' ]   
    [ , [ @logical_record_conflicts = ] logical_record_conflicts ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, avec une valeur par défaut **%** . Si la publication est spécifiée, tous les conflits qualifiés par la publication sont renvoyés. Par exemple, si le **MSmerge_conflict_Customers** table a des lignes de conflits pour les **WA** et le **autorité de certification** publications, en passant un nom de publication **autorité de certification**  récupère les conflits qui se rapportent à la **autorité de certification** publication.  
  
`[ @conflict_table = ] 'conflict_table'` Est le nom de la table de conflits. *conflict_table* est **sysname**, sans valeur par défaut. Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures, les tables de conflits sont nommés en utilisant les noms de format avec **MSmerge_conflict\__publication\_article_** , avec une table pour chaque article publié.  
  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données du serveur de publication. *publisher_db* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @logical_record_conflicts = ] logical_record_conflicts` Indique si le jeu de résultats contient des informations sur les conflits d’enregistrement logique. *logical_record_conflicts* est **int**, valeur par défaut est 0. **1** signifie que les informations de conflit d’enregistrement logique sont retournées.  
  
## <a name="result-sets"></a>Jeux de résultats  
 **sp_helpmergeconflictrows** renvoie un jeu de résultats composé de la structure de table de base et de ces colonnes supplémentaires.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar(255)**|Origine du conflit.|  
|**conflict_type**|**int**|Code indiquant le type de conflit :<br /><br /> **1** = conflit mise à jour : Le conflit est détecté au niveau des lignes.<br /><br /> **2** = conflit de mise à jour de colonne : Le conflit est détecté au niveau des colonnes.<br /><br /> **3** = conflit de mise à jour Delete Wins : La suppression gagne le conflit.<br /><br /> **4** = conflit de suppression / mise à jour : Le rowguid supprimé qui perd le conflit est enregistré dans cette table.<br /><br /> **5** = échouée de l’insertion du téléchargement : L’insertion provenant de l’abonné n’a pas pu être appliquée sur le serveur de publication.<br /><br /> **6** = échouée de l’insertion du téléchargement : L’insertion provenant du serveur de publication n’a pas pu être appliquée sur l’abonné.<br /><br /> **7** = échouée de la suppression du téléchargement : La suppression appliquée à l’abonné n’a pas pu être téléchargée vers le serveur de publication.<br /><br /> **8** = échouée de la suppression du téléchargement : La suppression appliquée au serveur de publication n’a pas pu être téléchargée à l’abonné.<br /><br /> **9** = mise à jour de téléchargement a échoué : La mise à jour à l’abonné n’a pas pu être appliquée sur le serveur de publication.<br /><br /> **10** = mise à jour de téléchargement a échoué : La mise à jour au serveur de publication n’a pas pu être appliquée à l’abonné.<br /><br /> **12** = suppression / de mise à jour enregistrement logique : L’enregistrement logique supprimé qui perd le conflit est enregistré dans cette table.<br /><br /> **13** = enregistrement logique conflit insertion mise à jour : Insérer un conflits d’enregistrement logique avec une mise à jour.<br /><br /> **14** = conflit de mise à jour / suppression d’enregistrement logique : L’enregistrement logique mis à jour qui perd le conflit est enregistré dans cette table.|  
|**reason_code**|**int**|Code d'erreur pouvant dépendre du contexte.|  
|**reason_text**|**varchar(720)**|Description de l'erreur qui peut dépendre du contexte.|  
|**pubid**|**uniqueidentifier**|Identificateur de publication.|  
|**MSrepl_create_time**|**datetime**|Moment où l'information sur les conflits a été ajoutée.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergeconflictrows** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe et le **replmonitor** du rôle dans la base de données de distribution peuvent exécuter **sp_helpmergeconflictrows**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher les informations relatives aux conflits pour les Publications de fusion &#40;programmation Transact-SQL&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
