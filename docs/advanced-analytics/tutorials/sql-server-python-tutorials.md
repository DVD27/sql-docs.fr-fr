---
title: Présentation du didacticiel de Python SQL Server 2017
description: Présentation des didacticiels Python pour l’analytique en base de données SQL Server 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 65dd2197d9fb079da116908871d931ad19370cf5
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714769"
---
# <a name="sql-server-2017-python-tutorials"></a>Didacticiels python SQL Server 2017
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit les didacticiels Python pour l’analyse dans la base de données sur [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md). 

+ Découvrez comment encapsuler et exécuter du code python dans des procédures stockées.
+ Sérialisez et enregistrez les modèles basés sur Python pour SQL Server bases de données.
+ En savoir plus sur les contextes de calcul locaux et distants et leur utilisation.
+ Explorez les modules Microsoft Python pour la science des données et les tâches de Machine Learning.

<a name="bkmk_pythontutorials"></a>

## <a name="python-quickstarts-and-tutorials"></a>Guides de démarrage rapide et didacticiels python

| Lien | Description |
|------|-------------|
| [Démarrage rapide : Script Python «Hello World» dans SQL Server](quickstart-python-run-using-t-sql.md) | Découvrez les principes de base de l’appel de Python dans T-SQL. |
| [Démarrage rapide : Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md) | Explique comment incorporer le code python dans une procédure stockée, fournir des entrées et l’exécution d’une procédure stockée. |
| [Tutoriel : Créer un modèle à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md) | Montre comment exécuter du code à partir d’un terminal python distant, à l’aide d’SQL Server contexte de calcul. Vous devez être familiarisé avec les outils et environnements Python. Un exemple de code est fourni pour créer un modèle à l’aide de **rxLinMod**, à partir de la nouvelle bibliothèque **revoscalepy** . |
| [Tutoriel : Découvrez les analyses python dans la base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md) | Cette procédure pas à pas de bout en bout illustre le processus de création d’une solution python complète à l’aide de procédures stockées T-SQL. Tout le code Python est inclus.|

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Exemples de code

Ces exemples et démonstrations fournis par l’équipe de développement SQL Server mettent en évidence des moyens d’utiliser des analyses incorporées dans des applications réelles.

| Lien | Description |
|------|-------------|
| [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Découvrez comment une entreprise de location de ski peut utiliser Machine Learning pour prédire les futurs loyers, ce qui aide le plan et le personnel de l’entreprise à répondre à la demande future. |
| [Effectuer un clustering client à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Découvrez comment utiliser l’algorithme KMeans pour effectuer un clustering de clients non supervisé. |

## <a name="see-also"></a>Voir aussi

+ [Extension Python à SQL Server](../concepts/extension-python.md)
+ [Didacticiels de Machine Learning Services SQL Server](machine-learning-services-tutorials.md)
