---
title: Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 59e3ababcebaf07ee953b3faedc0590db8b9bfec
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84952709"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Configurer la messagerie de l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données
  Cette rubrique explique comment configurer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour utiliser la messagerie de base de données pour envoyer une notification et des alertes dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Avant de commencer :**  
  
-   [Composants requis](#Prerequisites)  
  
-   [Sécurité](#Security)  
  
-   [Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données, à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
-   [Tâches de suivi](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
  
-   Activer la messagerie de base de données.  
  
-   Créer un compte de messagerie de base de données pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser.  
  
-   Créer un profil de messagerie de base de données pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à utiliser, et ajouter l'utilisateur au rôle **DatabaseMailUserRole** de la base de données **msdb** .  
  
-   Définir le profil comme profil par défaut pour la base de données **msdb** .  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 L'utilisateur qui crée les comptes de profils et exécute des procédures stockées doit être membre du rôle serveur fixe sysadmin.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour configurer l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données**  
  
-   Dans l'Explorateur d'objets, développez une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
-   Cliquez sur **Système d'alerte**.  
  
-   Sélectionnez **Activer le profil de messagerie**.  
  
-   Dans la liste **Système de messagerie** , choisissez **Database Mail**.  
  
-   Dans la liste **Profil de la messagerie**, sélectionnez un profil de messagerie pour la messagerie de base de données.  
  
-   Redémarrez l'Agent SQL Server.  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> Tâches de suivi  
 Les tâches suivantes sont nécessaires pour terminer la configuration de l'Agent pour envoyer des alertes et des notifications.  
  
-   [Alertes](../../ssms/agent/alerts.md)  
  
     Les alertes peuvent être configurées pour notifier à un opérateur une situation du système d'exploitation ou un événement de base de données particuliers.  
  
-   [Opérateurs](../../ssms/agent/operators.md)  
  
     Les opérateurs sont des alias pour les personnes ou les groupes qui peuvent recevoir une notification électronique  
  
  
