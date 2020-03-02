---
title: Résolution des problèmes de blocage ou de plantage avec SSMS
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: dnethi
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 09/18/2019
ms.openlocfilehash: f994a44d6fe0f458ae8f8d8be0351421322e7967
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75243880"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>Obtenir des données de diagnostic après un incident de SQL Server Management Studio (SSMS)

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

## <a name="get-full-memory-dump-after-a-hang-or-crash"></a>Obtenir l’image mémoire complète après un blocage ou un incident

Obtenez une image mémoire complète de SQL Server Management Studio (SSMS) lors d’un blocage ou d’un incident.

Pour capturer des informations de diagnostic pour détecter un problème de blocage ou d’incident du SSMS, suivez les étapes ci-dessous.

1. Télécharger [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Décompressez le téléchargement dans un dossier.

3. Ouvrez une invite de commandes et exécutez la commande suivante.

    ```console
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    S’il vous invite à accepter un contrat de licence, sélectionnez *Accepter*.

4. Démarrez SSMS, s’il n’a pas déjà démarré.

5. Reproduisez le problème.

6. Le texte doit apparaître dans l’invite de commandes sur l’écriture du fichier de sauvegarde, attendez la fin.

7. Créez un nouveau dossier et copiez le fichier *.dmp qui est écrit dans ce dossier.

8. Copiez les fichiers suivants dans le même dossier.

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Compressez le dossier.

## <a name="get-full-memory-dump-for-an-outofmemoryexception"></a>Obtenir une image mémoire complète pour une OutOfMemoryException

Obtenez une image mémoire complète de SSMS quand il lève une OutOfMemoryException.

Vous pouvez obtenir une image mémoire complète avec n’importe quelle exception managée.

Pour capturer des informations de diagnostic afin de résoudre une OutOfMemoryException à partir du SSMS, suivez les étapes ci-dessous.

1. Télécharger [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Décompressez le téléchargement dans un dossier.

3. Ouvrez une invite de commandes et exécutez la commande suivante.

    ```console
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    S’il vous invite à accepter un contrat de licence, sélectionnez *Accepter*.

4. Démarrez SSMS (SQL Server Management Studio) s’il n’est pas déjà démarré.

5. Reproduisez le problème.

6. Le texte doit apparaître dans l’invite de commandes sur l’écriture du fichier de sauvegarde, attendez la fin.

7. Créez un nouveau dossier et copiez le fichier *.dmp qui est écrit dans ce dossier.

8. Copiez les fichiers suivants dans le même dossier.

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Compresser le dossier.
