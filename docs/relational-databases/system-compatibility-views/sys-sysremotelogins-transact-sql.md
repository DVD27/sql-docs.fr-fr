---
title: sys. sysremotelogins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysremotelogins
- sysremotelogins_TSQL
- sys.sysremotelogins
- sys.sysremotelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysremotelogins system table
- sys.sysremotelogins compatibility view
ms.assetid: b7ffcfa6-aed8-41d4-8b70-845439ab813d
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c51ccd657c8a7c5f07bdaf836ba3e279e81c590
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68018136"
---
# <a name="syssysremotelogins-transact-sql"></a>sys.sysremotelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque utilisateur distant autorisé à appeler des procédures stockées distantes sur une instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**remoteserverid**|**smallint**|ID du serveur distant.|  
|**remoteusername**|**sysname**|Nom de connexion de l'utilisateur sur un serveur distant.|  
|**statut**|**smallint**|Retourne 0.|  
|**sid**|**varbinary (85)**|ID de sécurité de l'utilisateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|  
|**changedate**|**datetime**|Date et heure de l'ajout de l'utilisateur distant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de tables système à des vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
