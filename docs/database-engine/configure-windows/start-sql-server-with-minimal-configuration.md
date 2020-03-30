---
title: Démarrage de SQL Server avec une configuration minimale | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c919ad9202c99c7b010b6aee9c921e76784eb24
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "79027963"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Démarrage de SQL Server avec une configuration minimale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Si vous rencontrez des problèmes de configuration qui empêchent le démarrage du serveur, vous pouvez démarrer une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’option de démarrage en configuration minimale. Il s’agit de l’option de démarrage **-f**. Le démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server avec une configuration minimale fait automatiquement passer le serveur en mode mono-utilisateur.  
  
 Lorsque vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode configuration minimale, notez les éléments suivants :  
  
-   Un seul utilisateur peut se connecter et le processus `CHECKPOINT` n’est pas exécuté.  
  
-   L'accès à distance et la lecture anticipée sont désactivés.  
  
-   Les procédures stockées de démarrage ne sont pas exécutées.  

-   `tempdb` est configuré à la plus petite taille possible.

-   L’audit sera désactivé, mais la DDL d’audit peut toujours être émise. Dans la pratique, **-m** doit suffire dans la plupart des cas nécessitant une reconfiguration de l’audit SQL Server. Pour plus d’informations sur la sécurité dans la configuration de l’audit, consultez [Audit dans SQL Server](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd392015(v=sql.100)#security).
  
 N'oubliez pas ensuite de revenir à l'option de démarrage appropriée, d'arrêter le serveur, puis de le redémarrer.  
  
> [!IMPORTANT]  
>  Utilisez l’utilitaire **sqlcmd** et la connexion administrateur dédiée (DAC) pour vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous utilisez une connexion par défaut, arrêtez le service SQL Server Agent avant de vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode de configuration minimale. Sinon, le service SQL Server Agent utilise la connexion et bloque votre connexion à SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](https://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)   
 [Connexion de diagnostic pour les administrateurs de base de données](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)   
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  
