---
title: Accéder à des magasins de données et à des partages de fichiers avec l’authentification Windows | Microsoft Docs
description: Découvrez comment configurer le catalogue SSIS dans Azure SQL Database et Azure-SSIS Integration Runtime dans Azure Data Factory pour exécuter des packages qui accèdent à des magasins de données et à des partages de fichiers avec l’authentification Windows.
ms.date: 3/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: 009a65c7c4381440dd7af6bb627fe2db70a16918
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68007952"
---
# <a name="access-data-stores-and-file-shares-with-windows-authentication-from-ssis-packages-in-azure"></a>Accéder à des magasins de données et à des partages de fichiers avec l’authentification Windows à partir de packages SSIS sur Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Vous pouvez utiliser l’authentification Windows pour accéder à des magasins de données, par exemple des serveurs SQL, des partages de fichiers, Azure Files, etc. à partir de packages SSIS qui s’exécutent sur Azure-SSIS Integration Runtime (IR) dans Azure Data Factory (ADF). Il peut s’agir de magasins de données sur site, hébergés sur les Machines virtuelles Azure ou qui s’exécutent dans Azure en tant que services gérés. S’ils sont en local, vous devez joindre votre runtime Azure-SSIS IR à un réseau virtuel connecté à votre réseau local : voir [Joindre un runtime Azure-SSIS IR à un réseau virtuel](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network). Il existe quatre moyens d’accéder à des magasins de données avec l’authentification Windows à partir de packages SSIS qui s’exécutent sur un runtime Azure-SSIS IR :

| Méthode de connexion | Portée effective | Étape de configuration | Méthode d’accès dans des packages | Nombre de jeux d’informations d’identification et ressources connectées | Type de ressources connectées | 
|---|---|---|---|---|---|
| Configurer un contexte d’exécution au niveau de l’activité | Selon l’activité Exécuter un package SSIS | Configurez la propriété **Authentification Windows** pour définir un contexte « Exécution/Exécuter en tant que » pour l’exécution de packages SSIS en tant qu’activités Exécuter un package SSIS dans des pipelines ADF.<br/><br/> Pour plus d’informations, voir [Configurer l’activité Exécuter le package SSIS](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity). | Accédez directement aux ressources des packages via le chemin d’accès UNC, par exemple si vous utilisez des partages de fichiers ou Azure Files : `\\YourFileShareServerName\YourFolderName` ou `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName`. | Prise en charge d’un seul jeu d’informations d’identification pour toutes les ressources connectées | - Partages de fichiers localement/sur des machines virtuelles Azure<br/><br/> - Azure Files, voir [Utiliser un partage de fichiers Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - Serveurs SQL sur site/Machines virtuelles Azure avec authentification Windows<br/><br/> - Autres ressources avec authentification Windows |
| Configurer un contexte d’exécution au niveau du catalogue | Selon le runtime Azure-SSIS IR ; sera remplacé à la configuration d’un contexte d’exécution au niveau de l’activité (voir plus haut) | Exécutez la procédure stockée `catalog.set_execution_credential` SSISDB pour définir un contexte « Exécution/Exécuter en tant que ».<br/><br/> Pour plus d’informations, voir la suite de cet article. | Accédez directement aux ressources des packages via le chemin d’accès UNC, par exemple si vous utilisez des partages de fichiers ou Azure Files : `\\YourFileShareServerName\YourFolderName` ou `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName`. | Prise en charge d’un seul jeu d’informations d’identification pour toutes les ressources connectées | - Partages de fichiers localement/sur des machines virtuelles Azure<br/><br/> - Azure Files, voir [Utiliser un partage de fichiers Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - Serveurs SQL sur site/Machines virtuelles Azure avec authentification Windows<br/><br/> - Autres ressources avec authentification Windows |
| Conserver les informations d’identification avec la commande `cmdkey` | Selon le runtime Azure-SSIS IR ; sera remplacé à la configuration d’un contexte d’exécution au niveau de l’activité/du catalogue (voir plus haut) | Exécutez la commande `cmdkey` dans un script d’installation personnalisée (`main.cmd`) lors de l’approvisionnement/la reconfiguration de votre runtime Azure-SSIS IR, par exemple si vous utilisez des partages de fichiers ou Azure Files : `cmdkey /add:YourFileShareServerName /user:YourDomainName\YourUsername /pass:YourPassword` ou `cmdkey /add:YourAzureStorageAccountName.file.core.windows.net /user:azure\YourAzureStorageAccountName /pass:YourAccessKey`.<br/><br/> Pour plus d’informations, voir [Personnaliser l’installation du runtime Azure-SSIS IR](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup). | Accédez directement aux ressources des packages via le chemin d’accès UNC, par exemple si vous utilisez des partages de fichiers ou Azure Files : `\\YourFileShareServerName\YourFolderName` ou `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName`. | Prise en charge de plusieurs jeux d’informations d’identification pour différentes ressources connectées | - Partages de fichiers localement/sur des machines virtuelles Azure<br/><br/> - Azure Files, voir [Utiliser un partage de fichiers Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - Serveurs SQL sur site/Machines virtuelles Azure avec authentification Windows<br/><br/> - Autres ressources avec authentification Windows |
| Monter des lecteurs à l’exécution du package (non persistant) | Par package | Exécutez la commande `net use` dans la tâche Exécuter le processus ajoutée au début du flux de contrôle de vos packages, par exemple, `net use D: \\YourFileShareServerName\YourFolderName`. | Accédez aux partages de fichiers par le biais de lecteurs mappés. | Prise en charge de plusieurs lecteurs pour différents partages de fichiers | - Partages de fichiers localement/sur des machines virtuelles Azure<br/><br/> - Azure Files, voir [Utiliser un partage de fichiers Azure](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) |
|||||||

> [!WARNING]
> Si vous n’utilisez aucune des méthodes ci-dessus pour accéder à des magasins de données avec l’authentification Windows, les packages qui dépendent de l’authentification Windows ne pourront pas y accéder et échoueront à l’exécution. 

La suite de cet article explique comment configurer le catalogue SSIS (SSISDB) hébergé sur le serveur Azure SQL Database/Managed Instance pour exécuter des packages sur le runtime Azure-SSIS IR qui utilise l’authentification Windows pour accéder aux magasins de données. 

## <a name="you-can-only-use-one-set-of-credentials"></a>Vous ne pouvez utiliser qu’un seul jeu d’informations d’identification
Si vous utilisez l’authentification Windows dans un package SSIS, vous ne pouvez recourir qu’à un seul jeu d’informations d’identification. Tant que vous ne les changez et ne les supprimez pas, les informations d’identification de domaine que vous indiquez en suivant les étapes de cet article s’appliquent à toutes les exécutions de packages, interactives ou planifiées, sur votre runtime Azure-SSIS IR. Si votre package doit se connecter à plusieurs magasins de données avec différents jeux d’informations d’identification, tournez-vous vers les autres méthodes décrites plus haut.

## <a name="provide-domain-credentials-for-windows-authentication"></a>Fournir des informations d’identification de domaine pour l’authentification Windows
Suivez les étapes ci-dessous pour fournir des informations d’identification de domaine permettant aux packages d’utiliser l’authentification Windows afin d’accéder à des magasins de données sur site :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous au serveur Azure SQL Database/Managed Instance qui héberge SSISDB. Pour plus d’informations, voir [Se connecter à SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante en indiquant les informations d’identification de domaine nécessaires :

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  Exécutez vos packages SSIS. Les packages utiliseront les informations d’identification fournies pour accéder aux magasins de données sur site avec l’authentification Windows.

### <a name="view-domain-credentials"></a>Afficher les informations d’identification de domaine
Pour afficher les informations d’identification de domaine actives, effectuez les actions suivantes :

1.  Avec SSMS ou un autre outil, connectez-vous au serveur Azure SQL Database/Managed Instance qui héberge SSISDB. Pour plus d’informations, voir [Se connecter à SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante et vérifiez la sortie :

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>Effacer les informations d’identification de domaine
Pour effacer et supprimer les informations d’identification que vous avez fournies, comme indiqué dans cet article, effectuez les actions suivantes :

1.  Avec SSMS ou un autre outil, connectez-vous au serveur Azure SQL Database/Managed Instance qui héberge SSISDB. Pour plus d’informations, voir [Se connecter à SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante :

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-a-sql-server-on-premises"></a>Se connecter à un serveur SQL Server sur site 
Suivez les étapes ci-dessous pour vérifier que vous pouvez vous connecter à un serveur SQL Server sur site :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez la commande suivante pour lancer SSMS avec les informations d’identification de domaine souhaitées :

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  À partir de SSMS, vérifiez que vous pouvez vous connecter au serveur SQL Server sur site.

### <a name="prerequisites"></a>Conditions préalables requises
Suivez les étapes ci-dessous pour accéder à un serveur SQL Server sur site à partir de packages qui s’exécutent sur Azure :

1.  Dans le Gestionnaire de configuration SQL Server, activez le protocole TCP/IP.
2.  Autorisez l’accès à travers le Pare-feu Windows. Pour plus d’informations, voir [Configurer le Pare-feu Windows pour accéder à SQL Server](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access).
3.  Joignez votre runtime Azure-SSIS IR à un réseau virtuel connecté au serveur SQL Server sur site.  Pour plus d’informations, voir [Joindre un runtime Azure-SSIS IR à un réseau virtuel](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Utilisez la procédure stockée `catalog.set_execution_credential` SSISDB pour indiquer les informations d’identification comme le décrit cet article.

## <a name="connect-to-a-file-share-on-premises"></a>Se connecter à un partage de fichiers sur site 
Suivez les étapes ci-dessous pour vérifier que vous pouvez vous connecter à un partage de fichiers sur site :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez les commandes suivantes. Elles ouvrent une fenêtre d’invite de commandes avec les informations d’identification de domaine à utiliser, puis testent la connectivité au partage de fichiers sur site en récupérant une liste de répertoires.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Vérifiez que la liste de répertoires est retournée pour le partage de fichiers sur site.

### <a name="prerequisites"></a>Conditions préalables requises
Suivez les étapes ci-dessous pour accéder à un partage de fichiers sur site à partir de packages qui s’exécutent sur Azure :

1.  Autorisez l’accès à travers le Pare-feu Windows.
2.  Joignez votre runtime Azure-SSIS IR à un réseau virtuel connecté au partage de fichiers sur site.  Pour plus d’informations, voir [Joindre un runtime Azure-SSIS IR à un réseau virtuel](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
3.  Utilisez la procédure stockée `catalog.set_execution_credential` SSISDB pour indiquer les informations d’identification comme le décrit cet article.

## <a name="connect-to-a-file-share-on-azure-vm"></a>Se connecter à un partage de fichiers sur les Machines virtuelles Azure
Suivez les étapes ci-dessous pour accéder à un partage de fichiers sur les Machines virtuelles Azure à partir de packages qui s’exécutent sur Azure :

1.  Avec SSMS ou un autre outil, connectez-vous au serveur Azure SQL Database/Managed Instance qui héberge SSISDB. Pour plus d’informations, voir [Se connecter à SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante en indiquant les informations d’identification de domaine nécessaires :

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>Se connecter à un partage de fichiers dans Azure Files
Pour plus d’informations sur Azure Files, consultez [Azure Files](https://azure.microsoft.com/services/storage/files/).

Suivez les étapes ci-dessous pour accéder à un partage de fichiers sur Azure Files à partir de packages qui s’exécutent sur Azure :

1.  Avec SSMS ou un autre outil, connectez-vous au serveur Azure SQL Database/Managed Instance qui héberge SSISDB. Pour plus d’informations, voir [Se connecter à SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante en indiquant les informations d’identification de domaine nécessaires :

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Étapes suivantes
- Déployez vos packages. Pour plus d’informations, voir [Déployer un projet SSIS dans Azure avec SSMS](../ssis-quickstart-deploy-ssms.md).
- Exécutez vos packages. Pour plus d’informations, voir [Exécuter des packages SSIS sur Azure avec SSMS](../ssis-quickstart-run-ssms.md).
- Planifiez vos packages. Pour plus d’informations, consultez [Planifier des packages SSIS dans Azure](ssis-azure-schedule-packages.md).
