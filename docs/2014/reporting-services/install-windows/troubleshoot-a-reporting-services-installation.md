---
title: Résoudre les problèmes d’une Installation Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 447cab185ce02b83b25af160421391ed73bb7cf6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248339"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Dépanner une installation de Reporting Services
  Si vous ne parvenez pas à installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] suite à des erreurs qui se produisent durant l'installation, utilisez les instructions fournies dans cette rubrique pour étudier les conditions les plus susceptibles de provoquer des erreurs d'installation.  
  
 Pour plus d’informations concernant les problèmes avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez [Reporting Services SQL Server 2012 conseils, astuces et dépannage](http://go.microsoft.com/fwlink/?LinkId=221297)  
  
 Pour plus d'informations sur d'autres erreurs et problèmes liés à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez [Résoudre les problèmes et erreurs de SSRS.](http://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx)  
  
 Examinez les [notes de publication en ligne](http://go.microsoft.com/fwlink/?linkid=236893) si le problème que vous rencontrez est décrit dans les notes de mise à jour.  
  
 Cette rubrique contient les informations suivantes :  
  
-   [Vérifiez les journaux d’installation](#bkmk_setuplogs)  
  
-   [Vérifier les prérequis](#bkmk_prereq)  
  
-   [Problèmes liés aux installations en SharePoint Mode](#bkmk_tshoot_sharepoint)  
  
-   [Résoudre les problèmes avec les Installations en Mode natif](#bkmk_tshoot_native)  
  
-   [Ressources supplémentaires](#bkmk_additional)  
  
##  <a name="bkmk_setuplogs"></a> Vérification des journaux d'installation  
 Les erreurs d'installation sont enregistrées dans des fichiers journaux, dans le dossier **Program Files\Microsoft SQL Server\110\Setup Bootstrap\Log** . Un sous-dossier est créé chaque fois que vous exécutez le programme d'installation. Le nom du sous-dossier est l'heure et la date d'exécution du programme d'installation. Pour obtenir des instructions sur la manière d’afficher les fichiers journaux d’installation, consultez [Afficher et lire les fichiers journaux d’installation de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
-   Les fichiers journaux incluent une collection de fichiers.  
  
-   Ouvrez le fichier *_summary.txt pour afficher des informations sur les produits, les composants et les instances.  
  
-   Ouvrez le fichier *_errorlog.txt pour afficher des informations sur les erreurs générées durant l'installation.  
  
-   Ouvrez le fichier *_RS\_\*_ComponentUpdateSetup.log pour consulter les informations de l’installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
##  <a name="bkmk_prereq"></a> Vérification de la configuration requise  
 Le programme d'installation vérifie automatiquement les conditions préalables. Toutefois, si vous tentez de résoudre des problèmes d'installation, il est utile de connaître les vérifications effectuées par le programme d'installation.  
  
-   Les spécifications relatives aux comptes pour l'exécution du programme d'installation incluent l'appartenance au groupe Administrateurs local. Le programme d'installation doit avoir l'autorisation d'ajouter des fichiers et des paramètres du Registre, de créer des groupes de sécurité locaux et de définir des autorisations. Si vous installez une configuration par défaut, le programme d'installation doit avoir l'autorisation de créer une base de données du serveur de rapports sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle vous effectuez l'installation.  
  
-   Le système d'exploitation doit prendre en charge HTTP.SYS 1.1.  
  
-   Le service HTTP doit être activé et en cours d'exécution.  
  
-   Le Coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator) doit s'exécuter si vous installez également le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
-   Authz.dll doit être présent dans le dossier System32.  
  
 Le programme d'installation ne recherche plus les services Internet (IIS) ou [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nécessite MDAC 2.0 et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] version 2.0. Le programme d'installation installe ces composants s'ils ne le sont pas déjà.  
  
##  <a name="bkmk_tshoot_sharepoint"></a> Dépannage des problèmes liés aux installations en mode SharePoint  
  
-   [Le gestionnaire de configuration de Reporting Services ne démarre pas](#bkmk_configmanager_notstart)  
  
-   [Vous ne voyez pas le service SQL Server Reporting Services dans Administration centrale de SharePoint après l’installation de SQL Server 2012 SSRS en mode SharePoint](#bkmk_no_ssrs_service)  
  
-   [Les applets de commande PowerShell de Reporting Services ne sont pas disponibles et les commandes ne sont pas identifiées](#bkmk_cmdlets_not_recognized)  
  
-   [Vous voyez s'afficher un message d'erreur indiquant que l'URL n'est pas configurée](#bkmk_URL_not_configured)  
  
-   [L'installation échoue sur un ordinateur sur lequel SharePoint est installé sans être configuré](#bkmk_sharepoint_not_confiugred)  
  
-   [La page Administration centrale de SharePoint est vide](#bkmk_central_admin_blank)  
  
-   [Vous voyez s'afficher un message d'erreur lorsque vous essayez de créer un nouveau rapport du Générateur de rapports](#bkmk_reportbuilder_newreport_error)  
  
-   [Un message d'erreur indiquant que RS_SHP n'est pas pris en charge avec PREPAREIMAGE s'affiche](#bkmk_RS_SHP_notsupported)  
  
###  <a name="bkmk_configmanager_notstart"></a> Le gestionnaire de configuration de Reporting Services ne démarre pas  
 **Description :** ceci est la procédure normale dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dispose dorénavant d'une architecture pour l'architecture de service SharePoint. Le Gestionnaire de configuration n'est plus nécessaire pour configurer et administrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.  
  
 **Solution de contournement :** utilisez l'Administration centrale SharePoint pour configurer un serveur de rapports en mode SharePoint. Pour plus d’informations, consultez [Gérer une application de service SharePoint Reporting Services](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
###  <a name="bkmk_no_ssrs_service"></a> Vous ne voyez pas le service SQL Server Reporting Services dans Administration centrale de SharePoint après l’installation de SQL Server 2012 SSRS en mode SharePoint  
 **Description :** si après avoir correctement installé [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint et le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in pour SharePoint 2010, vous ne pas voyez « SQL Server Reporting Services » dans les deux menus suivants, puis le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service n’a pas été inscrit :  
  
-   Administration centrale de SharePoint 2010 -&gt; « Gestion des applications » -&gt; Page « Gérer les services sur le serveur »  
  
-   Administration centrale de SharePoint 2010 --> « Gestion des applications » -> « Gérer les applications de service » -> Menu « Nouveau »  
  
 **Solution de contournement :** pour inscrire et démarrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services, effectuez les opérations suivantes :  
  
1.  Sur l'ordinateur qui exécute l'Administration centrale de SharePoint 2010  
  
    1.  Ouvrez SharePoint 2010 Management Shell avec des privilèges d'administrateur. Cliquez avec le bouton droit sur l'icône et cliquez sur « Exécuter en tant qu'administrateur ». Exécutez les trois applets de commande suivantes à partir de l'interpréteur de commandes :  
  
    2.  ```  
        Install-SPRSService  
        ```  
  
    3.  ```  
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```  
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  Vérifiez le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service affiche l’état «**démarré**» dans la page :-> de Administration centrale de SharePoint 2010 »**gestion des applications**« -> »**gérer les Services sur Serveur**»  
  
###  <a name="bkmk_cmdlets_not_recognized"></a> Les applets de commande PowerShell de Reporting Services ne sont pas disponibles et les commandes ne sont pas identifiées  
 **Description :** lorsque vous essayez d'exécuter une applet de commande PowerShell [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , un message d'erreur semblable au suivant s'affiche :  
  
-   Le terme « Install-SPRSServiceInstall-SPRSService » **n’est pas reconnu** comme nom d’applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez l'orthographe du nom, ou si le chemin d'accès existe, vérifiez que le chemin d'accès est correct et réessayez. At line:1 char:39+ Install-SPRSServiceInstall-SPRSService <<<<    + CategoryInfo          : ObjectNotFound: (Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **Solution de contournement :** sélectionnez l'une des options suivantes :  
  
-   Exécutez le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint. **rssharepoint.msi**.  
  
-   Installez le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à partir du support d'installation SQL Server.  
  
 **Remarque :** si **SharePoint 2013 Management Shell** est ouvert lorsque vous appliquez l'une des solutions de contournement, fermez et ouvrez de nouveau le shell de gestion.  
  
 Pour plus d'informations, consultez les documents suivants :  
  
-   [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
-   [Installer le Mode SharePoint de Reporting Services pour SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
###  <a name="bkmk_URL_not_configured"></a> Vous voyez s'afficher un message d'erreur indiquant que l'URL n'est pas configurée  
 **Description :** un message d’erreur s’affiche, semblable au suivant :  
  
 Cette fonctionnalité SQL Server Reporting Services (SSRS) n'est pas prise en charge. Utilisez l'Administration centrale pour vérifier et résoudre un ou plusieurs des problèmes suivants : • Une URL de serveur de rapports n'est pas configurée. Utilisez la page d'intégration SSRS pour la configurer. • Le proxy d'application de service SSRS n'est pas configuré. Utilisez les pages d'application de service SSRS pour configurer le proxy. • L'application de service SSRS n'est pas mappée à cette application Web. Utilisez les pages d'application de service SSRS pour associer le proxy d'application de service SSRS au Groupe de proxy d'application pour cette application Web.  
  
 **Solution de contournement :** le message d'erreur suggère trois étapes pour résoudre ce problème. La première suggestion dans le message « Un serveur de rapports URL n'est pas configuré... » s'applique lors de l'intégration à la version de serveur de rapports antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. La configuration SharePoint pour les versions de serveurs de rapports précédentes est effectuée dans la page **Paramètres généraux de l’application** , à l’aide de **SQL Server Reporting Services (2008 et 2008 R2)**.  
  
 **Autres informations :** vous verrez ce message d'erreur lorsque vous tenterez d'utiliser une fonctionnalité [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui requiert une connexion au service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Cela inclut :  
  
-   Ouverture du Générateur de rapports Microsoft SQL Server à partir d'une bibliothèque de documents SharePoint.  
  
-   Gestion des abonnements.  
  
-   Gestion d'une application de service.  
  
###  <a name="bkmk_sharepoint_not_confiugred"></a> L'installation échoue sur un ordinateur sur lequel SharePoint est installé sans être configuré  
 **Description :** si vous choisissez d'installer le mode SharePoint de Reporting Services sur un ordinateur sur lequel SharePoint est installé mais non configuré, un message semblable au suivant s'affiche et l'installation est interrompue :  
  
 Le programme d'installation de SQL Server a cessé de fonctionner  
  
 **Solution de contournement :** configurez SharePoint, puis exécutez le programme d'installation de SQL Server.  
  
 **Plus d'informations :** En installant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans une installation existante de SharePoint, le programme d'installation tente d'installer et de démarrzer le service SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si SharePoint n'est pas configuré, le programme d'installation de service échoue, ce qui entraîne l'échec de l'installation.  
  
###  <a name="bkmk_central_admin_blank"></a> La page Administration centrale de SharePoint est vide  
 **Description :** vous avez correctement installé SharePoint 2010, sans erreur. Toutefois, lorsque vous accédez à l'Administration centrale, vous voyez uniquement une page vide :  
  
 **Solution de contournement :** ce problème n'est pas spécifique à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mais est lié à la configuration des autorisations de votre installation globale SharePoint. La liste ci-dessous répertorie les suggestions :  
  
-   Consultez la rubrique SharePoint sur les environnements de développement. [Configurer l’environnement de développement pour SharePoint 2010 sur Windows Vista, Windows 7 et Windows Server 2008](http://msdn.microsoft.com/library/ee554869\(office.14\).aspx)  
  
-   Consultez la question du forum : [Central Administration returns blank page after installation on Windows 7](http://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   Le compte de service que vous utilisez pour les services SharePoint tels que le service Administration centrale de SharePoint 2010 doit être doté des privilèges d'administrateur du système d'exploitation local.  
  
###  <a name="bkmk_reportbuilder_newreport_error"></a> Vous voyez s'afficher un message d'erreur lorsque vous essayez de créer un nouveau rapport du Générateur de rapports  
 **Description :** Un message d'erreur semblable au suivant s'affiche lorsque vous essayez de créer un rapport du Générateur de rapports dans une bibliothèque de documents :  
  
 Cette fonctionnalité n'est pas prise en charge car une application de service SQL Server Reporting Services n'existe pas ou une URL de serveur de rapports n'a pas été configurée dans l'Administration centrale.  
  
 **Solution de contournement :** vérifiez que vous disposez d'une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et qu'elle est configurée correctement. Pour plus d’informations, consultez la section « créer une Application de Service Reporting Services » dans [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
###  <a name="bkmk_RS_SHP_notsupported"></a> Un message d'erreur indiquant que RS_SHP n'est pas pris en charge avec PREPAREIMAGE s'affiche  
 **Description :** lorsque vous essayez d'exécuter PREPAREIMAGE pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , un message d'erreur semblable au suivant s'affiche :  
  
 « La fonctionnalité spécifiée « RS_SHP » n'est pas prise en charge lors de l'exécution de l'action de PREPAREIMAGE, car elle ne prend pas en charge SysPrep. Supprimez les fonctionnalités incompatibles avec SysPrep et exécutez de nouveau le programme d'installation. »  
  
 **Solution de contournement :** il n'existe aucune solution de contournement. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prend pas en charge SYSPREP (PREPAREIMAGE). [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prends pas en charge SYSPREP.  
  
##  <a name="bkmk_tshoot_native"></a> Dépannage de problèmes dans les installations en mode natif  
  
###  <a name="PerfCounters"></a> Les compteurs de performance ne sont pas visibles après une mise à niveau vers Windows Vista ou Windows Server 2008  
 Si vous mettez à niveau le système d'exploitation vers [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] ou [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] sur un ordinateur qui exécute [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les compteurs de performance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne seront pas définis après la mise à niveau.  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>Pour rétablir les compteurs de performances Reporting Services  
  
1.  Supprimez les clés de Registre suivantes :  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service**  
  
2.  Ouvrez une fenêtre de commande et tapez la commande suivante à l'invite de commandes :  
  
    -   **Exécutez \< ** *répertoire .NET Framework 2.0* **> \InstallUtil.exe \< ** *répertoire Bin Report Server* **> \ReportingServicesLibrary.dll**  
  
        > [!NOTE]  
        >  Remplacez \< *répertoire .NET Framework 2.0*> avec le chemin d’accès physique du .NET Framework 2.0 fichiers et \< *répertoire Bin Report Server*> avec le chemin d’accès physique fichiers de rapports server bin.  
  
3.  Redémarrez le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Pour vérifier que les opérations effectuées ont fonctionné, ouvrez un navigateur Web et accédez à l'URL du Gestionnaire de rapports ou à l'URL du serveur de rapports. Ouvrez ensuite l'Analyseur de performances pour vérifier que les compteurs fonctionnent.  
  
#### <a name="to-re-add-the-performance-registry-keys-by-using-registry-editor"></a>Pour rajouter les clés de Registre Performance à l'aide de l'Éditeur du Registre  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans le **exécuter** boîte de dialogue le **Open** , tapez `regedit`.  
  
2.  Dans l’Éditeur du Registre, sélectionnez la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
3.  Cliquez avec le bouton droit sur le nœud **Performance** , pointez sur **Nouveau**, puis cliquez sur **Valeur de chaînes multiples**.  
  
4.  Type `Counter Names` puis appuyez sur ENTRÉE.  
  
5.  Répétez l’opération pour ajouter le `Counter Types` clé de Registre dans ce nœud.  
  
6.  Accédez à la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
7.  Cliquez avec le bouton droit sur le nœud **Performance** , pointez sur **Nouveau**, puis cliquez sur **Valeur de chaînes multiples**.  
  
8.  Type `Counter Names` puis appuyez sur ENTRÉE.  
  
9. Répétez l’opération pour ajouter le `Counter Types` clé de Registre dans ce nœud.  
  
 Après avoir réparé l'instance 64 bits ou rajouté les clés de Registre manuellement, vous pouvez utiliser l'Analyseur de performances pour configurer les objets de performance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à surveiller.  
  
###  <a name="ConfigPropsMissing"></a> Les propriétés de configuration ReportServerExternalURL et PassThroughCookies ne sont pas configurées après une mise à niveau à partir de SQL Server 2005  
 Lorsque vous mettez à niveau à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] à [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], le `ReportServerExternalURL` et `PassThroughCookies` propriétés de configuration ne sont pas configurées par le processus de mise à niveau. `ReportServerExternalURL` est une propriété facultative, et il doit être défini uniquement si vous utilisez des composants WebPart SharePoint 2.0 et vous souhaitez que les utilisateurs puissent récupérer un rapport et l’ouvrir dans une nouvelle fenêtre de navigateur. Pour plus d’informations sur `ReportServerExternalURL`, consultez [URL des fichiers de Configuration de &#40;Gestionnaire de Configuration de SSRS&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md). `PassThroughCookies` est requis uniquement lorsque vous utilisez la méthode d’authentification personnalisée. Pour plus d’informations sur `PassThroughCookies`, consultez [configurer le Gestionnaire de rapports pour passer des Cookies d’authentification personnalisé](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
> [!NOTE]  
>  Lorsque vous utilisez l'authentification personnalisée, il est recommandé de migrer votre installation plutôt que d'effectuer une mise à niveau. Pour plus d’informations sur la migration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Migrer une installation Reporting Services &#40;mode natif&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
 Par défaut, ces propriétés n'existent pas dans la configuration de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] . Si vous avez configuré ces propriétés dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et que vous avez toujours besoin des fonctionnalités qu'elles offrent, vous devez les ajouter manuellement au fichier **RSReportServer.config** après la mise à niveau. Pour plus d’informations, consultez [Modifier un fichier de configuration &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
###  <a name="Default2005InstallBreaks2008"></a> L’installation échoue pour une instance par défaut de SQL Server 2005 Reporting Services sur un ordinateur qui exécute SQL Server 2012 Reporting Services  
 Si vous tentez d’installer une instance par défaut de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un ordinateur qui exécute déjà une instance de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance ne peut pas installer avec le message d’erreur suivant :  
  
 « Une instance portant le même nom est déjà installée sur un ou plusieurs nœuds du cluster. Pour poursuivre l'installation de SQL Server, fournissez un nom d'instance unique. »  
  
 Ce problème se produit indépendamment du fait que l'instance de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] soit une instance par défaut ou nommée, et indépendamment du fait qu'une instance de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] portant ce nom soit déjà présente ou non sur l'ordinateur.  
  
 Pour contourner ce problème, choisissez l'une des méthodes suivantes :  
  
-   Si vous devez exécuter [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en tant que l’instance par défaut sur l’ordinateur, vous devez installer le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance avant la [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] instance.  
  
-   Si le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance n’a pas besoin être une instance par défaut, vous pouvez installer le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance comme instance nommée après avoir installé le [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] instance.  
  
###  <a name="WindowsAuthBreaksAfterUpgrade"></a> Erreur 401 non autorisée lors de l’utilisation de l’authentification Windows après une mise à niveau à partir de SQL Server 2005 vers SQL Server 2012  
 Si vous mettez à niveau à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]et vous utilisez l’authentification NTLM avec un compte intégré pour le compte de service Report Server, vous pouvez rencontrer une erreur 401-non autorisé lorsque vous accédez au serveur de rapports ou le Gestionnaire de rapports après la mise à niveau.  
  
 Cette erreur se produit à cause d'une modification dans la configuration par défaut de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] pour l'authentification Windows. Negotiate est configuré lorsque le compte de service Report Server est Service réseau ou Système local. NTLM est configuré lorsque le compte de service Report Server n'est pas l'un de ces comptes intégrés. Pour résoudre ce problème après la mise à niveau, vous pouvez modifier le fichier RSReportServer.config et attribuer à `AuthenticationType` la valeur `RSWindowsNTLM`. Pour plus d’informations, consultez [configurer l’authentification Windows sur le serveur de rapports](../security/configure-windows-authentication-on-the-report-server.md).  
  
###  <a name="Uninstall32BitBreaks64Bit"></a> Désinstallation de l’instance 32 bits de SQL Server 2012 Reporting Services dans le déploiement de côte à côte avec une instance 64 bits arrête l’instance 64 bits instance  
 Lorsque vous installez une instance 32 bits et une instance 64 bits de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] côte à côte sur un ordinateur, puis désinstallez l’instance 32 bits, quatre clés de Registre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont supprimées. Cela arrête l'instance 64 bits de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Les clés de Registre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui sont supprimées lorsque vous désinstallez l’instance 32 bits sont les suivantes :  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Types`)  
  
 Pour résoudre ce problème, vous pouvez réparer l'instance 64 bits. Bien qu'il soit recommandé d'utiliser la réparation, vous pouvez manuellement rajouter les clés de Registre à l'aide de l'Éditeur du Registre.  
  
> [!CAUTION]  
>  Une modification incorrecte du Registre peut sérieusement endommager votre système. Avant d'apporter des modifications au Registre, il convient de sauvegarder les données importantes qui se trouvent sur l'ordinateur.  
  
##  <a name="bkmk_additional"></a> Ressources supplémentaires  
 Vous trouverez ci-dessous des ressources complémentaires pour vous aider à résoudre les problèmes :  
  
-   Wiki TechNet : rubriques de dépannage [Dépanner SQL Server Reporting Services (SSRS) en mode intégré SharePoint](http://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [Forum : SQL Server Reporting Services](http://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
 ![Paramètres SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "paramètres SharePoint") [envoyer des commentaires et des informations via Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
  