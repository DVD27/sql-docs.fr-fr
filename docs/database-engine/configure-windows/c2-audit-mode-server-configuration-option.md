---
title: C2 audit mode (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], C2 Audit Mode option
- C2 auditing
- C2 Audit Mode option
- recording attempts
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 52e39eda53e08a4267ac97faa3b691ffcd7acaad
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68013003"
---
# <a name="c2-audit-mode-server-configuration-option"></a>C2 audit mode (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Le mode d’audit C2 peut être configuré à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de l’option **c2 audit mode** dans **sp_configure**. La sélection de cette option configure le serveur pour qu'il enregistre les tentatives d'accès aux instructions et aux objets ayant réussi et ayant échoué. Ces informations peuvent vous aider à comprendre l'activité du système et à détecter les éventuelles violations de la stratégie de sécurité.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] La norme de sécurité C2 a été remplacée par la certification Critères communs. Voir [common criteria compliance enabled (option de configuration de serveur)](../../database-engine/configure-windows/common-criteria-compliance-enabled-server-configuration-option.md).  
  
## <a name="audit-log-file"></a>Fichier journal d'audit  
 Les données de mode d'audit C2 sont enregistrées dans un fichier dans le répertoire de données par défaut de l'instance. Si le fichier journal d’audit atteint sa taille maximale de 200 mégaoctets (Mo), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée un fichier, referme l’ancien et écrit tous les nouveaux enregistrements d’audit dans le nouveau fichier. Cette opération se poursuit jusqu’à la saturation du répertoire des données d'audit ou la désactivation de l'audit. Pour déterminer l'état d'une trace C2, interrogez l'affichage catalogue sys.traces.  
  
> [!IMPORTANT]  
>  Le mode d'audit C2 enregistre une grande quantité d'informations sur les événements dans le fichier journal, qui peut se remplir rapidement. Si le répertoire des données où sont enregistrés les journaux arrive à saturation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête de lui-même. Si l’audit est configuré pour démarrer automatiquement, vous devez soit redémarrer l’instance avec l’indicateur **-f** (pour ignorer l’audit), soit libérer de l’espace disque pour le journal d’audit.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="example"></a>Exemple  
 L'exemple suivant active le mode d'audit C2.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
