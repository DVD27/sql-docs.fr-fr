---
title: Désigner un serveur de transfert d’événements (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 08c0de849f09fc557057500d5cfbd05af450997c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262530"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Designate an Events Forwarding Server (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment désigner un serveur auquel [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transfère les événements dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Notez que le transfert d'événements s'applique aux événements transférés entre serveurs, et non aux événements transférés entre instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hébergées sur un même ordinateur. Notez également qu'afin de recevoir les événements transférés, le serveur de gestion des alertes doit être une instance par défaut de SQL Server.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour désigner un serveur de transfert d'événements, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-designate-an-events-forwarding-server"></a>Pour désigner un serveur de transfert d'événements  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur depuis lequel vous souhaitez transférer des événements vers un autre serveur.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de SQL Server Agent -** _nom_serveur_, sous **Sélectionner une page**, sélectionnez **Avancé**.  
  
4.  Sous **Transfert d'événements SQL Server**, sélectionnez la case à cocher **Transférer les événements sur un autre serveur** .  
  
5.  Dans la liste **Serveur** , sélectionnez un serveur, puis, sous **Événements**, sélectionnez l'une des options suivantes :  
  
    -   Sélectionnez **Événements non gérés** pour ne transmettre que les événements qui n'ont pas été gérés par des alertes locales.  
  
    -   Sélectionnez **Tous les événements** pour transférer tous les événements, indépendamment de leur gestion par des alertes locales ou non.  
  
6.  Dans la liste **Si l'événement a une gravité au moins égale à** , cliquez sur le niveau de gravité auquel les événements sont transférés au serveur sélectionné.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
