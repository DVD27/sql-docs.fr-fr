---
title: Serveur de distribution | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replicationutilities.selectdistributor.f1
ms.assetid: 787f0e9c-09dd-438a-bc04-5b8f99c127b8
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 22770207bd0c6da38f88680313d8da433e1da286
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768518"
---
# <a name="distributor"></a>Serveur de distribution
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  La page **Serveur de distribution** figure dans l'Assistant Configuration de la distribution et l'Assistant Nouvelle publication. Le serveur de distribution est le serveur qui contient la base de données de distribution et qui stocke les métadonnées et les données d'historique de tous les types de réplications. Le serveur de distribution stocke également les transactions de la réplication transactionnelle. Le serveur de distribution peut correspondre au serveur de publication (serveur de distribution) ou à un serveur distinct du serveur de publication (serveur de distribution distant). Le rôle du serveur de distribution varie en fonction du type de réplication implémenté. En règle générale, il joue un rôle beaucoup plus important pour la réplication transactionnelle que pour la réplication de fusion et la réplication d'instantané. La réplication de fusion et la réplication d'instantané utilisent un serveur de distribution local, mais la réplication transactionnelle sur un système très occupé peut tirer parti d'un serveur de distribution distant.  
  
 Le serveur de distribution utilise les ressources supplémentaires suivantes sur le serveur sur lequel il se trouve :  
  
-   espace disque supplémentaire si les fichiers d'instantané de la publication y sont stockés (ce qui est généralement le cas) ;  
  
-   espace disque supplémentaire pour stocker la base de données de distribution ;  
  
-   augmentation de l'utilisation du processeur par les agents de réplication pour les abonnements par envoi de données (push) exécutés sur le serveur de distribution.  
  
 Le serveur que vous sélectionnez comme serveur de distribution doit avoir un espace disque suffisant et un processeur suffisamment puissant pour prendre en charge la réplication et toutes les autres activités basées sur ce serveur.  
  
## <a name="options"></a>Options  
 **'\<Nom_serveur>' agit comme son propre serveur de distribution ; SQL Server crée une base de données de distribution et un journal**  
 Sélectionnez cette option pour configurer le serveur auquel vous êtes connecté comme serveur de distribution.  
  
 **Utiliser le serveur suivant comme serveur de distribution (le serveur que vous sélectionnez doit déjà être configuré en tant que serveur de distribution)**  
 Sélectionnez cette option et cliquez sur le nom d'un serveur en dessous pour configurer un autre serveur comme serveur de distribution.  
  
 **Ajouter**  
 Si le serveur que vous voulez utiliser comme serveur de distribution ne figure pas dans la liste, cliquez sur **Ajouter** pour identifier le serveur et l'ajouter à la liste.  
  
> [!NOTE]  
>  Pour utiliser un serveur distant comme serveur de distribution, le serveur distant doit être déjà configuré comme serveur de distribution. Le serveur par rapport auquel cet Assistant est exécuté doit être activé comme serveur de publication sur ce serveur de distribution.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
