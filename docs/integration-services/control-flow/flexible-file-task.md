---
title: Flexible File Task | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPEXTFILETASK.F1
- SQL14.DTS.DESIGNER.AFPEXTFILETASK.F1
author: janinezhang
ms.author: janinez
ms.openlocfilehash: cc95201ec856d5e7daa998c7de52b91981af5552
ms.sourcegitcommit: 2efb0fa21ff8093384c1df21f0e8910db15ef931
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68316639"
---
# <a name="flexible-file-task"></a>Tâche de fichier flexible

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Flexible File Task permet aux utilisateurs d’effectuer des opérations de fichiers sur divers services de stockage pris en charge.
Les services de stockage actuellement pris en charge sont :

- Système de fichiers local
- [Stockage Blob Azure](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)

Flexible File Task est un composant du [Feature Pack SQL Server Integration Services (SSIS) pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Pour ajouter une tâche Flexible File Task à un package, faites-la glisser de la boîte à outils SSIS vers la zone de conception. Ensuite, double-cliquez sur la tâche, ou cliquez dessus avec le bouton droit et sélectionnez **Modifier**, pour ouvrir la boîte de dialogue **Flexible File Task Editor**.

La propriété **Operation** indique l’opération de fichier à réaliser.
Seule l’opération **Copy** est actuellement prise en charge.

Pour l’opération **Copy**, les propriétés suivantes sont disponibles.

- **SourceConnectionType :** spécifie le type de gestionnaire de connexions source.
- **SourceConnection :** spécifie le gestionnaire de connexions source.
- **SourceFolderPath :** spécifie le chemin du dossier source.
- **SourceFileName :** spécifie le nom du fichier source. Si ce champ est vide, le dossier source sera copié.
- **SearchRecursively :** spécifie s’il faut copier les sous-dossiers de manière récursive.
- **DestinationConnectionType :** spécifie le type de gestionnaire de connexions de destination.
- **DestinationConnection :** spécifie le gestionnaire de connexions de destination.
- **DestinationFolderPath :** spécifie le chemin du dossier de destination.
- **DestinationFileName :** spécifie le nom du fichier de destination.

***Remarques sur la configuration des autorisations du principal de service***

Pour que la **connexion de test** fonctionne (soit le stockage d’objets blob, soit Data Lake Storage Gen2), le principal de service doit disposer au moins du rôle **Lecteur des données Blob du stockage** pour le compte de stockage.
Cette opération s’effectue à l’aide de [RBAC](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).

Pour le stockage d’objets blob, des autorisations de lecture et d’écriture sont accordées en affectant au moins les rôles **Lecteur des données Blob du stockage**  et **Contributeur aux données Blob du stockage**, respectivement.

Pour Data Lake Storage Gen2, l’autorisation est déterminée à la fois par RBAC et par des [listes des contrôles d’accès (ACL)](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-how-to-set-permissions-storage-explorer).
Faites attention à ce que les listes de contrôle d’accès soient configurées à l’aide de l’ID d’objet (OID) du principal de service pour l’inscription d’application, comme indiqué [ici](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control#how-do-i-set-acls-correctly-for-a-service-principal).
Cet ID diffère de l’ID d’application (client) utilisé avec la configuration RBAC.
Quand un principal de sécurité reçoit des autorisations sur les données RBAC par le biais d’un rôle intégré ou personnalisé, ces autorisations sont évaluées en premier lors de l’autorisation d’une demande.
Si l’opération demandée est autorisée par les attributions RBAC du principal de sécurité, l’autorisation est immédiatement résolue et aucune vérification de liste de contrôle d’accès supplémentaire n’est effectuée.
Sinon, si le principal de sécurité n’a pas d’attribution RBAC ou si l’opération de la demande ne correspond pas à l’autorisation affectée, les vérifications de liste de contrôle d’accès sont effectuées pour déterminer si le principal de sécurité est autorisé à effectuer l’opération demandée.

- Pour l’autorisation de lecture, accordez au moins l’autorisation d’**Exécution** à partir du système de fichiers source, ainsi que l’autorisation de **Lecture** pour les fichiers à copier. Vous pouvez également accorder au moins le rôle **Lecteur des données Blob du stockage** avec RBAC.
- Pour l’autorisation d’écriture, accordez au moins l’autorisation d’**Exécution** à partir du système de fichiers récepteur, ainsi que l’autorisation d’**Écriture** pour le dossier récepteur. Vous pouvez également accorder au moins le rôle **Contributeur aux données Blob du stockage** avec RBAC.

Pour plus d’informations, consultez [cet](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control) article.
