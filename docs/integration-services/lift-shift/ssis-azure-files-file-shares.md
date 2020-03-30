---
title: Ouvrir et enregistrer des fichiers avec des packages SSIS déployés dans Azure | Microsoft Docs
description: Découvrez comment ouvrir et enregistrer des fichiers localement et dans Azure quand effectuez un lift-and-shift de packages SSIS qui utilisent des systèmes de fichiers locaux dans SSIS dans Azure.
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: 696b7bbd19ed41aeedaf0cbba683870c04de1b13
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67896198"
---
# <a name="open-and-save-files-on-premises-and-in-azure-with-ssis-packages-deployed-in-azure"></a>Ouvrir et enregistrer des fichiers localement et dans Azure avec des packages SSIS déployés dans Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Cet article explique ouvrir et enregistrer des fichiers localement et dans Azure quand effectuez un lift-and-shift de packages SSIS qui utilisent des systèmes de fichiers locaux dans SSIS dans Azure.

## <a name="save-temporary-files"></a>Enregistrer des fichiers temporaires
Si vous devez stocker et traiter des fichiers temporaires au cours d’une même exécution d’un package, les packages peuvent utiliser le répertoire de travail actuel (`.`) ou le répertoire temporaire (`%TEMP%`) de vos nœuds Azure SSIS Integration Runtime.

## <a name="use-on-premises-file-shares"></a>Utiliser des partages de fichiers locaux
Pour continuer à utiliser les **partages de fichiers locaux** quand vous faites un lift-and-shift des packages basés sur des systèmes de fichiers locaux dans SSIS au sein d’Azure, effectuez les actions suivantes :
1.  Transférez les fichiers des systèmes de fichiers locaux vers des partages de fichiers locaux.
2.  Joignez les partages de fichiers locaux à un réseau virtuel Azure.
3.  Joignez votre runtime d’intégration Azure-SSIS au même réseau virtuel. Pour plus d’information, voir [Joindre un runtime d’intégration Azure-SSIS à un réseau virtuel](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Connectez votre runtime d’intégration Azure-SSIS aux partages de fichiers locaux dans le même réseau virtuel en configurant des informations d’identification d’accès qui utilisent l’authentification Windows. Pour plus d’informations, consultez [Se connecter à des données et des partages de fichiers avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).
5.  Mettez à jour les chemins de fichiers locaux de vos packages en fonction des chemins UNC qui pointent vers les partages de fichiers locaux. Par exemple, mettez à jour `C:\abc.txt` vers `\\<on-prem-server-name>\<share-name>\abc.txt`.

## <a name="use-azure-file-shares"></a>Utiliser les partages de fichiers Azure
Pour utiliser **Azure Files** quand vous faites un lift-and-shift des packages basés sur des systèmes de fichiers locaux dans SSIS au sein d’Azure, effectuez les actions suivantes :
1.  Transférez les fichiers des systèmes de fichiers locaux vers Azure Files. Pour plus d’informations, consultez [Azure Files](https://azure.microsoft.com/services/storage/files/).
2.  Connectez votre runtime d’intégration Azure SSIS à Azure Files en configurant les informations d’identification d’accès qui utilisent l’authentification Windows. Pour plus d’informations, consultez [Se connecter à des données et des partages de fichiers avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).
3.  Mettez à jour les chemins de fichiers locaux de vos packages en fonction des chemins UNC qui pointent vers Azure Files. Par exemple, mettez à jour `C:\abc.txt` vers `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.
