---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 79b6637bcfa0c3484de5d4438c48abbec35e40d5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68056639"
---
# <a name="mssqlserver_21898"></a>MSSQLSERVER_21898
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|21898|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21898|  
|Texte du message|Le serveur de publication '%s' utilise la base de données de distribution '%s' et non '%s', requise pour héberger la base de données de publication '%s'. Exécutez **sp_changedistpublisher** sur le serveur de distribution '%s' pour remplacer la base de données du serveur de distribution utilisée par le serveur de publication par '%s'.|  
  
## <a name="explanation"></a>Explication  
**sp_validate_redirected_publisher** interroge msdb.dbo.MSdistpublishers sur le serveur de distribution local pour vérifier que la base de données de distribution utilisée par le nouveau serveur de publication est la même que la base de données de distribution utilisée par le serveur de publication d’origine. Cette erreur est retournée lorsque ces bases de données diffèrent, faisant du serveur de publication un hôte incorrect pour la base de données du serveur de publication.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez la procédure stockée **sp_changedistpublisher** pour remplacer la base de données de distribution du nouveau serveur de publication et utiliser celle utilisée par le serveur de publication d’origine.  
  
> [!NOTE]  
> L’exécution de **sp_changedistpublisher** résout le problème si la base de données de distribution incorrecte a été configurée quand **sp_adddistpublisher** a été exécuté sur le serveur de distribution pour le serveur de publication. Toutefois, si le serveur de publication distant possède des publications existantes provenant d'une autre base de données de publication qui utilisent la base de données de distribution identifiée, cette modification n'est pas appropriée. La réplication utilisant la base de données de distribution nommée doit être systématiquement supprimée puis rétablie à l’aide de la base de données de distribution d’origine du serveur de publication pour que le nouveau serveur de publication fonctionne comme un hôte approprié.  
  
