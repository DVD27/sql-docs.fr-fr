---
title: Vue d’ensemble de SQL Server sur Linux
description: Cet article explique comment SQL Server s’exécute sur Linux et fournit des informations sur la façon d’en savoir plus.
author: VanMSFT
ms.author: vanto
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: e3bd50cba4bcab81e7dcf00db9394704c5486160
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68105459"
---
# <a name="sql-server-on-linux"></a>SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: moniker range="= sql-server-2017 || = sqlallproducts-allversions"
À compter de SQL Server 2017, SQL Server s’exécute sur Linux. Il s’agit du même moteur de base de données SQL Server, avec de nombreux services et fonctionnalités similaires, quel que soit votre système d’exploitation.
::: moniker-end

::: moniker range=">= sql-server-ver15 || >= sql-server-linux-ver15"
La préversion SQL Server 2019 s’exécute sur Linux. Il s’agit du même moteur de base de données SQL Server, avec de nombreux services et fonctionnalités similaires, quel que soit votre système d’exploitation. Pour en savoir plus sur cette mise en production, consultez [Nouveautés de la préversion SQL Server 2019 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sql-server-on-linux).
::: moniker-end

::: moniker range="= sql-server-2017"
> [!TIP]
> [Préversion SQL Server 2019](sql-server-linux-overview.md?view=sql-server-ver15) mise en production ! Pour en savoir plus sur les nouveautés pour Linux dans la dernière mise en production, consultez [Nouveautés dans la préversion SQL Server 2019 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).
::: moniker-end

::: moniker range="= sql-server-linux-2017"
> [!TIP]
> [Préversion SQL Server 2019](sql-server-linux-overview.md?view=sql-server-linux-ver15) mise en production ! Pour en savoir plus sur les nouveautés pour Linux dans la dernière mise en production, consultez [Nouveautés dans la préversion SQL Server 2019 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-linux-ver15#sql-server-on-linux).
::: moniker-end

::: moniker range="= sqlallproducts-allversions"
> [!TIP]
> Préversion SQL Server 2019 mise en production ! Pour en savoir plus sur les nouveautés pour Linux dans la dernière mise en production, consultez [Nouveautés dans la préversion SQL Server 2019 pour Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sql-server-on-linux).
::: moniker-end

## <a name="install"></a>Installation

Pour commencer, installez SQL Server sur Linux à l’aide de l’un des outils de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-docker.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

> [!NOTE]
> Docker lui-même s’exécute sur plusieurs plateformes, ce qui signifie que vous pouvez exécuter l’image de Docker sur Linux, Mac et Windows.

## <a name="connect"></a>Se connecter

Après l’installation, connectez-vous à l’instance sur votre machine Linux. Vous pouvez vous connecter localement ou à distance et avec un large éventail d’outils et de pilotes. Les démarrages rapides montrent comment utiliser l'outil en ligne de commande [sqlcmd](sql-server-linux-setup-tools.md). D’autres outils incluent les éléments suivants :

| Outil | Didacticiel |
|-----|-----|
| Visual Studio Code (VS Code) | [Utiliser VS Code avec SQL Server sur Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Utiliser SSMS sur Windows pour vous connecter à SQL Server sur Linux](sql-server-linux-manage-ssms.md) |
| SQL Server Data Tools (SSDT) | [Utiliser SSDT avec SQL Server sur Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Explorer

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

SQL Server 2017 a le même moteur de base de données sous-jacent sur toutes les plateformes prises en charge, y compris Linux. Par conséquent, de nombreuses fonctionnalités existantes fonctionnent de la même façon sur Linux. Cette partie de la documentation expose certaines de ces fonctionnalités du point de vue de Linux. Il appelle également les zones qui présentent des exigences uniques sur Linux.

Si vous êtes déjà familiarisé avec SQL Server, consultez les [Notes de publication](sql-server-linux-release-notes.md) pour obtenir des instructions générales et des problèmes connus pour cette mise en production. Examinez ensuite les [nouveautés de SQL Server sur Linux](sql-server-linux-whats-new.md), ainsi que les [nouveautés de l’ensemble de SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15"

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] a le même moteur de base de données sous-jacent sur toutes les plateformes prises en charge, y compris Linux. Par conséquent, de nombreuses fonctionnalités existantes fonctionnent de la même façon sur Linux. Cette partie de la documentation expose certaines de ces fonctionnalités du point de vue de Linux. Il appelle également les zones qui présentent des exigences uniques sur Linux.

Si vous êtes déjà familiarisé avec SQL Server sur Linux, consultez les [Notes de publication](sql-server-linux-release-notes-2019.md) pour obtenir des instructions générales et des problèmes connus pour cette mise en production. Consultez ensuite les [nouveautés de la préversion SQL Server 2019 sur Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

::: moniker-end

<!--SQL Server All Versions-->
::: moniker range="=sqlallproducts-allversions"

SQL Server 2017 et [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] ont le même moteur de base de données sous-jacent sur toutes les plateformes prises en charge, y compris Linux. Par conséquent, de nombreuses fonctionnalités existantes fonctionnent de la même façon sur Linux. Cette partie de la documentation expose certaines de ces fonctionnalités du point de vue de Linux. Il appelle également les zones qui présentent des exigences uniques sur Linux.

Si vous êtes déjà familiarisé avec SQL Server sur Linux, consultez les notes de publication :

- [Notes de publication de SQL Server 2017](sql-server-linux-release-notes.md)
- [Notes de publication de la préversion SQL Server 2019](sql-server-linux-release-notes-2019.md)

Consultez ensuite les nouveautés :

- [Nouveautés de SQL Server 2017](sql-server-linux-whats-new.md)
- [Nouveautés de la préversion SQL Server 2019 sur Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sql-server-on-linux)

::: moniker-end

> [!TIP]
> Pour obtenir des réponses aux questions fréquemment posées, consultez la [FAQ de SQL Server sur Linux](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
