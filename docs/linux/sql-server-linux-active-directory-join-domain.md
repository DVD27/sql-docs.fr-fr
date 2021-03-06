---
title: Joindre SQL Server sur Linux à Active Directory
titleSuffix: SQL Server
description: ''
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.date: 04/01/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: d5cd6356f4bc691518f11e1e6fb00add527cc595
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68027341"
---
# <a name="join-sql-server-on-a-linux-host-to-an-active-directory-domain"></a>Joindre SQL Server sur un hôte Linux à un domaine Active Directory

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article fournit des instructions générales sur la façon de joindre une machine hôte Linux SQL Server à un domaine Active Directory (AD). Il existe deux méthodes : utiliser un package SSSD intégré ou utiliser des fournisseurs Active Directory tiers. Par exemple, les produits de jonction de domaine tiers sont les suivants : [Service d’identité PowerBroker (PBIS)](https://www.beyondtrust.com/), [One Identity](https://www.oneidentity.com/products/authentication-services/) et [Centrify](https://www.centrify.com/). Ce guide comprend les étapes permettant de vérifier la configuration de votre Active Directory. Toutefois, il n’est pas prévu de fournir des instructions sur la façon de joindre une machine à un domaine lors de l’utilisation d’utilitaires tiers.

## <a name="prerequisites"></a>Conditions préalables requises

Avant de configurer l’authentification Active Directory, vous devez configurer un contrôleur de domaine Active Directory, Windows, sur votre réseau. Joignez alors votre hôte SQL Server sur Linux à un domaine Active Directory.

> [!IMPORTANT]
> Les exemples d’étapes décrits dans cet article sont fournis à titre d’information uniquement. Les étapes réelles peuvent différer légèrement dans votre environnement en fonction de la configuration de votre environnement global. Faites appel à vos administrateurs système et de domaine pour votre environnement à des fins de configuration, de personnalisation et de résolution des problèmes spécifiques.

## <a name="check-the-connection-to-a-domain-controller"></a>Vérifier la connexion à un contrôleur de domaine

Vérifiez que vous pouvez contacter le contrôleur de domaine avec les noms courts et complets du domaine :

```bash
ping contoso
ping contoso.com
```

> [!TIP]
> Ce didacticiel utilise **contoso.com** et **CONTOSO.COM** comme exemple de domaine et de nom de domaine, respectivement. Il utilise également **DC1.CONTOSO.COM** comme exemple de nom de domaine complet du contrôleur de domaine. Vous devez remplacer ces noms par vos propres valeurs.

Si l’une de ces vérifications de nom échoue, mettez à jour votre liste de recherche de domaine. Les sections suivantes fournissent des instructions pour Ubuntu, Red Hat Enterprise Linux (RHEL) et SUSE Linux Enterprise Server (SLES), respectivement.

### <a name="ubuntu"></a>Ubuntu

1. Modifiez le fichier **/etc/network/interfaces** de façon à ce que votre domaine Active Directory se trouve dans la liste de recherche de domaine :

   ```/etc/network/interfaces
   # The primary network interface
   auto eth0
   iface eth0 inet dhcp
   dns-nameservers **<AD domain controller IP address>**
   dns-search **<AD domain name>**
   ```

   > [!NOTE]
   > L’interface réseau `eth0` peut différer selon les machines. Pour déterminer celui que vous utilisez, exécutez **ifconfig**. Copiez ensuite l’interface qui a une adresse IP et les octets transmis et reçus.

1. Après avoir modifié ce fichier, redémarrez le service réseau :

   ```bash
   sudo ifdown eth0 && sudo ifup eth0
   ```

1. Ensuite, vérifiez que votre fichier **/etc/resolv.conf** contient une ligne comme dans l’exemple suivant :

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

### <a name="rhel"></a>RHEL

1. Modifiez le fichier **/etc/sysconfig/network-scripts/ifcfg-eth0** de façon à ce que votre domaine Active Directory se trouve dans la liste de recherche de domaine. Ou modifiez un autre fichier config d’interface comme il convient :

   ```/etc/sysconfig/network-scripts/ifcfg-eth0
   PEERDNS=no
   DNS1=**<AD domain controller IP address>**
   DOMAIN="contoso.com com"
   ```

1. Après avoir modifié ce fichier, redémarrez le service réseau :

   ```bash
   sudo systemctl restart network
   ```

1. Ensuite, vérifiez que votre fichier **/etc/resolv.conf** contient une ligne comme dans l’exemple suivant :

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

1. Si vous ne pouvez toujours pas effectuer un test ping sur le contrôleur de domaine, recherchez le nom de domaine complet et l’adresse IP du contrôleur de domaine. Un exemple de nom de domaine est **DC1.CONTOSO.COM**. Ajoutez l’entrée suivante à **/etc/hosts** :

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

### <a name="sles"></a>SLES

1. Modifiez le fichier **/etc/sysconfig/network/config** pour que votre adresse IP du contrôleur de domaine Active Directory soit utilisée pour les requêtes DNS et que votre domaine Active Directory figure dans la liste de recherche du domaine :

   ```/etc/sysconfig/network/config
   NETCONFIG_DNS_STATIC_SEARCHLIST=""
   NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
   ```

1. Après avoir modifié ce fichier, redémarrez le service réseau :

   ```bash
   sudo systemctl restart network
   ```

1. Ensuite, vérifiez que votre fichier **/etc/resolv.conf** contient une ligne comme dans l’exemple suivant :

   ```/etc/resolv.conf
   search contoso.com com
   nameserver **<AD domain controller IP address>**
   ```

## <a name="join-to-the-ad-domain"></a>Joindre au domaine AD

Après la vérification de la configuration de base et de la connectivité avec le contrôleur de domaine, il existe deux options pour joindre une machine hôte Linux SQL Server au contrôleur de domaine Active Directory :

- [Option n°1 : Utiliser un package SSSD](#option1)
- [Option n°2 : Utiliser des utilitaires de fournisseur OpenLDAP tiers](#option2)

### <a id="option1"></a> Option n°1 : Utiliser le package SSSD pour joindre le domaine Active Directory

Cette méthode joint l’hôte SQL Server à un domaine AD à l’aide de packages **realmd** et **sssd**.

> [!NOTE]
> Il s’agit de la méthode recommandée pour joindre un hôte Linux à un contrôleur de domaine AD.

Procédez comme suit pour joindre un hôte SQL Server à un domaine Active Directory :

1. Utilisez [realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join) pour joindre votre machine hôte à votre domaine AD. Vous devez d’abord installer les packages client **realmd** et Kerberos sur la machine hôte SQL Server à l’aide du gestionnaire de package de votre distribution Linux :

   **RHEL :**

   ```base
   sudo yum install realmd krb5-workstation
   ```

   **SUSE :**

   ```bash
   sudo zypper install realmd krb5-client
   ```

   **Ubuntu :**

   ```bash
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Si l’installation du package client Kerberos vous invite à entrer un nom de domaine, entrez votre nom de domaine en majuscules.

1. Une fois que vous avez confirmé que votre DNS est correctement configuré, joignez le domaine en exécutant la commande suivante. Vous devez vous authentifier à l’aide d’un compte AD disposant de privilèges suffisants dans AD pour joindre une nouvelle machine au domaine. Cette commande crée un nouveau compte d’ordinateur dans AD, crée le fichier keytab de l’hôte **/etc/krb5.keytab**, configure le domaine dans **/etc/sssd/sssd.conf** et met à jour **/etc/krb5.conf**.

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   ```

   Le message, `Successfully enrolled machine in realm`, doit s’afficher.

   Le tableau suivant répertorie certains messages d’erreur que vous pouvez recevoir et des suggestions pour les résoudre :

   | Message d'erreur | Recommandation |
   |---|---|
   | `Necessary packages are not installed` | Installez ces packages à l’aide du gestionnaire de package de votre distribution Linux avant d’exécuter à nouveau la commande de jonction de domaine. |
   | `Insufficient permissions to join the domain` | Vérifiez auprès d’un administrateur de domaine que vous disposez des autorisations suffisantes pour joindre des machines Linux à votre domaine. |
   | `KDC reply did not match expectations` | Vous n’avez peut-être pas spécifié le nom de domaine correct pour l’utilisateur. Les noms de domaine respectent la casse, généralement en majuscules et peuvent être identifiés avec la commande de découverte de domaine contoso.com. |

   SQL Server utilise SSSD et NSS pour le mappage des comptes et des groupes d’utilisateurs aux identificateurs de sécurité (SID). SSSD doit être configuré et en cours d’exécution pour SQL Server pour créer des connexions AD avec succès. **realmd** effectue généralement cette opération automatiquement dans le cadre de la jonction au domaine, mais dans certains cas, vous devez le faire séparément.

   Pour plus d’informations, consultez comment [configurer SSSD manuellement](https://access.redhat.com/articles/3023951) et [configurer NSS pour fonctionner avec SSSD](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options).

1. Vérifiez que vous pouvez maintenant collecter des informations sur un utilisateur à partir du domaine et que vous pouvez acquérir un ticket Kerberos en tant qu’utilisateur. L’exemple suivant utilise les commandes **id**, [kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html) et [klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html) pour ce faire.

   ```bash
   id user@contoso.com

   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM

   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   ```

   > [!NOTE]
   > - Si l'**iduser@contoso.com** retourne `No such user`, assurez-vous que le service SSSD a démarré avec succès en exécutant la commande `sudo systemctl status sssd`. Si le service est en cours d’exécution et que vous voyez toujours l’erreur, essayez d’activer la journalisation détaillée pour SSSD. Pour plus d’informations, consultez la documentation Red Hat sur la [Résolution des problèmes liés à SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
   >
   > - Si **kinituser@CONTOSO.COM** retourne `KDC reply did not match expectations while getting initial credentials`, assurez-vous que vous avez spécifié le domaine en majuscules.

Pour plus d’informations, consultez la documentation Red Hat sur la [Découverte et la jonction de domaines d’identité](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html).

### <a id="option2"></a> Option n°2 : Utiliser des utilitaires de fournisseur OpenLDAP tiers

Vous pouvez utiliser des utilitaires tiers tels que [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/) ou [Centrify](https://www.centrify.com/). Cet article ne couvre pas les étapes de chaque utilitaire individuellement. Vous devez d’abord utiliser l’un de ces utilitaires pour joindre l’hôte Linux pour SQL Server au domaine avant de continuer.  

SQL Server n’utilise pas le code ou la bibliothèque de l’intégrateur tiers pour les requêtes relatives à AD. SQL Server interroge toujours AD à l’aide des appels de la bibliothèque OpenLDAP directement dans cette installation. Les intégrateurs tiers sont utilisés uniquement pour joindre l’hôte Linux au domaine AD et SQL Server n’a aucune communication directe avec ces utilitaires.

> [!IMPORTANT]
> Veuillez consulter les suggestions relatives à l'utilisation de l'option de configuration **mssql-conf** `network.disablesssd` dans la section **Options de configuration supplémentaires** de l’article [Utiliser l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md#additionalconfig).

Vérifiez que votre **/etc/krb5.conf** est correctement configuré. Pour la plupart des fournisseurs Active Directory tiers, cette configuration est effectuée automatiquement. Toutefois, vérifiez que les valeurs suivantes se trouvent dans **/etc/krb5.conf** afin d’éviter tout problème futur :

```/etc/krb5.conf
[libdefaults]
default_realm = CONTOSO.COM

[realms]
CONTOSO.COM = {
}

[domain_realm]
contoso.com = CONTOSO.COM
.contoso.com = CONTOSO.COM
```

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Vérifier que le DNS inversé est correctement configuré

La commande suivante doit retourner le nom de domaine complet (FQDN) de l’hôte qui exécute SQL Server. **SqlHost.contoso.com** est un exemple.

```bash
host **<IP address of SQL Server host>**
```

La sortie de cette commande doit être similaire à `**<reversed IP address>**.in-addr.arpa domain name pointer SqlHost.contoso.com`. Si cette commande ne retourne pas le nom de domaine complet de votre hôte ou si le nom de domaine complet est incorrect, ajoutez une entrée DNS inversé pour votre hôte SQL Server sur Linux à votre serveur DNS.

## <a name="next-steps"></a>Étapes suivantes

Cet article aborde les conditions préalables à la configuration de SQL Server sur une machine hôte Linux avec l’authentification Active Directory. Pour terminer la configuration de SQL Server sur Linux pour la prise en charge des comptes Active Directory, suivez les instructions sur [Utiliser l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).