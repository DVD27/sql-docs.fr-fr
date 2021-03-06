---
title: Connexion à SQL Server pour la suppression | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: acb755f8cc1e425e38714013511948f7b5b4c580
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62836859"
---
# <a name="connection-to-sql-server-for-delete"></a>Connexion à SQL Server pour la suppression
  Lorsqu’une connexion sans rôle de base de données qui inclut l’autorisation d’accès en écriture (par exemple le rôle **db_owner**) à la base de données MSXDBCDC tente de supprimer une instance Oracle CDC, la boîte de dialogue Connexion à SQL Server s’affiche.  
  
 Dans cette boîte de dialogue, vous devez entrer les informations d’identification pour une connexion qui a l’autorisation d’accès en écriture à la base de données MSXDBCDC, notamment le rôle de base de données **db_owner** pour supprimer l’instance Oracle CDC.  
  
 Dans la boîte de dialogue Connexion à SQL Server, entrez les informations suivantes :  
  
 **Nom de serveur**  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Authentification**  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**  
  
-   **Authentification SQL Server** : si vous sélectionnez cette option, vous devez taper **l’Identifiant** et le **Mot de passe** de l’utilisateur dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
 **Options**  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion** : tapez le délai (en secondes) pendant lequel le programme attend la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de générer une erreur de délai d’expiration. La valeur par défaut est **15**.  
  
-   **Délai d’exécution** : tapez le délai (en secondes) pendant lequel le programme attend la fin d’exécution de la commande SQL avant de générer une erreur de délai d’expiration. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion** : sélectionnez **Chiffrer la connexion** pour que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] établie soit chiffrée dans un souci de protection des données personnelles.  
  
-   **Avancé** : Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de connexion SQL Server requises pour le service de capture de données modifiées](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
