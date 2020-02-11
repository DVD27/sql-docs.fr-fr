---
title: Se connecter à une instance de SQL Server (via l’invite de commandes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ec0250a6928dc2dd7b2d1881fbede89eb0aa51f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62781776"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>Se connecter à une instance de SQL Server (via l'invite de commandes)
  Cette rubrique explique comment tester la connectivité à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avec l'utilitaire **sqlcmd** .  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a>Pour se connecter à l’instance par défaut de SQL Server  
  
1.  À partir d'une invite de commandes, saisissez la commande suivante afin de vérifier vos informations d'identification par l'authentification Windows :  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a>Pour se connecter à une instance nommée de SQL Server  
  
1.  À partir d'une invite de commandes, saisissez la commande suivante afin de vérifier vos informations d'identification par l'authentification Windows :  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Utilitaire osql](../../tools/osql-utility.md)  
  
  
