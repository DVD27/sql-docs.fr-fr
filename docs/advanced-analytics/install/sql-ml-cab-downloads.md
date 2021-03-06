---
title: Téléchargements CAB pour SQL Server les mises à jour cumulatives
description: Les fichiers CAB r et Python et les téléchargements de packages pour SQL Server Machine Learning Services et SQL Server 2016 R services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7b77a1fd3a0d2575f0add7badb1c5bf632d29d70
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715833"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>Téléchargements CAB pour les mises à jour cumulatives des instances d’analyse en base de données SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server instances configurées pour l’analyse dans la base de données incluent les fonctionnalités R et Python. Ces fonctionnalités sont livrées dans des fichiers CAB, installés et desservis via le programme d’installation de SQL Server. Sur les appareils connectés à Internet, les mises à jour CAB sont généralement appliquées via Windows Update. Sur les serveurs déconnectés, les fichiers CAB doivent être téléchargés et appliqués manuellement. 

Cet article fournit des liens de téléchargement vers des fichiers CAB pour chaque mise à jour cumulative. Pour plus d’informations sur les installations en mode hors connexion, consultez [installer des composants SQL Server machine learning sans accès à Internet](sql-ml-component-install-without-internet-access.md#apply-cu).

## <a name="prerequisites"></a>Prérequis

Commencez par une installation de base.

+ Sur SQL Server Machine Learning Services, la version initiale est l’installation de base. 
+ Sur SQL Server services R 2016, vous pouvez commencer par la version initiale, SP1 ou SP2. 

Vous pouvez également appliquer des mises à jour cumulatives à un serveur autonome.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="sql-server-2017-cabs"></a>SQL Server les CAB 2017

Les fichiers CAB sont répertoriés par ordre chronologique inverse. Lorsque vous téléchargez les fichiers CAB et les transférez vers l’ordinateur cible, placez-les dans un dossier pratique, tel que **téléchargements** ou le dossier% Temp% de l’utilisateur du programme d’installation.

|Libérer  |Composant | Télécharger le lien  | Problèmes résolus | 
|---------|----------|----------------|------------------|
|**[SQL Server 2017 CU14](https://support.microsoft.com/help/4484710/)-[CU15](https://support.microsoft.com/help/4498951/)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073898&clcid=1033)| Les binaires dans le package sont maintenant signés. |
| | R Server      |[SRS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2069739&clcid=1033)| Les binaires dans le package sont maintenant signés. |
| | Microsoft python Open     | [SPO_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073897&clcid=1033)| Les binaires dans le package sont maintenant signés. |
| | Serveur python    |[SPS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2071421&clcid=1033)| Les binaires dans le package sont maintenant signés.  |
|**[SQL Server 2017 CU13](https://support.microsoft.com/help/4466404)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification par rapport aux versions précédentes. |
| | R Server      |[SRS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038263&clcid=1033)| Contient un correctif pour la mise à niveau d’un [R Server autonome opérationnel](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), tel qu’il est installé via le programme d’installation de SQL Server. Utilisez les CU13 cab et suivez [ces instructions](sql-machine-learning-standalone-windows-install.md#apply-cu) pour appliquer la mise à jour. |
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification par rapport aux versions précédentes. |
| | Serveur python    |[SPS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038197&clcid=1033)| Contient un correctif pour la mise à niveau d’un [serveur python autonome autonome](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), tel qu’il est installé via le programme d’installation de SQL Server. Utilisez les CU13 cab et suivez [ces instructions](sql-machine-learning-standalone-windows-install.md#apply-cu) pour appliquer la mise à jour. |
|**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)-[CU12](https://support.microsoft.com/help/4464082)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification par rapport aux versions précédentes. |
| | R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Correctifs mineurs.|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification par rapport aux versions précédentes. |
| | Serveur python    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Python rx_data_step perd l’ordre des lignes lorsque des doublons sont supprimés. <br/>SPEE a échoué la détection de type de données sur l’index ColumnStore cluster. <br/>Retourne une table vide lorsque les colonnes contiennent toutes les valeurs NULL. |
|**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification par rapport aux versions précédentes. |
| | R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification par rapport aux versions précédentes. |
| | Serveur python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
|**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification par rapport aux versions précédentes. |
| | R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification par rapport aux versions précédentes. |
| | Serveur python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| Types de données DateTime dans la requête SPEES.<br/>amélioration des messages d’erreur dans microsoftml lorsque des modèles préformés sont manquants.<br/> Résout des fonctions et des variables de transformation revoscalepy.|
|**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification par rapport aux versions précédentes. |
| | R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| Erreurs liées au chemin d’accès long dans rxInstallPackages.<br/>Connexions dans un bouclage pour RxExec.
| | Microsoft python Open    | Aucune modification par rapport aux versions précédentes. |
| | Serveur python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>Connexions dans un bouclage pour rx_exec.
|**[SQL Server 2017 CU4](https://support.microsoft.com/help/4056498)** |  |   |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Aucune modification par rapport aux versions précédentes. |
| | R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
| | Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification par rapport aux versions précédentes. |
| |  Serveur python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
|**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |  |
| | Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
| | R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
| | Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification par rapport aux versions précédentes. |
| | Serveur python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| Sérialisation du modèle python dans revoscalepy, à l’aide de la [fonction rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/>Prise en charge de la [notation Native](../sql-native-scoring.md) , plus des améliorations apportées à la [notation en temps réel](../real-time-scoring.md). 
|**[SQL Server 2017 CU1](https://support.microsoft.com/help/4038634)-[Cu2](https://support.microsoft.com/help/4052574)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| Aucune modification par rapport aux versions précédentes. |
| | R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Aucune modification par rapport aux versions précédentes. | 
| | Serveur python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | Ajoute rx_create_col_info pour retourner les informations de schéma. <br/>Améliorations apportées à [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) pour prendre en charge `RxLocalParallel` des scénarios parallèles à l’aide du contexte de calcul.|
|**Version initiale** |  |  |
| | Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
| | R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
| | Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
| | Serveur python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server les CAB 2016

Pour les services SQL Server R 2016, les versions de base sont soit la version RTM, soit une version Service Pack.

|Libérer  |Télécharger le lien  |
|---------|---------------|
|**SQL Server 2016 SP2 CU6**     |
|Microsoft R Open     |[SRO_3.2.2.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079936&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079933&clcid=1033)|
|**SQL Server 2016 SP2 CU1-CU5**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
|**SQL Server 2016 SP2**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)|
|**SQL Server 2016 SP1 CU14**     |
|Microsoft R Open     |[SRO_3.2.2.16100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2080130&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.17200_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079935&clcid=1033)|
|**SQL Server 2016 SP1 CU1-CU13**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
|**SQL Server 2016 SP1**     |
|Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)|
|Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)|
|**SQL Server 2016 CU4-CU9**     |
|Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
|Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
|**SQL Server 2016 CU2-CU3**     |
|Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)|
|Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)|
|**SQL Server 2016 CU1**     |
|Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)|
|Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)|
|**SQL Server 2016 RTM**     |
|Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)|
|Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)|

> [!NOTE]
> 
> Lors de l’installation de SQL Server 2016 SP1 CU4 ou SP1 CU5 hors connexion, téléchargez SRO_ 3.2.2.16000 _1033. cab. Si vous avez téléchargé SRO_ 3.2.2.13000 _1033. cab à partir de FWLINK 831785 comme indiqué dans la boîte de dialogue d’installation, renommez le fichier sro_ 3.2.2.16000 _1033. cab avant d’installer la mise à jour cumulative.

Si vous souhaitez afficher le code source de Microsoft R, vous pouvez le télécharger en tant qu’archive au format. tar: [Télécharger les programmes d’installation R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

[Appliquer des mises à jour cumulatives sur des ordinateurs sans accès à Internet](sql-ml-component-install-without-internet-access.md#apply-cu)

[Appliquer des mises à jour cumulatives sur des ordinateurs disposant d’une connexion Internet](sql-ml-component-install-without-internet-access.md#apply-cu)

[Appliquer des mises à jour cumulatives à un serveur autonome](sql-machine-learning-standalone-windows-install.md#apply-cu)
