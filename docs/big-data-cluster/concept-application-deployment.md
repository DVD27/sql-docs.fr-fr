---
title: Présentation du déploiement d’application
titleSuffix: SQL Server Big Data Clusters
description: Cet article décrit le déploiement d’application sur un cluster Big Data pour SQL Server 2019.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4b647ab4d03d110ce303388a8b62461f28033b6c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "76831569"
---
# <a name="what-is-application-deployment-on-a-big-data-cluster"></a>Présentation du déploiement d’application sur un cluster Big Data

Le déploiement d’application sur le cluster Big Data s’effectue au moyen d’interfaces conçues pour créer, gérer et exécuter des applications. Les applications déployées sur le cluster Big Data bénéficient de la puissance de calcul du cluster et peuvent accéder aux données disponibles sur le cluster. Vous augmentez ainsi la scalabilité et les performances des applications tout en gérant les applications où résident les données. Les runtimes d’application pris en charge sur les clusters Big Data SQL Server sont R, Python, SSIS et MLeap.

Les sections suivantes décrivent l’architecture et les fonctionnalités du déploiement d’application.

## <a name="application-deployment-architecture"></a>Architecture du déploiement d’application

Le déploiement d’application passe par un contrôleur et des gestionnaires d’exécution d’application. Quand vous créez une application, un fichier de spécification (`spec.yaml`) est fourni. Ce fichier `spec.yaml` contient tout ce que le contrôleur doit savoir pour déployer correctement l’application. Voici un exemple du contenu de `spec.yaml` :

```yaml
#spec.yaml
name: add-app #name of your python script
version: v1  #version of the app
runtime: Python #the language this app uses (R or Python)
src: ./add.py #full path to the location of the app
entrypoint: add #the function that will be called upon execution
replicas: 1  #number of replicas needed
poolsize: 1  #the pool size that you need your app to scale
inputs:  #input parameters that the app expects and the type
  x: int
  y: int
output: #output parameter the app expects and the type
  result: int
```

Le contrôleur inspecte le `runtime` spécifié dans le fichier `spec.yaml` et appelle le gestionnaire d’exécution correspondant. Le gestionnaire d’exécution crée l’application. Tout d’abord, un ReplicaSet Kubernetes est créé avec un ou plusieurs pods, chacun d’eux contenant l’application à déployer. Le nombre de pods est défini par le paramètre `replicas` défini dans le fichier `spec.yaml` de l’application. Chaque pod peut avoir un ou plusieurs pools. Le nombre de pools est défini par le paramètre `poolsize` défini dans le fichier `spec.yaml`.

Ces paramètres ont un impact sur la quantité de demandes que le déploiement peut traiter en parallèle. Le nombre maximal de demandes à un moment donné est égal à `replicas` fois `poolsize`. Si vous avez 5 réplicas et 2 pools par réplica, le déploiement peut donc gérer 10 demandes en parallèle. L’image ci-dessous est une représentation graphique de `replicas` et de `poolsize` :

![Taille de pool et réplicas](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Une fois le ReplicaSet créé et les pods démarrés, un travail cron est créé si un `schedule` a été défini dans le fichier `spec.yaml`. Enfin, le service Kubernetes créé peut être utilisé pour gérer et exécuter l’application (voir ci-dessous).

Quand une application est exécutée, le service Kubernetes pour l’application transmet par proxy les demandes à un réplica et retourne les résultats.

## <a name="how-to-work-with-application-deployment"></a>Comment utiliser le déploiement d’application

Les deux interfaces principales pour le déploiement d’application sont les suivantes : 
- [Interface de ligne de commande `azdata`](big-data-cluster-create-apps.md)
- [Visual Studio Code et extension Azure Data Studio](app-deployment-extension.md)

Vous pouvez également exécuter une application à l’aide d’un service web RESTful. Pour plus d’informations, consultez [Utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la création et l’exécution d’applications sur des [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez les rubriques suivantes :

- [Déployer des applications avec azdata](big-data-cluster-create-apps.md)
- [Déployer des applications à l’aide de l’extension de déploiement d’application](app-deployment-extension.md)
- [Utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md)

Pour plus d’informations sur les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], consultez la vue d’ensemble suivante :

- [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md)
