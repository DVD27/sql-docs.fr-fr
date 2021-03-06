---
title: Informations de référence sur azdata bdc
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0a2891256bd6e45de356d620d3fa75256528b697
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68894011"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **bdc** dans l’outil **azdata**. Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes

|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | Crée un cluster Big Data.
[azdata bdc delete](#azdata-bdc-delete) | Supprime un cluster Big Data.
[azdata bdc config](reference-azdata-bdc-config.md) | Commandes de configuration.
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | Commandes relatives aux points de terminaison.
[azdata bdc status](reference-azdata-bdc-status.md) | Commandes relatives à l’état.
[azdata bdc debug](reference-azdata-bdc-debug.md) | Commandes de débogage.
[azdata bdc control](reference-azdata-bdc-control.md) | Commandes de contrôle.
[azdata bdc pool](reference-azdata-bdc-pool.md) | Commandes relatives aux pools.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Le module HDFS fournit des commandes pour accéder à un système de fichiers HDFS.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Les commandes Spark permettent à l’utilisateur d’interagir avec le système Spark en créant et en gérant des sessions, des instructions et des lots.
## <a name="azdata-bdc-create"></a>azdata bdc create
Crée un cluster Big Data SQL Server - Vous devez avoir une configuration Kube sur votre système, ainsi que les variables d’environnement suivantes : ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD', 'MSSQL_SA_PASSWORD', 'KNOX_PASSWORD'].
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>Exemples

Déploiement guidé de BDC : vous serez invité à entrer les valeurs nécessaires.

```bash
azdata bdc create
```

Déploiement de BDC avec des arguments.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
Déploiement de BDC avec le nom spécifié au lieu du nom par défaut du profil.
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```

Déploiement de BDC avec des arguments : aucune invite ne s’affiche, car l’indicateur --force est utilisé.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```

### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du cluster Big Data, utilisé pour les espaces de noms Kubernetes.
#### `--config-profile -c`
Profil de configuration de cluster Big Data, utilisé pour le déploiement du cluster : ['aks-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence ? [oui/non]. Si vous ne voulez pas utiliser cet argument, vous pouvez définir la variable d’environnement ACCEPT_EULA sur « oui ». Vous pouvez consulter les termes du contrat de licence de [https://go.microsoft.com/fwlink/?LinkId=2002534](https://go.microsoft.com/fwlink/?LinkId=2002534)ce produit à l’adresse.
#### `--node-label -l`
Étiquette de nœud de cluster Big Data, utilisée pour désigner les nœuds sur lesquels effectuer le déploiement.
#### `--force -f`
Création forcée. L’utilisateur ne sera pas invité à entrer des valeurs, et les éventuels problèmes seront affichés dans le cadre d’une erreur standard.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmenter le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et quitter.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmenter le niveau de détail de la journalisation. Utilisez --debug pour obtenir des journaux de débogage complets.
## <a name="azdata-bdc-delete"></a>azdata bdc delete
Supprime le cluster Big Data SQL Server - Vous devez avoir une configuration Kube sur votre système, ainsi que les variables d’environnement suivantes : ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD'].
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Exemples
Suppression de BDC où le nom d’utilisateur et le mot de passe du contrôleur sont déjà définis dans votre environnement système.
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du cluster Big Data, utilisé pour l’espace de noms Kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--force -f`
Suppression forcée du cluster Big Data.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmenter le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et quitter.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmenter le niveau de détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
