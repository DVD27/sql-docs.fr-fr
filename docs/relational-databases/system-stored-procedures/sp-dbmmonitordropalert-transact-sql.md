---
title: sp_dbmmonitordropalert (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitordropalert_TSQL
- sp_dbmmonitordropalert
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitordropalert
ms.assetid: fe4a134b-25bf-464e-a5c4-358de215b65a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4776e043505c787e74c9cecf766325d189c4f702
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108122"
---
# <a name="spdbmmonitordropalert-transact-sql"></a>sp_dbmmonitordropalert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime l'avertissement associé à une mesure de performance spécifiée, en attribuant au seuil la valeur NULL.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dbmmonitordropalert database_name   
    [ , alert_id ]   
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Spécifie la base de données pour laquelle supprimer le seuil d'avertissement spécifié.  
  
 *alert_id*  
 Entier qui identifie l'avertissement à supprimer. Si cet argument est omis, tous les avertissements associés à la base de données sont supprimés. Pour supprimer l'avertissement associé à une mesure de performance spécifique, définissez l'une des valeurs suivantes :  
  
|Value|Mesure de performance|Seuil d'avertissement|  
|-----------|------------------------|-----------------------|  
|1|Transaction non envoyée la plus ancienne|Spécifie le nombre de minutes de transactions pouvant s'accumuler dans la file d'attente d'envoi avant qu'un avertissement ne soit généré sur l'instance de serveur principal. Cet avertissement permet de mesurer le risque de perte de données en termes de temps et s'avère particulièrement approprié en mode hautes performances. Toutefois, l'avertissement est également approprié en mode haute sécurité lorsque la mise en miroir est interrompue ou suspendue en raison de la déconnexion des partenaires.|  
|2|Journal non envoyé|Spécifie la quantité de kilo-octets (Ko) de journal non envoyé qui génère un avertissement sur l'instance de serveur principal. Cet avertissement permet de mesurer le risque de perte de données en termes de Ko et s’avère particulièrement approprié pour le mode hautes performances. Toutefois, l'avertissement est également approprié en mode haute sécurité lorsque la mise en miroir est interrompue ou suspendue en raison de la déconnexion des partenaires.|  
|3|Journal non restauré|Spécifie la quantité de Ko de journal non restauré qui génère un avertissement sur l'instance de serveur miroir. Cet avertissement permet de mesurer le temps de basculement. Le*temps de basculement* est principalement constitué du temps nécessaire à l'ancien serveur miroir pour restaurer par progression tout journal demeuré dans sa file d'attente de restauration par progression et d'un court laps de temps supplémentaire.|  
|4|Charge de validation par le serveur miroir|Spécifie le nombre de millisecondes de délai moyen par transaction qui sont tolérés avant qu'un avertissement soit généré sur le serveur principal. Ce délai correspond au temps de traitement pendant lequel l'instance de serveur principal attend que l'instance de serveur miroir écrive l'enregistrement du journal de transaction dans la file d'attente de restauration par progression. Cette valeur est utile uniquement en mode haute sécurité.|  
|5\.|Période de rétention|Métadonnées qui déterminent la durée de conservation des lignes dans la table de l'état des mises en miroir de base de données.|  
  
> [!NOTE]  
>  Cette procédure supprime les seuils d’avertissement, indépendamment de si elles ont été spécifiées à l’aide de **sp_dbmmonitorchangealert** ou le moniteur de mise en miroir de base de données.  
  
 Pour plus d’informations sur les ID d’événement correspondant aux avertissements, consultez [utilisez les seuils d’avertissement et d’alertes sur des métriques de performances de mise en miroir &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Aucun  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la valeur de la période de rétention de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_dbmmonitordropalert AdventureWorks2012, 5;  
```  
  
 L'exemple suivant supprime tous les seuils d'avertissement et la période de rétention de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_dbmmonitordropalert AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)  
  
  
