---
title: Instructions d’utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 5f9a94c4-854b-4577-a8b1-7142f19904e3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ae552c12c3d4773d6a05a6d61c7644eb245b68ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094994"
---
# <a name="guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm"></a>Instructions d'utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010
  Cette rubrique récapitule la disponibilité des fonctionnalités selon les versions et les éditions du logiciel utilisé. Elle décrit également la configuration requise pour l'installation de SharePoint 2010 avec des fonctionnalités spécifiques de SQL Server. Pour plus d’informations sur SharePoint 2013, consultez [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
 Dans cette rubrique :  
  
-   [Configuration requise de général SharePoint 2010](#bkmk_generalsharepoint)  
  
-   [SharePoint 2010 Service Pack 1 (SP1)](#bkmk_sp1)  
  
-   [Prise en charge des éditions de SharePoint et des fonctionnalités BI](#bkmk_vers)  
  
-   [Outil de préparation des produits SharePoint 2010](#bkmk_prereq)  
  
-   [Exigences et suggestions pour l’exécution de l’installation de SharePoint](#bkmk_install)  
  
##  <a name="bkmk_generalsharepoint"></a> Configuration requise de général SharePoint 2010  
  
-   Les produits SharePoint 2010 n'existent qu'en version 64 bits. Si une installation 32 bits d'une version précédente de SharePoint et de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installée en mode intégré SharePoint, vous ne pourrez pas effectuer de mise à niveau vers SharePoint 2010. Pour plus d'informations, consultez la documentation de SharePoint.  
  
-   les Reporting Services incluent un complément pour les produits SharePoint. Les configurations prises en charge pour le complément et le serveur de rapports sont disponibles à un niveau de granularité plus fin que ce qui est indiqué ici. Pour plus d’informations, consultez [pris en charge les combinaisons de SharePoint et le serveur Reporting Services et complément &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   Les outils de développement SharePoint ne prennent en charge qu'une configuration autonome SharePoint.  Pour plus d’informations, consultez la documentation de SharePoint : [Configuration requise pour développer des Solutions SharePoint](https://msdn.microsoft.com/library/ee231582.aspx).  
  
##  <a name="bkmk_vers"></a> Prise en charge des éditions de SharePoint et des fonctionnalités BI  
 Certaines fonctionnalités de Business Intelligence [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sont prises en charge uniquement sur les éditions spécifiques des produits SharePoint.  
  
|Fonctionnalités prises en charge|Produit SharePoint|  
|------------------------|------------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], une fonctionnalité de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Alertes de données.<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|[!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.|  
|Affichage du rapport général [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et intégration des fonctionnalités avec SharePoint.|[!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Éditions Standard et Enterprise.<br /><br /> [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] .|  
  
 Pour plus d’informations, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473).  
  
##  <a name="bkmk_sp1"></a> SharePoint 2010 Service Pack 1 (SP1)  
 Il est recommandé de mettre à jour votre installation de SharePoint 2010 avec le Service Pack 1 (SP1) de SharePoint 2010. SharePoint SP1 est requis dans les cas suivants :  
  
-   Vous souhaitez utiliser la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] du moteur de base de données pour les bases de données de contenu SharePoint ou les bases de données de catalogue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Vous souhaitez utiliser [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 Une des raisons pour lesquelles SP1 est requise pour les installations de SharePoint en cours d’exécution avec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] est la fonctionnalité du moteur de base de données **sp_dboption**, qui a été déconseillée dans une version précédente, il n’est plus disponible dans le [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] mise en production. Pour plus d’informations, consultez [fonctionnalités de moteur de base de données supprimées dans SQL Server 2014](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)  
  
### <a name="sharepoint-2010-sp1-installation-guidance"></a>Aide à l'installation de SharePoint 2010 SP1  
 [Télécharger SharePoint Server 2010 SP1](https://go.microsoft.com/fwlink/?LinkID=219697) et appliquez-le sur tous les serveurs de la batterie de serveurs.  
  
> [!NOTE]  
>  Sur une batterie de serveurs existante, vous devez utiliser une des opérations suivantes **supplémentaires** mise à niveau des étapes à effectuer de SharePoint SP1. Pour plus d’informations, consultez [problèmes connus lorsque vous installez Office 2010 SP1 et SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126) et [Description de SharePoint Server 2010 SP1](https://support.microsoft.com/kb/2460045):  
  
-   **Assistant Configuration des produits SharePoint :** Exécutez l’Assistant pour terminer la configuration et la mise à niveau SP1.  
  
-   **Effectuez la mise à niveau avec psconfig :** Exécutez la commande `psconfig -upgrade` pour effectuer la mise à niveau SP1  
  
 Pour plus d’informations, consultez la section « mise à niveau » de [(SharePoint Server 2010)](https://technet.microsoft.com/library/cc263093.aspx) et [centre de ressources : Mises à jour pour les produits SharePoint 2010](https://technet.microsoft.com/sharepoint/ff800847.aspx)  
  
## <a name="sharepoint-installation-with-sql-server-bi-features"></a>Installation de SharePoint avec les fonctionnalités SQL Server BI  
  
###  <a name="bkmk_prereq"></a> Outil de préparation des produits SharePoint 2010  
 L'outil de préparation des produits SharePoint permet de recourir aux rôles de serveur dans le système d'exploitation et installe d'autres logiciels requis par une installation SharePoint. Le tableau suivant répertorie les étapes supplémentaires de la configuration du serveur pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Composant|Action|  
|---------------|------------|  
|composant logiciel enfichable Reporting Services|L'Outil de préparation des produits SharePoint 2010 installe la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] du complément Reporting Services. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] intègre une nouvelle version du complément qui est requise pour les fonctionnalités [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Le complément peut être téléchargé et installé à l'aide de l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de MSDN. Pour plus d’informations sur où obtenir la version actuelle du complément et comment l’installer, consultez [où trouver la macro complémentaire Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md) et [installer ou désinstaller Reporting Services Complément pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).|  
|Fournisseur OLE DB pour Analysis Services (MSOLAP)|SharePoint 2010 installe la version SQL Server 2008 du fournisseur OLE DB dans le cadre d'un déploiement Excel Services. Cette version ne prend pas en charge l'accès aux données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Vous devez installer les versions ultérieures du fournisseur sur les serveurs SharePoint qui prennent en charge les connexions de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Pour plus d’informations, consultez [installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)|  
|Services ADO.NET|SharePoint 2010 répertorie les services ADO.NET dans la liste des composants requis, mais le programme d'installation préalable ne procède pas à l'installation. Pour ajouter des services ADO.NET, vous devez procéder à l'installation manuelle. L'installation des services ADO.NET est obligatoire si vous souhaitez utiliser des listes SharePoint en tant que flux de données entrant de classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ou de rapports Reporting Services. Pour obtenir des instructions, consultez [installer ADO.NET Data Services pour prendre en charge les données exportations de flux des listes SharePoint](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).|  
  
###  <a name="bkmk_install"></a> Exigences et suggestions pour l’exécution de l’installation de SharePoint  
 Les fonctionnalités [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installées et leur ordre d'installation déterminent les niveaux d'intégration possibles avec SharePoint. Par exemple, alors qu'un certain niveau d'intégration de fonctionnalité est disponible via les Reporting Services sur un serveur SharePoint qui utilise une base de données intégrée, la plupart des scénarios d'intégration de fonctionnalité requièrent une installation de batterie de serveurs SharePoint, car seule une installation de serveurs fournit l'infrastructure requise pour certaines fonctionnalités de BI.  
  
 Une batterie de serveurs SharePoint peut être formée d'un seul serveur ou de plusieurs. Ce qui définit une batteri,e indépendamment d'une installation autonome, est la présence d'infrastructure supplémentaire, comme le Service d'émission de jetons Revendications vers Windows.  
  
 Une batterie de serveurs est activée lorsque vous choisissez la **batterie de serveurs** option dans le programme d’installation de SharePoint. Vous devez avoir une installation de batterie de serveurs si vous souhaitez utiliser [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint ou [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. L'installation autonome SharePoint est prise en charge et courante pour les environnements de développement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Toutefois, l'installation d'une batterie de serveurs SharePoint est recommandée pour un environnement de production.  
  
 ![GMNI_SetupUI_SharePoint2010InstallType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010installtype.gif "GMNI_SetupUI_SharePoint2010InstallType")  
  
 Une installation complète de serveur est également requise pour [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint ou le service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 ![GMNI_SetupUI_SharePoint2010ServerType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010servertype.gif "GMNI_SetupUI_SharePoint2010ServerType")  
  
 La dernière page de l'Assistant Installation vous invite à configurer la batterie et à configurer éventuellement une application Web et une collection de sites racine par défaut. La plupart des utilisateurs du programme d'installation suivent ce chemin d'installation. Si pour une raison quelconque vous ne configurez pas la batterie, vous pouvez utiliser l'option de configuration de batterie de serveurs dans l'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour la configurer.  
  
 Dans les versions précédentes, nous recommandions de ne pas configurer la batterie pour installer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] afin de raccourcir la procédure si vous utilisiez les options d'installation de SQL Server pour installer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint dans un état prêt à l'emploi. Dans cette version, cette approche est inutile. L'outil de configuration de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sert à paramétrer une batterie existante de manière à ce qu'elle utilise les paramètres recommandés d'une installation de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peut être installé dans une batterie de serveurs SharePoint existante. Vous pouvez installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou SharePoint dans n'importe quel ordre, mais la configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] varie selon la commande. Pour plus d’informations, consultez [ajouter un serveur de rapports supplémentaire à une batterie de serveurs &#40;SSRS Scale-out&#41; ](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) et [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 ![GMNI_SetupUI_DoNotConfigureMOSS](../../../2014/sql-server/install/media/gmni-setupui-donotconfiguremoss.gif "GMNI_SetupUI_DoNotConfigureMOSS")  
  
## <a name="see-also"></a>Voir aussi  
 [Installation et déploiement pour SharePoint Server 2010](https://technet.microsoft.com/sharepoint/ee518643.aspx)   
 [Plusieurs serveurs pour une batterie de serveurs à trois niveaux (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834)  
  
  
