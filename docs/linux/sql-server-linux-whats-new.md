---
title: Nouveautés de SQL Server 2017 sur Linux
description: Cet article présente les nouveautés de SQL Server 2017 sur Linux.
author: VanMSFT
ms.author: vanto
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: 3f3f51716acf69368ae2554446c47d125b500e03
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032158"
---
# <a name="whats-new-for-sql-server-on-linux"></a>Nouveautés de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit les principaux services et fonctionnalités disponibles pour SQL Server 2017 s’exécutant sur Linux.

La préversion de SQL Server 2019 a été mise en production. Cet article ne couvre pas les mises en production des préversions SQL Server 2019. Pour en savoir plus sur la préversion SQL Server 2019, consultez [Nouveautés de la préversion SQL Server 2019 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

> [!NOTE]
> En plus des fonctionnalités du présent article, des mises à jour cumulatives sont mises en production à intervalles réguliers après la mise en production du GA. Ces mises à jour cumulatives fournissent de nombreuses améliorations et correctifs. Pour plus d’informations sur la dernière mise en production CU, consultez [https://aka.ms/sql2017cu](https://aka.ms/sql2017cu). Pour connaitre les téléchargements de packages et les problèmes connus, consultez les [Notes de publication](sql-server-linux-release-notes.md).

## <a name="sql-server-database-engine"></a>Moteur de base de données SQL Server

- Activation des fonctionnalités de Moteur de base de données de SQL Server principales.
- Support des chemins d’accès Linux natifs.
- Support IPV6.
- Support des fichiers de base de données sur NFS.
- Activation du chiffrement du [Protocole TLS](sql-server-linux-encrypted-connections.md) (Transport Layer Security).
- Activation de l’[Authentification Active Directory](sql-server-linux-active-directory-authentication.md).
- [Fonctionnalités de groupes de disponibilité](sql-server-linux-availability-group-overview.md) pour la haute disponibilité.
- Support de la [Recherche en texte intégral](sql-server-linux-setup-full-text-search.md).

## <a name="sql-server-agent"></a>SQL Server Agent

- Activation du support [SQL Server Agent](sql-server-linux-setup-sql-agent.md) pour les tâches suivantes :
  - [Tâches Transact-SQL](sql-server-linux-run-sql-server-agent-job.md)
  - [Courrier de base de messages](sql-server-linux-db-mail-sql-agent.md)
  - [Copie des journaux de transaction](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Capacité d’exécuter des packages SSIS sur Linux. Pour plus d’informations, consultez [Configurer SQL Server Integration Services sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="other-improvements"></a>Autres améliorations

- Outil de configuration de ligne de commande, [mssql-conf](sql-server-linux-configure-mssql-conf.md).
- Support de l’installation sans assistance avec les [variables d’environnement](sql-server-linux-configure-environment-variables.md).
- [Extension mssql-server de Visual Studio Code](sql-server-linux-develop-use-vscode.md) multiplateforme.
- Générateur de script multiplateforme, [mssql-scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md).
- Analyse des vues de gestion dynamique (DMV) multiplateforme, [outil DBFS](https://github.com/Microsoft/dbfs).

## <a name="next-steps"></a>Étapes suivantes

Pour installer SQL Server sur Linux, utilisez l’un des didacticiels suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-docker.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Pour voir d’autres améliorations introduites dans SQL Server 2017, consultez [Nouveautés de SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

> [!TIP]
> Pour obtenir des réponses aux questions fréquemment posées, consultez la [FAQ de SQL Server sur Linux](sql-server-linux-faq.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
