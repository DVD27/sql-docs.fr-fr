---
title: fournisseur WMI pour Gestion de l'ordinateur
description: Découvrez comment le fournisseur WMI pour la gestion de la configuration utilise WMI pour gérer les services, les alias de serveur et les paramètres réseau client/serveur dans SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4795ee1d456e5f4b823c24fc1ad48e81c9d6541e
ms.sourcegitcommit: bf5e9cb3a2caa25d0a37f401b3806b7baa5adea8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85295432"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Présentation du fournisseur WMI pour la gestion de la configuration
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fournit le fournisseur WMI pour la gestion de la configuration. Cela vous permet d'utiliser WMI (Windows Management Instrumentation) pour gérer les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les paramètres réseau client et serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que les alias de serveur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les services, les paramètres réseau et les alias sont représentés par des objets WMI dans l’espace de noms root\Microsoft\SqlServer\ComputerManagement*nn* de l’ordinateur. Une fois qu'une connexion est établie avec le fournisseur WMI sur l'ordinateur spécifié, les services, paramètres réseau et alias peuvent être interrogés à l'aide du langage WQL ou d'un langage de script.  
  
 Le fournisseur WMI est un fournisseur d'instances. Il fournit des instances des [classes WMI](../../relational-databases/wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) et prend en charge les opérations asynchrones suivantes.  
  
 Récupération d'instance  
 Récupération d'une instance spécifique d'un type de classe.  
  
 Énumération  
 Énumération de toutes les instances d'un type de classe.  
  
 Modification  
 Modification d'une instance spécifique d'un type de classe.  
  
 Les classes ont des méthodes qui autorisent la modification de leurs propriétés.  
  
 Suppression  
 Suppression d'une instance spécifique d'un type de classe.  
  
 Traitement des requêtes  
 Énumération des instances d'un type de classe en fonction d'un filtre.  
  
 Pour obtenir des exemples d’applications de gestion utilisant le fournisseur WMI pour la gestion de la configuration, consultez [utilisation des langages WQL et de script avec le fournisseur WMI pour la gestion de la configuration](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Pour plus d’informations sur la programmation d’applications de gestion à l’aide du fournisseur WMI, consultez la documentation WMI dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] Kit de développement logiciel (SDK) .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du fournisseur WMI pour la gestion de la configuration](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [Utilisation des langages WQL et de script avec le fournisseur WMI pour la gestion de configuration](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
