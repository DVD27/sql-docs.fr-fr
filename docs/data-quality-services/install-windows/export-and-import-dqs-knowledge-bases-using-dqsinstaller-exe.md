---
title: Exporter et importer des bases de connaissances DQS à l’aide de fichier DQSInstaller. exe
description: Découvrez comment utiliser fichier DQSInstaller. exe pour exporter et importer des bases de connaissances DQS pour SQL Server Data Quality Services (DQS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8234c63b-a018-4e55-8184-9a6bdf03274d
author: swinarko
ms.author: sawinark
ms.openlocfilehash: ae87b9daebdef6b81c4d96abc253820cf7cb8228
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75558141"
---
# <a name="export-and-import-dqs-knowledge-bases-using-dqsinstallerexe"></a>Exporter et importer des bases de connaissances DQS à l'aide de DQSInstaller.exe

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Pour une installation existante de DQS, vous pouvez exporter toutes les bases de connaissances de votre [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] en même temps dans un fichier de sauvegarde DQS (.dqsb), puis utiliser ultérieurement ce fichier .dqsb pour importer toutes les bases de connaissances à la fois vers un autre [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] en exécutant le fichier DQSInstaller.exe à partir de l'invite de commandes. Pour plus d'informations sur l'exécution du fichier DQSInstaller.exe à partir de l'invite de commandes, consultez [Exécuter DQSInstaller.exe à partir d'une invite de commandes](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) dans [Exécuter DQSInstaller.exe pour terminer l'installation du serveur DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
 Cette fonctionnalité vous permet d'effectuer une sauvegarde de *toutes* vos bases de connaissances de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] en même temps sans avoir à exporter chaque base de connaissances individuellement dans un fichier .dqs à l'aide de [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]. De la même façon, vous pouvez importer *toutes* les bases de connaissances du fichier de sauvegarde dans un autre [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] en même temps sans avoir à importer individuellement chaque base de connaissances à partir d'un fichier .dqs à l'aide de [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]. Cela est particulièrement utile pour sauvegarder et restaurer vos bases de connaissances lorsque vous désinstallez [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] sur un ordinateur, puis le réinstallez sur un autre ordinateur. Vous pouvez facilement exporter toutes les bases de connaissances d'une installation existante de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] dans un fichier de sauvegarde DQS (.dqsb), puis importer toutes les bases de connaissances du fichier de sauvegarde après l'installation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] sur un autre ordinateur.  
  
##  <a name="exporting-knowledge-bases-to-dqsb-file"></a><a name="export"></a> Exportation de bases de connaissances vers le fichier .dqsb  
 Vous pouvez exporter toutes les bases de connaissances du [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] existant à tout moment ou lors de la désinstallation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].  
  
-   Pour exporter toutes les bases de connaissances d'un [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] dans un fichier de sauvegarde DQS (.dqsb), exécutez DQSInstaller.exe avec le paramètre `exportkbs` à partir de l'invite de commandes, avec le chemin d'accès complet et le nom du fichier dans lequel vous voulez exporter les bases de connaissances. Par exemple, pour exporter toutes les bases de connaissances dans le fichier DQSBackup.dqsb du lecteur C :  
  
    ```  
    dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  Si le nom de fichier spécifié existe déjà à l'emplacement indiqué, le programme d'installation vous demande si vous souhaitez remplacer ce fichier.  
  
-   Pour exporter toutes les bases de connaissances dans un fichier de sauvegarde DQS lors de la désinstallation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], exécutez DQSInstaller.exe avec le paramètre `uninstall` à partir de l'invite de commandes, avec le chemin d'accès complet et le nom du fichier dans lequel vous voulez exporter les bases de connaissances. Ainsi, pour exporter toutes les bases de connaissances dans le fichier DQSBackup.dqsb du lecteur C, puis désinstaller [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]:  
  
    ```  
    dqsinstaller.exe -uninstall c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  Si vous ne spécifiez pas le chemin d'accès complet et le nom du fichier de sauvegarde DQS lors de la désinstallation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] à partir de l'invite de commandes à l'aide du paramètre `uninstall` , un message apparaît indiquant que toutes les bases de connaissances seront supprimées. Il vous permet de choisir si vous voulez poursuivre le processus de désinstallation.  
  
##  <a name="importing-knowledge-bases-from-dqsb-file"></a><a name="import"></a> Importation de bases de connaissances à partir du fichier .dqsb  
 Vous pouvez importer toutes les bases de connaissances à partir d'un fichier de sauvegarde DQS (.dqsb) une fois l'installation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] terminée. Pour importer des bases de connaissances, vous devez disposer d'un fichier de sauvegarde DQS (.dqsb) valide.  
  
 Exécutez le fichier DQSInstaller.exe avec le paramètre `importkbs` à partir de l'invite de commandes, avec le chemin d'accès complet et le nom du fichier à partir duquel vous souhaitez importer les bases de connaissances. Par exemple, pour importer toutes les bases de connaissances à partir du fichier DQSBackup.dqsb du lecteur C :  
  
```  
dqsinstaller.exe -importkbs c:\DQSBackup.dqsb  
```  
  
 Si votre [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] contient des bases de connaissances portant le même nom que celles que vous importez, les noms des bases de connaissances importées sont complétés par un trait de soulignement (_) suivi d'une valeur entière en commençant par 1. Par exemple, si le domaine « CompanyName » apparaît deux fois, le nom de domaine importé est « CompanyName_1 ».  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter fichier DQSInstaller. exe pour terminer l’installation du serveur de qualité des données](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)   
 [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Exporter une base de connaissances vers un fichier. DQS](../../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)   
 [Importer une base de connaissances à partir d'un fichier .dqs](../../data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)  
  
  
