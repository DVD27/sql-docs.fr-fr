---
title: Conseils pour le déploiement
titleSuffix: SQL Server big data clusters
description: Découvrez comment déployer des clusters Big Data SQL Server 2019 (préversion) sur Kubernetes.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b7439fdc93f04ad137b0bb65269b9767d8281798
ms.sourcegitcommit: 58f1d5498c87bfe0f6ec4fd9d7bbe723be47896b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995833"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Comment déployer des clusters Big Data SQL Server sur Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Un cluster Big Data SQL Server est déployé sous la forme de conteneurs Docker sur un cluster Kubernetes. Voici une vue d’ensemble des étapes d’installation et de configuration :

- Configurez un cluster Kubernetes sur une seule machine virtuelle, un cluster de machines virtuelles ou dans AKS (Azure Kubernetes Service).
- Installez l’outil de configuration de cluster **azdata** sur votre machine cliente.
- Déployez un cluster Big Data SQL Server dans un cluster Kubernetes.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>Installer les outils de Big Data SQL Server

Avant de déployer un cluster Big Data SQL Server 2019, commencez par [installer les outils de Big Data](deploy-big-data-tools.md) :

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **Extension SQL Server 2019**

## <a id="prereqs"></a> Kubernetes - Prérequis

Les clusters Big Data SQL Server nécessitent au minimum Kubernetes version 1.10 sur le serveur et le client (kubectl).

> [!NOTE]
> Notez que la différence entre les versions mineures de Kubernetes sur le client et le serveur ne doit pas dépasser +1 ou -1. Pour plus d’informations, consultez [les notes de publication de Kubernetes et la stratégie en matière de différence de version pour les références SKU](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a> Configuration du cluster Kubernetes

Si vous avez déjà un cluster Kubernetes qui répond aux prérequis ci-dessus, vous pouvez passer directement à l’[étape de déploiement](#deploy). Cette section suppose que vous disposez de connaissances de base sur les concepts de Kubernetes.  Pour obtenir des informations plus détaillées, consultez la [documentation de Kubernetes](https://kubernetes.io/docs/home).

Vous pouvez choisir de déployer Kubernetes de trois manières :

| Déployer Kubernetes sur : | Description | Lien |
|---|---|---|
| **Azure Kubernetes Services (AKS)** | Service de conteneur Kubernetes managé dans Azure. | [Instructions](deploy-on-aks.md) |
| **Plusieurs machines (kubeadm)** | Cluster Kubernetes déployé sur des machines physiques ou virtuelles à l’aide de **kubeadm**. | [Instructions](deploy-with-kubeadm.md) |
| **Minikube** | Cluster Kubernetes à un seul nœud dans une machine virtuelle. | [Instructions](deploy-on-minikube.md) |

> [!TIP]
> Vous pouvez également générer un script pour déployer AKS et un cluster Big Data en une seule étape. Pour plus d’informations, consultez la procédure à suivre dans un [script Python](quickstart-big-data-cluster-deploy.md) ou dans un [notebook](deploy-notebooks.md) Azure Data Studio.

### <a name="verify-kubernetes-configuration"></a>Vérifier la configuration de Kubernetes

Exécutez la commande **kubectl** pour afficher la configuration du cluster. Vérifiez que kubectl pointe vers le bon contexte de cluster.

```bash
kubectl config view
```

Après avoir configuré votre cluster Kubernetes, vous pouvez passer au déploiement d’un nouveau cluster Big Data SQL Server. Si vous effectuez une mise à niveau à partir d’une version précédente, consultez [Guide pratique pour mettre à niveau des clusters Big Data SQL Server](deployment-upgrade.md).

## <a id="deploy"></a> Vue d’ensemble du déploiement

La plupart des paramètres de cluster Big Data sont définis dans un fichier de configuration de déploiement JSON. Vous pouvez utiliser un profil de déploiement par défaut pour AKS, `kubeadm` ou `minikube`, ou vous pouvez personnaliser un fichier de configuration de déploiement et l’utiliser pendant l’installation. Pour des raisons de sécurité, les paramètres d’authentification sont passés par le biais de variables d’environnement.

Les sections suivantes fournissent plus d’informations sur la façon de configurer vos déploiements de cluster Big Data, ainsi que des exemples de personnalisations courantes. Sachez que vous pouvez toujours modifier le fichier de configuration de déploiement personnalisé à l’aide d’un éditeur comme VS Code.

## <a id="configfile"></a> Configurations par défaut

Les options de déploiement d’un cluster Big Data sont définies dans les fichiers de configuration JSON. Il existe trois profils de déploiement standard avec des paramètres par défaut pour les environnements de développement et de test :

| Profil de déploiement | Environnement Kubernetes |
|---|---|
| **aks-dev-test** | Azure Kubernetes Service (AKS) |
| **kubeadm-dev-test** | Plusieurs machines (kubeadm) |
| **minikube-dev-test** | minikube |

Vous pouvez déployer un cluster Big Data en exécutant **azdata bdc create**. Vous êtes alors invité à choisir l’une des configurations par défaut, puis à suivre la procédure de déploiement.

La première fois que vous exécutez `azdata`, vous devez inclure `--accept-eula=yes` pour accepter le contrat de licence utilisateur final (CLUF).

```bash
azdata bdc create --accept-eula=yes
```

Dans ce scénario, vous êtes invité à fournir tous les paramètres qui ne font pas partie de la configuration par défaut, notamment les mots de passe. 

> [!IMPORTANT]
> Par défaut, le cluster Big Data est nommé **mssql-cluster**. Il est important de le connaître si vous souhaitez exécuter l’une des commandes **kubectl** spécifiant l’espace de noms Kubernetes avec le paramètre `-n`.

## <a id="customconfig"></a> Configurations personnalisées

Vous pouvez également personnaliser votre propre profil de configuration de déploiement. Pour cela, effectuez les étapes suivantes :

1. Commencez par l’un des profils de déploiement standard correspondant à votre environnement Kubernetes. Vous pouvez utiliser la commande **azdata bdc config list** pour les lister :

   ```bash
   azdata bdc config list
   ```

1. Pour personnaliser votre déploiement, créez une copie du profil de déploiement avec la commande **azdata bdc config init**. Par exemple, la commande suivante crée une copie des fichiers de configuration de déploiement **aks-dev-test** dans un répertoire cible nommé `custom` :

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

   azdata
   > `--target` spécifie un répertoire qui contient les fichiers de configuration **cluster.json** and **control.json**, en fonction du paramètre`--source`.

1. Pour personnaliser les paramètres dans votre profil de configuration de déploiement, vous pouvez modifier le fichier de configuration de déploiement dans un outil adapté à la modification des fichiers JSON, par exemple VS Code. Pour une automatisation par script, vous pouvez également modifier le profil de déploiement personnalisé à l’aide de la commande **azdata bdc config**. Par exemple, la commande suivante modifie un profil de déploiement personnalisé en remplaçant le nom par défaut du cluster déployé (**mssql-cluster**) par **test-cluster** :  

   ```bash
   azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
   ```
   
> [!TIP]
> Vous pouvez également passer le nom du cluster au moment du déploiement à l’aide du paramètre *--name* pour la commande *azdata create bdc*. Les paramètres dans la commande ont priorité sur les valeurs dans les fichiers de configuration.

   > [JSONPath Online Evaluator](https://jsonpath.com/) est un outil utile pour rechercher des chemins JSON.

   En plus de passer des paires clé-valeur, vous pouvez également fournir des valeurs JSON inline ou passer des fichiers de correctif JSON. Pour plus d’informations, consultez [Configurer les paramètres de déploiement de clusters Big Data](deployment-custom-configuration.md).

1. Passez ensuite le fichier de configuration personnalisé à **azdata bdc create**. Notez que vous devez définir les [variables d’environnement](#env) exigées ; sinon, vous serez invité à entrer des valeurs :

   ```bash
   azdata bdc create --config-profile custom --accept-eula yes
   ```

> Pour plus de détails sur la structure d’un fichier de configuration de déploiement, consultez ces [informations de référence](reference-deployment-config.md). Pour obtenir d’autres exemples de configuration, consultez [Configurer les paramètres de déploiement de clusters Big Data](deployment-custom-configuration.md).

## <a id="env"></a> Variables d’environnement

Les variables d’environnement suivantes sont utilisées pour les paramètres de sécurité qui ne sont pas stockés dans un fichier de configuration de déploiement. Notez que les paramètres Docker, à l’exception des informations d’identification, peuvent être définis dans le fichier de configuration.

| Variable d'environnement | Prérequis |Description |
|---|---|---|
| **CONTROLLER_USERNAME** | Obligatoire |Nom d’utilisateur de l’administrateur de cluster. |
| **CONTROLLER_PASSWORD** | Obligatoire |Mot de passe de l’administrateur du cluster. |
| **MSSQL_SA_PASSWORD** | Obligatoire |Mot de passe de l’utilisateur désigné comme administrateur système pour l’instance maître SQL. |
| **KNOX_PASSWORD** | Obligatoire |Mot de passe de l’utilisateur Knox. |
| **ACCEPT_EULA**| Obligatoire pour la première utilisation de `azdata`| Ne nécessite aucune valeur. Si vous la définissez en tant que variable d’environnement, elle applique le CLUF à SQL Server et `azdata`. Si vous ne la définissez pas en tant que variable d’environnement, vous pouvez inclure `--accept-eula` dans la première utilisation de la commande `azdata`.|
| **DOCKER_USERNAME** | Facultatif | Nom d’utilisateur utilisé pour accéder aux images de conteneur si elles sont stockées dans un dépôt privé. Pour plus d’informations sur l’utilisation d’un dépôt Docker privé pour le déploiement d’un cluster Big Data, consultez la rubrique [Déploiements hors connexion](deploy-offline.md).|
| **DOCKER_PASSWORD** | Facultatif |Mot de passe nécessaire pour accéder au dépôt privé ci-dessus. |

Ces variables d’environnement doivent être définies avant d’appeler **azdata bdc create**. Si une variable n’est pas définie, vous êtes invité à le faire.

L’exemple suivant montre comment définir les variables d’environnement pour Linux (bash) et Windows (PowerShell) :

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
```

Après avoir défini les variables d’environnement, vous devez exécuter `azdata bdc create` pour déclencher le déploiement. Cet exemple utilise le profil de configuration de cluster créé ci-dessus :

```bash
azdata bdc create --config-profile custom --accept-eula yes
```

Notez les consignes suivantes :

- Veillez à inclure le mot de passe entre guillemets doubles s’il contient des caractères spéciaux. Vous pouvez définir **MSSQL_SA_PASSWORD** avec la valeur de votre choix, mais veillez à ce que le mot de passe soit suffisamment complexe et n’utilisez pas les caractères `!`, `&` ou `'`. Notez que les délimiteurs de guillemets doubles fonctionnent uniquement dans les commandes bash.
- La connexion **SA** est un administrateur système sur l’instance maître SQL Server dont la création a lieu lors de l’installation. Une fois le conteneur SQL Server créé, la variable d’environnement **MSSQL_SA_PASSWORD** que vous avez spécifiée peut être découverte en exécutant `echo $MSSQL_SA_PASSWORD` dans le conteneur. Pour des raisons de sécurité, changez le mot de passe de l’administrateur système conformément aux bonnes pratiques décrites [ici](../linux/quickstart-install-connect-docker.md#sapassword).

## <a id="unattended"></a> Installation sans assistance

Pour un déploiement sans assistance, vous devez définir toutes les variables d’environnement nécessaires, utiliser un fichier de configuration et appeler la commande `azdata bdc create` avec le paramètre `--accept-eula yes`. Les exemples de la section précédente illustrent la syntaxe d’une installation sans assistance.

## <a id="monitor"></a> Superviser le déploiement

Durant l’amorçage du cluster, la fenêtre de commande du client indique l’état du déploiement. Vous devez ensuite voir une série de messages indiquant que le processus de déploiement attend le pod du contrôleur :

```output
Waiting for cluster controller to start.
```

Après 15 à 30 minutes, vous devez être informé que le pod du contrôleur est en cours d’exécution :

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> L’ensemble du processus de déploiement peut durer longtemps en raison du temps nécessaire au téléchargement des images conteneur pour les composants du cluster Big Data. Il ne devrait cependant pas prendre plusieurs heures. Si vous rencontrez des problèmes avec votre déploiement, consultez [Supervision des clusters Big Data SQL Server et résolution des problèmes](cluster-troubleshooting-commands.md).

Une fois le déploiement terminé, vous êtes notifié dans la sortie :

```output
Cluster deployed successfully.
```

> [!TIP]
> Le nom par défaut du cluster Big Data déployé est `mssql-cluster`, sauf s’il est modifié par une configuration personnalisée.

## <a id="endpoints"></a> Récupérer des points de terminaison

Une fois le script de déploiement terminé, vous pouvez obtenir les adresses IP des points de terminaison externes du cluster Big Data en effectuant les étapes suivantes.

1. Après le déploiement, vous trouverez l’adresse IP du point de terminaison du contrôleur dans la sortie standard du déploiement ou la sortie EXTERNAL-IP de la commande **kubectl** suivante :

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Si vous n’avez pas changé le nom par défaut durant le déploiement, utilisez `-n mssql-cluster` dans la commande précédente. **mssql-cluster** est le nom par défaut du cluster Big Data.

1. Connectez-vous au cluster Big Data avec [azdata login](reference-azdata.md). Affectez au paramètre **--controller-endpoint** l’adresse IP externe du point de terminaison du contrôleur.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Spécifiez le nom d’utilisateur et le mot de passe que vous avez configurés pour le contrôleur (CONTROLLER_USERNAME et CONTROLLER_PASSWORD) durant le déploiement.

1. Exécutez [azdata bdc endpoint list](reference-azdata-bdc-endpoint.md) pour obtenir une liste comprenant la description de chaque point de terminaison ainsi que les adresses IP et ports correspondants. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   La liste suivante montre un exemple de sortie de cette commande :

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

Vous pouvez également obtenir tous les points de terminaison de service déployés pour le cluster en exécutant la commande **kubectl** suivante :

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

### <a name="minikube"></a>Minikube

Si vous utilisez minikube, vous devez exécuter la commande suivante pour récupérer l’adresse IP à laquelle vous devez vous connecter. En plus de l’adresse IP, spécifiez le port du point de terminaison auquel vous devez vous connecter.

```bash
minikube ip
```

## <a id="status"></a> Vérifier l’état du cluster

Après le déploiement, vous pouvez vérifier l’état du cluster à l’aide de la commande [azdata bdc status show](reference-azdata-bdc-status.md).

```bash
azdata bdc status show -o table
```

> [!TIP]
> Pour exécuter les commandes d’état, vous devez d’abord vous connecter à l’aide de la commande **azdata login** (présentée dans la section précédente sur les points de terminaison).

Voici un exemple de sortie de cette commande :

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

Dans cet état résumé, vous pouvez également obtenir un état plus détaillé avec les commandes suivantes :

- [azdata bdc control status](reference-azdata-bdc-control-status.md)
- [azdata bdc pool status](reference-azdata-bdc-pool-status.md)

La sortie de ces commandes contient des URL aux tableaux de bord Kibana et Grafana pour une analyse plus détaillée.

Outre **azdata**, vous pouvez utiliser Azure Data Studio pour trouver les points de terminaison et des informations sur l’état. Pour plus d’informations sur l’affichage de l’état d’un cluster avec **azdata** et Azure Data Studio, consultez [Guide pratique pour afficher l’état d’un cluster Big Data](view-cluster-status.md).

## <a id="connect"></a> Se connecter au cluster

Pour plus d’informations sur la façon de se connecter au cluster Big Data, consultez [Se connecter à un cluster Big Data SQL Server avec Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le déploiement d’un cluster Big Data, consultez les ressources suivantes :

- [Configurer les paramètres de déploiement de clusters Big Data](deployment-custom-configuration.md).
- [Effectuer un déploiement hors connexion d’un cluster Big Data SQL Server](deploy-offline.md)
- [Atelier : Architecture des clusters Big Data Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
