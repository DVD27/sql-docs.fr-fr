---
title: Exécuter SQL Server avec ou sans réseau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 050986f4c78fc285e936b206c82faef90b89d75e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62810357"
---
# <a name="run-sql-server-with-or-without-a-network"></a>Exécuter SQL Server avec ou sans réseau
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut s’exécuter sur un réseau ou fonctionner sans réseau.  
  
## <a name="running-sql-server-on-a-network"></a>Exécution de SQL Server sur un réseau  
 Pour permettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de communiquer en réseau, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en cours d'exécution. Par défaut, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows démarre automatiquement le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégré. Pour savoir si le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est lancé, à l'invite de commandes tapez :  
  
 **NET START**  
  
 Si les services associés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ont été démarrés, les services suivants s’affichent dans la sortie **net start** :  
  
-   Analysis Services (MSSQLSERVER)  
  
-   SQL Server (MSSQLSERVER)  
  
-   Agent SQL Server (MSSQLSERVER)  
  
## <a name="running-sql-server-without-a-network"></a>Exécution de SQL Server sans réseau  
 Lors de l'exécution d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans réseau, il n'est pas nécessaire de démarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégré. Étant donné que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], le Gestionnaire de configuration SQL Server et les commandes **net start** et **net stop** sont toujours fonctionnels (même sans réseau), les procédures de démarrage et d’arrêt d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont identiques, qu’il s’agisse d’un fonctionnement en réseau ou en mode autonome.  
  
 Quand vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode autonome à partir d’une station cliente locale telle que **sqlcmd**, par exemple, vous ignorez le réseau et vous accédez directement à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’un canal de communication local. La différence entre un canal de communication local et un canal de communication réseau réside dans l'utilisation ou non d'un réseau. Les canaux de communication local et réseau établissent une connexion avec une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du canal standard (\\\\.\pipe\sql\query), sauf instructions contraires.  
  
 Quand vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale sans spécifier le nom d'un serveur, vous utilisez un canal de communication local. Lorsque vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale en spécifiant explicitement le nom d'un serveur, vous utilisez soit un canal réseau, soit un autre mécanisme de réseau IPC, comme IPX/SPX (Internetwork Packet Exchange/Sequenced Packet Exchange) (si vous avez configuré [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour une utilisation multi-réseau). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Comme un autonome ne prend pas en charge les canaux de communication réseau, vous devez **/** omettre l’argument _<Server_name>_ inutile lors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion à l’instance de à partir d’un client. Par exemple, pour vous connecter à une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de **osql**, tapez :  
  
 **osql/USA/p** _ \<SAPassword>_  
  
  
