---
title: Sécurité de l’agent &lt;nom_agent&gt; | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75d4cccdb867716cf16490b4662edec4d5856fe6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85016780"
---
# <a name="ltagentnamegt-agent-security"></a>Sécurité de l’agent &lt;nom_agent&gt;
  La page sécurité de l' ** \<AgentName> agent** vous permet de spécifier les comptes sous lesquels l’agent de distribution (pour la réplication transactionnelle et d’instantané) ou agent de fusion (pour la réplication de fusion) s’exécutent et se connectent aux ordinateurs dans une topologie de réplication. Pour plus d’informations sur les autorisations exigées par les agents et les bonnes pratiques en matière de sécurité de la réplication, consultez [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md) et [Bonnes pratiques en matière de sécurité de la réplication](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Options  
 Cliquez sur le bouton de propriétés ( **...** ) dans la ligne de chaque Abonné pour accéder à la boîte de dialogue **Sécurité de l'Agent de distribution** ou **Sécurité de l'Agent de fusion** . Cliquez sur **Aide** dans la boîte de dialogue qui s'affiche pour fournir plus d'informations sur les autorisations indispensables pour les comptes utilisés par les agents.  
  
 Après avoir entré les paramètres dans l'une des boîtes de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agent de l'Abonné**  
 Nom de chaque Abonné.  
  
 **Connexion au serveur de distribution**  
 S'affiche pour les réplications d'instantané et transactionnelle. Le contexte dans lequel la connexion au serveur de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par émission de type push, la connexion locale est la connexion au serveur de distribution. par conséquent, ce champ affiche toujours : **emprunter l’identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '** pour les abonnements envoyés.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d’une connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le champ affiche l’un des éléments suivants : **utiliser la connexion' \<Login> '**, emprunter l' **identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion au serveur de publication et serveur de distribution**  
 S'affiche pour la réplication de fusion. Le contexte des connexions aux serveurs de publication et de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par émission de type push, la connexion locale est la connexion au serveur de publication et au serveur de distribution. par conséquent, ce champ affiche toujours : **emprunter l’identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '** pour les abonnements envoyés.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ affiche l’un des éléments suivants : **utiliser la connexion' \<Login> '**, emprunter l' **identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion à l'Abonné**  
 Le contexte dans lequel la connexion à l'abonné s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par extraction, la connexion locale est la connexion à l’abonné. ce champ affiche donc toujours : **emprunter l’identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '** pour les abonnements envoyés.  
  
-   Pour les abonnements par émission de données, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ affiche l’un des éléments suivants : **utiliser la connexion' \<Login> '**, emprunter l' **identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md)   
 [Afficher et modifier les propriétés d’un abonnement par émission de données](view-and-modify-push-subscription-properties.md)   
 [Gérer les connexions et les mots de passe dans la réplication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md)   
 [Sécurité Réplication SQL Server](security/view-and-modify-replication-security-settings.md)  
  
  
