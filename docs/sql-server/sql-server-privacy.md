---
title: Avenant à la déclaration de confidentialité de SQL Server | Microsoft Docs
ms.date: 01/19/2019
ms.prod: sql
ms.reviewer: mikeray
ms.custom: ''
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords: ''
author: aliceku
ms.author: aliceku
ms.openlocfilehash: 40057200c5b8241849f4030e6c418cf080d149f2
ms.sourcegitcommit: 73dc08bd16f433dfb2e8406883763aabed8d8727
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68329341"
---
# <a name="sql-server-privacy-supplement"></a>Avenant à la déclaration de confidentialité de SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article résume les fonctionnalités Internet qui peuvent collecter et envoyer à Microsoft des données anonymes de diagnostic et d’utilisation des fonctionnalités. SQL Server peut collecter des informations informatiques standard, et les données sur l’utilisation et les performances peuvent être transmises à Microsoft et analysées dans le but d’améliorer la qualité, la sécurité et la fiabilité du produit. Cet article fait office d’addendum à la [déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) générale. La classification des données dans cet article s’applique uniquement aux versions du produit SQL Server local. Elle ne s'applique pas aux éléments suivants :

- Azure SQL Database
- [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/en-us/sql/ssms/sql-server-management-studio-telemetry-ssms?view=sql-server-2017)
- SQL Server Data Tools (SSDT)
- Azure Data Studio
- Database Migration Assistant
- Assistant Migration SQL Server
- Extension MS-SQL

Définition des *scénarios d’usages autorisés*. Dans le contexte de cet article, Microsoft définit les « Scénarios d’usages autorisés » comme des actions ou activités démarrées par Microsoft.

## <a name="access-control"></a>Contrôle d’accès

Détails des informations d’identification utilisées pour sécuriser les connexions, utilisateurs ou comptes au sein d’une installation de SQL Server.

### <a name="examples-of-access-control"></a>Exemples de contrôle d’accès

- Mots de passe
- Certificats

### <a name="permitted-usage-scenarios"></a>Scénarios d’usages autorisés

|Scénario |Restrictions d'accès |Conditions de rétention |
|---------|---------|---------|
|Ces informations d’identification ne quittent jamais l’ordinateur de l’utilisateur par le biais des données d’utilisation et de diagnostic. |- |- |
|Les images mémoire peuvent contenir des données de contrôle d’accès. |- |Vidages sur incident : 30 jours maximum. |
|Ces informations d’identification ne quittent jamais l’ordinateur de l’utilisateur via les Commentaires des utilisateurs, sauf si le client les indique manuellement |Limité à un usage interne Microsoft sans accès à des tiers. |Commentaires des utilisateurs : 1 an maximum|
|&nbsp;|&nbsp;|&nbsp;|

## <a name="customer-content"></a>Contenu client

Le contenu client est défini comme les données stockées dans les tables utilisateur, directement ou indirectement. Les données sont notamment des statistiques ou des littéraux d’utilisateur dans les textes de requête qui peuvent être stockés dans les tables utilisateur.

### <a name="examples-of-customer-content"></a>Exemples de contenu client

- Valeurs de données stockées dans les lignes d’une table utilisateur.
- Objets de statistiques contenant des copies des valeurs contenues dans les lignes d’une table utilisateur.
- Textes de requête contenant des valeurs littérales.

### <a name="permitted-usage-scenarios"></a>Scénarios d’usages autorisés

|Scénario  |Restrictions d'accès  |Conditions de rétention |
|---------|---------|---------|
|Ces données ne quittent jamais l’ordinateur de l’utilisateur par le biais des données d’utilisation et de diagnostic. |- |- |
|Les images mémoire peuvent contenir du contenu de client et être envoyées à Microsoft. |- |Vidages sur incident : 30 jours max. |
|Les clients avec leur consentement peuvent envoyer via les Commentaires des utilisateurs du contenu client à Microsoft. |Limité à un usage interne Microsoft sans accès à des tiers. Microsoft peut exposer les données au client d’origine. |Commentaires des utilisateurs : 1 an maximum |

## <a name="end-user-identifiable-information-euii"></a>Informations d’identification de l’utilisateur final (EUII)

Données reçues d’un utilisateur ou générées par son utilisation du produit.
- Pouvant être liées à un utilisateur individuel.
- Sans contenu.

### <a name="examples-of-end-user-identifiable-information"></a>Exemples d’informations d’identification de l’utilisateur final

- Identification de l’interface. Adresse IP complète
- Nom de l’ordinateur
- Noms de la connexion/de l’utilisateur
- Partie locale de l’adresse e-mail (joe@contoso.com)
- Informations de localisation
- Identification du client

### <a name="permitted-usage-scenarios"></a>Scénarios d’usages autorisés

|Scénario  |Restrictions d'accès  |Conditions de rétention|
|---------|---------|---------|
|Ces données ne quittent jamais l’ordinateur de l’utilisateur par le biais des données d’utilisation et de diagnostic. |- |- |
|Les images mémoire peuvent contenir des informations EUII et être envoyées à Microsoft. |- |Vidages sur incident : 30 jours max |
|L’ID d’identification du client peut être envoyé à Microsoft pour distribuer des nouvelles fonctionnalités hybrides et cloud auxquelles l’utilisateur s’est abonné. |- |Actuellement, ces fonctionnalités cloud ou hybrides n’existent pas.|
|Les clients avec leur consentement peuvent envoyer via les Commentaires des utilisateurs du contenu client à Microsoft.|Limité à un usage interne Microsoft sans accès à des tiers. Microsoft peut exposer les données au client d’origine. |Commentaires des utilisateurs : 1 an maximum |

## <a name="internet-based-services-data"></a>Données des services Internet

Données nécessaires pour fournir des services Internet, d’après le CLUF de SQL Server.

### <a name="examples-of-internet-based-services-data"></a>Exemples de données de services Internet

- Informations sur les spécifications de l’ordinateur
- Nom/version du navigateur
- Version de SQL Server
- Code langue
- Adresse IP avec certains octets supprimés
- Données cartographiques

### <a name="permitted-usage-scenarios"></a>Scénarios d’usages autorisés

|Scénario  |Restrictions d'accès  |Conditions de rétention|
|---------|---------|---------| 
|Peut être utilisé par Microsoft pour améliorer les fonctionnalités et/ou corriger les bogues dans les fonctionnalités actuelles. |Limité à un usage interne Microsoft sans accès à des tiers. Microsoft peut exposer les données au client d’origine.  Par exemple, les tableaux de bord |90 jours minimum, 3 ans maximum |
|Les clients avec leur consentement peuvent envoyer via les Commentaires des utilisateurs du contenu client à Microsoft. |Limité à un usage interne Microsoft sans accès à des tiers. |Les clients avec leur consentement peuvent envoyer via les Commentaires des utilisateurs du contenu client à Microsoft. |
|Les éléments cartographiques Power View et SQL Reporting Services peuvent envoyer des données pour l’utilisation de Bing Maps. |Limité aux données de session |- |

## <a name="system-metadata"></a>Métadonnées système

Données générées au cours de l’exécution du serveur.  Les données ne contiennent pas de contenu client.

### <a name="examples-of-system-metadata"></a>Exemples de métadonnées système

Les éléments suivants sont considérés comme des métadonnées système quand ils n’ont pas de contenu client, de métadonnées d'objet, de données de contrôle d’accès client ou d’informations EUII :

- GUID de la base de données
- Code de hachage du nom de l’ordinateur
- Code de hachage du nom de l’instance
- Nom de l'application
- Données comportementales/d’utilisation
- Données du programme d’amélioration du produit SQL (SQLCEIP)
- Données de configuration du serveur, par exemple les paramètres de sp_configure
- Données de configuration des fonctionnalités
- Noms d’événement et codes d’erreur
- Paramètres matériels et identification, tels que le fabricant OEM

Microsoft examine les valeurs de nom d’application définies par d’autres programmes qui utilisent SQL Server (exemple : SharePoint ou programmes packagés tiers et inclut cette information dans les métadonnées système envoyées à Microsoft lorsque les Données d’utilisation sont activées). Les clients ne doivent pas placer de données personnelles, comme les informations d’identification de l’utilisateur final, dans les champs Métadonnées système ni créer d’applications conçues pour stocker des données personnelles dans ces champs. 

### <a name="permitted-usage-scenarios"></a>Scénarios d’usages autorisés

|Scénario  |Restrictions d'accès  |Conditions de rétention|
|---------|---------|---------|
|Peut être utilisé par Microsoft pour améliorer les fonctionnalités ou corriger les bogues dans les fonctionnalités actuelles.|Limité à un usage interne Microsoft sans accès à des tiers. |90 jours minimum, 3 ans maximum |
|Peut être utilisé pour faire des suggestions au client.  Par exemple, « D’après votre utilisation du produit, utilisez la fonctionnalité *X* pour obtenir de meilleures performances ». |Microsoft peut exposer les données au client d’origine, par exemple, à travers des tableaux de bord. |Journaux de sécurité des données client : 3 ans min - 6 ans max |
|Peut être utilisé par Microsoft pour la planification du produit futur. |Microsoft peut partager ces informations avec d’autres fournisseurs de matériel et de logiciel afin d’améliorer le fonctionnement de leurs produits exécutés avec les logiciels Microsoft. |90 jours minimum, 3 ans maximum|
|Peut être utilisé par Microsoft pour fournir des services cloud basés sur les données d’utilisation et de diagnostic envoyées. Par exemple, le tableau de bord d’un client affichant l’utilisation des fonctionnalités sur toutes les installations de SQL Server dans une organisation. |Microsoft peut exposer les données au client d’origine, par exemple, à travers des tableaux de bord. |90 jours minimum, 3 ans maximum |
|Les clients avec leur consentement peuvent envoyer via les Commentaires des utilisateurs du contenu client à Microsoft. |Limité à un usage interne Microsoft sans accès à des tiers. Microsoft peut exposer les données au client d’origine. |Commentaires des utilisateurs : 1 an maximum |
|Peut utiliser les noms de base de données et les noms d’application pour classer les bases de données et les applications dans des catégories connues, par exemple, celles susceptibles d’exécuter des logiciels fournis par Microsoft ou d’autres sociétés.|Limité à un usage interne Microsoft sans accès à des tiers.|90 jours minimum, 3 ans maximum |

## <a name="object-metadata"></a>les métadonnées d'objets.

Données qui décrivent ou sont utilisées pour configurer des serveurs, des bases de données, des tables et d’autres ressources.  Les métadonnées d’objet sont notamment les noms de table et de colonne de base de données, mais pas le contenu des lignes de base de données ou un autre contenu client. Les clients ne doivent pas placer de données personnelles, comme les informations d’identification de l’utilisateur final, dans les champs de métadonnées d’objet ni créer d’applications conçues pour stocker des données personnelles dans ces champs. Pour le scénario d’usage autorisé ci-dessous, seul le formulaire de hachage est utilisé pour déterminer les modèles d’usage visant à améliorer le produit. 

### <a name="examples-of-object-metadata"></a>Exemples de métadonnées d'objet

- Noms de base de données SQL Server
- Noms de table et de colonne
- Noms de statistiques

### <a name="permitted-usage-scenarios"></a>Scénarios d’usages autorisés

> [!NOTE]
> Toutes les valeurs de métadonnées d’objet sont hachées avant d’être collectées.
>

|Scénario  |Restrictions d'accès  |Conditions de rétention|
|---------|---------|---------|
|Peut être utilisé par Microsoft pour améliorer les fonctionnalités ou corriger les bogues dans les fonctionnalités actuelles. |Limité à un usage interne Microsoft sans accès à des tiers. |90 jours minimum, 3 ans maximum|

## <a name="telemetry-controls"></a>Commandes de télémétrie

Des instructions sur l’activation/désactivation de la télémétrie dans le produit peuvent être référencées ici - https://support.microsoft.com/help/3153756/how-to-configure-sql-server-2016-to-send-feedback-to-microsoft.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
