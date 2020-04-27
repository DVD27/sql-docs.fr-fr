---
title: Propriétés du serveur (page Sécurité) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.security.f1
ms.assetid: b8a131c7-e7bd-4203-bf26-234f1ebfe622
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3a42d496a59f489238d270fcb6bb17f3e1ff6421
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62809003"
---
# <a name="server-properties-security-page"></a>Propriétés du serveur (page Sécurité)
  Utilisez cette page pour afficher ou modifier les options de sécurité de votre serveur.  
  
## <a name="server-authentication"></a>Authentification du serveur  
 **Mode d'authentification Windows**  
 Utilisez l'authentification Windows pour valider les tentatives de connexion. Si le mot de passe d’administrateur système **sa** est vide lorsque le mode de sécurité est modifié, le système demande à l’utilisateur d’entrer un mot de passe **sa** .  
  
> [!IMPORTANT]  
>  L'authentification Windows est plus sûre que l'authentification SQL Server. Lorsque c'est possible, utilisez l'authentification Windows.  
  
 **Mode d'authentification SQL Server et Windows**  
 Utilise le mode d'authentification mixte pour vérifier les tentatives de connexion, pour des raisons de compatibilité descendante avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le mot de passe d’administrateur système **sa** est vide lorsque le mode de sécurité est modifié, le système demande à l’utilisateur d’entrer un mot de passe **sa** .  
  
> [!NOTE]  
>  La modification de la configuration de la sécurité nécessite un redémarrage du service. Lorsque vous remplacez l'authentification SQL Server par le mode d'authentification SQL Server et Windows, le compte administrateur système n'est pas automatiquement activé. Pour utiliser le compte SA, exécutez [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) avec l’option ENABLE.  
  
## <a name="login-auditing"></a>Audit de connexion en cours  
 **Aucun**  
 Désactive l'audit de connexion en cours.  
  
 **Échecs de connexion uniquement**  
 Limite l'audit aux connexions qui ont échoué.  
  
 **Réussites de connexion uniquement**  
 Limite l'audit aux connexions qui ont réussi.  
  
 **Échecs et réussites de connexion**  
 Effectue l'audit de toutes les tentatives de connexion.  
  
> [!NOTE]  
>  La modification du niveau d'audit nécessite un redémarrage du service.  
  
## <a name="server-proxy-account"></a>Compte proxy du serveur  
 **Activer le compte proxy du serveur**  
 Active un compte destiné à être utilisé par **xp_cmdshell**. Les comptes proxy autorisent l'emprunt d'identité des connexions, rôles du serveur et rôles de la base de données lors de l'exécution d'une commande du système d'exploitation.  
  
> [!CAUTION]  
>  La connexion utilisée par le compte proxy du serveur doit avoir les privilèges minimum requis pour exécuter le travail prévu. Des privilèges excessifs pour le compte proxy pourraient être employés par un utilisateur malveillant pour compromettre la sécurité de votre système.  
  
 **Compte proxy**  
 Spécifiez le compte proxy utilisé.  
  
 **Mot de passe**  
 Spécifiez le mot de passe du compte proxy.  
  
## <a name="options"></a>Options  
 **Activer le suivi d'audit C2**  
 Les audits tentent tous d’accéder aux instructions et aux objets et de les enregistrer dans un fichier du répertoire \MSSQL\Data pour les instances par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou dans le répertoire \MSSQL$*nom_instance*\Data pour les instances nommées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [C2 audit mode (option de configuration de serveur)](c2-audit-mode-server-configuration-option.md).  
  
 **Chaînage des propriétés des bases de données croisées**  
 Sélectionnez cette option pour autoriser la base de données comme source ou cible d'une chaîne de propriétés de bases de données croisées. Pour plus d’informations, consultez [cross db ownership chaining (option de configuration de serveur)](cross-db-ownership-chaining-server-configuration-option.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
