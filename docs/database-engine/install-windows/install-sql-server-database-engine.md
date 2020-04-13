---
title: Installer le moteur de base de données SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 91a8515417d25c2ef9f23d1698811a5f872227db
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664271"
---
# <a name="install-sql-server-database-engine"></a>Installer le moteur de base de données SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

## <a name="overview"></a>Vue d’ensemble
Le composant [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est le service de base pour le stockage, le traitement et la protection des données. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] fournit un accès contrôlé et un traitement transactionnel rapide qui répondent aux exigences des applications les plus gourmandes en termes de données dans votre entreprise.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge jusqu’à 50 instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur un seul ordinateur. Pour créer une installation par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Installer SQL Server avec l’Assistant Installation &#40;programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
>[!IMPORTANT]
>Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.  

## <a name="features"></a>Fonctionnalités
Les fonctionnalités suivantes sont installées quand vous sélectionnez **Moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** dans la page Composants à installer de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [Réplication SQL Server](../../relational-databases/replication/sql-server-replication.md) (composant facultatif)  

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions" 
-   [Machine Learning Services](../../machine-learning/install/sql-machine-learning-services-windows-install.md) (R et Python) et [Extensions de langage](../..//language-extensions/install/install-sql-server-language-extensions-on-windows.md) (Java) - composant facultatif
::: moniker-end

::: monikerRange=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
-   [Machine Learning Services (dans la base de données)](../../machine-learning/install/sql-machine-learning-services-windows-install.md) (R et Python) - composant facultatif
::: moniker-end

::: monikerRange=">=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions"
-   [R Services (dans la base de données)](../../machine-learning/install/sql-r-services-windows-install.md) - composant facultatif
::: moniker-end

-   Recherche en texte intégral (composant facultatif)  
  
-   Data Quality Services est un composant facultatif  
  
    > [!NOTE]  
    >  Dans cette version, le fait de cocher la case **Data Quality Services** au moment de l’installation n’installe pas le serveur Data Quality Services (DQS). Vous devrez procéder à des étapes supplémentaires après l'installation pour installer le serveur DQS. Pour plus d’informations, consultez [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
    
- [Service de requête PolyBase pour données externes](../../relational-databases/polybase/polybase-guide.md) (composant facultatif). À compter de SQL Server 2019, le connecteur Java pour les sources de données HDFS est également disponible.

  
 Les fonctionnalités supplémentaires suivantes sont des options pour un grand nombre de scénarios utilisateur classiques :  
  
-   Data Quality Client
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]
-   Composants de connectivité
-   Modèles de programmation
-   Outils d'administration
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]
-   Composants de documentation  
  

> [!NOTE]  
>  Par défaut, les exemples de bases de données et les exemples de code ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour installer les exemples de bases de données et les exemples de code, consultez [Exemples Microsoft SQL Server](../../sample/microsoft-sql-server-samples.md). Pour des exemples plus anciens, consultez le [CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843).  

  
## <a name="see-also"></a>Voir aussi  
 [Éditions et fonctionnalités prises en charge de SQL Server 2017](~/sql-server/editions-and-components-of-sql-server-2017.md)   
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Solutions haute disponibilité &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Mettre à niveau SQL Server à l’aide de l’Assistant Installation &#40;Installation&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
