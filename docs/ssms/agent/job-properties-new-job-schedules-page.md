---
title: Propriétés du travail - Nouveau travail (page Planifications)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b8cb5f6fafa2ef48b3aea31e916480e712f477af
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75242257"
---
# <a name="job-properties---new-job-schedules-page"></a>Propriétés du travail - Nouveau travail (page Planifications)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et organiser des planifications pour un travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Liste des planifications**  
Affiche la liste des planifications pour ce travail.  
  
**Nouveau**  
Créez une nouvelle planification. Une fois que vous avez créé la planification, celle-ci est ajoutée au travail.  
  
**Choisir**  
Sélectionnez une planification parmi les planifications existantes. Étant donné qu'un travail et une planification doivent appartenir à la même personne, cette option vous permet uniquement d'accéder aux planifications dont vous êtes le propriétaire.  
  
**Modifier**  
Modifiez la planification sélectionnée pour changer les propriétés de planification du travail.  
  
**Remove**  
Supprimez la planification sélectionnée du travail. Si la planification en question n'est pas utilisée par un autre travail, elle est supprimée de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
  
