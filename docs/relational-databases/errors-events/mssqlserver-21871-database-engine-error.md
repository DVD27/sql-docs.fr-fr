---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fa8d7f1a92891cc2dcdabc431dcf97a1392201c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056700"
---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21871|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21871|  
|Texte du message|Le serveur de publication %s de la base de données %s n'a pas été redirigé.|  
  
## <a name="explanation"></a>Explication  
**sp_validate_replica_hosts_as_publishers** recherche dans la table MSredirected_publishers de la base de données de distribution une entrée pour le serveur de publication et la base de données du serveur de publication identifiés.  **sp_validate_replica_hosts_as_publishers** retourne l’erreur 21871 quand aucune entrée n’est trouvée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
**sp_validate_replica_hosts_as_publishers** est applicable uniquement aux serveurs de publication redirigés. Si la base de données du serveur de publication est membre d’un groupe de disponibilité, utilisez la procédure stockée **sp_redirect_publisher** pour associer le serveur de publication et la base de données du serveur de publication au nom de l’écouteur du groupe de disponibilité.  
  
