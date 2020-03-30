---
title: Expiration du mot de passe de connexion SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 92a8452b586768e260c9bc378d06201cd2e67ed7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68021629"
---
# <a name="sql-server-login-password-expiration"></a>Expiration du mot de passe de connexion SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie si l'option Expiration du mot de passe est activée pour chaque connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est activée et si la version du système d'exploitation est antérieure à [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], un pirate peut régulièrement exploiter un mot de passe de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connu.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Nous vous recommandons de mettre à niveau le système d'exploitation vers [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas requise dans votre environnement, utilisez l'authentification Windows. Pour plus d’informations, consultez [Choisir un mode d’authentification](../../relational-databases/security/choose-an-authentication-mode.md).  
  
 Activez l'option Expiration du mot de passe pour toutes les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Utilisez [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) pour configurer la stratégie de mot de passe pour la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
