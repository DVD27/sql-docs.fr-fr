---
title: Option replay (outil d’administration Distributed Replay) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a709d4badbd270d9ddffedd62ff040e8ca6c628
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63149471"
---
# <a name="replay-option-distributed-replay-administration-tool"></a>Option replay (outil d'administration Distributed Replay)
  L' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] outil d’administration Distributed Replay `DReplay.exe`,, est un outil en ligne de commande que vous pouvez utiliser pour communiquer avec le contrôleur Distributed Replay. Cette rubrique décrit l’option de ligne de commande **replay** et la syntaxe correspondante.  
  
 L’option **replay** initialise l’étape de relecture d’événement, dans laquelle le contrôleur distribue des données de relecture aux clients spécifiés, lance la relecture distribuée et synchronise les clients. Chaque client participant à la relecture peut éventuellement enregistrer l'activité de relecture et enregistrer un fichier de trace de résultats localement.  
  
 ![Icône de lien de rubrique](../../database-engine/media/topic-link.gif "Icône du lien de rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées avec la syntaxe de l’outil d’administration, consultez conventions de la [syntaxe Transact-sql &#40;&#41;Transact-SQL ](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
```  
  
#### <a name="parameters"></a>Paramètres  
 **-m** *contrôleur*  
 Spécifie le nom de l'ordinateur du contrôleur. Vous pouvez utiliser «`localhost`» ou «`.`» pour désigner l'ordinateur local.  
  
 Si le paramètre **-m** n’est pas spécifié, l’ordinateur local est utilisé.  
  
 **-d** *controller_working_dir*  
 Spécifie le répertoire du contrôleur où sera stocké le fichier intermédiaire. Le paramètre **-d** est obligatoire.  
  
 Les conditions suivantes s'appliquent :  
  
-   Le répertoire doit résider sur le contrôleur.  
  
-   Vous devez spécifier le chemin complet, en commençant par une lettre de lecteur (par exemple, `c:\WorkingDir`).  
  
-   Le chemin d'accès ne doit pas se terminer par une barre oblique inverse «`\`».  
  
-   Les chemins d'accès UNC ne sont pas pris en charge.  
  
 **-o**  
 Capture l'activité de relecture des clients et la sauvegarde dans un fichier de trace de résultats dans le chemin d'accès spécifié par l'élément `<ResultDirectory>` , dans le fichier de configuration client `DReplayClient.xml`.  
  
 Lorsque le paramètre **-o** n’est pas spécifié, le fichier de trace de résultats n’est pas généré. La sortie de console retourne les informations de résumé à la fin de la relecture, mais aucune autre statistique de relecture n'est disponible.  
  
 **-s** *target_server*  
 Spécifie l'instance cible de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec laquelle la charge de travail distribuée doit être relue. Vous devez spécifier ce paramètre au format **nom_serveur[\nom_instance]**.  
  
 Vous ne pouvez pas utiliser «`localhost`» ou «`.`» comme serveur cible.  
  
 Le paramètre **-s** n’est pas obligatoire si l’élément `<Server>` est spécifié dans la section `<ReplayOptions>` du fichier de configuration de relecture `DReplay.exe.replay.config`.  
  
 Si le paramètre **-s** est utilisé, l’élément `<Server>` dans la section `<ReplayOptions>` du fichier de configuration de relecture est ignoré.  
  
 **-w** *clients*  
 Ce paramètre obligatoire est une liste de valeurs séparées par des virgules (sans espaces) qui spécifie les noms d'ordinateur des clients qui doivent participer à la relecture distribuée. Les adresses IP ne sont pas autorisées. Sachez que les clients doivent être déjà enregistrés avec le contrôleur.  
  
> [!NOTE]  
>  Chaque client s'inscrit avec le contrôleur spécifié dans le fichier de configuration client lors du démarrage du service client.  
  
 **-c** *Config_file*  
 C'est le chemin d'accès complet du fichier de configuration de relecture ; il est utilisé pour spécifier l'emplacement du fichier lorsqu'il est stocké à un autre emplacement.  
  
 Le paramètre **-c** n’est pas obligatoire si vous voulez utiliser les valeurs par défaut du fichier de configuration de relecture `DReplay.exe.replay.config`.  
  
 **-f** *status_interval*  
 Spécifie la fréquence (en secondes) à laquelle afficher l'état.  
  
 Si **-f** n’est pas spécifié, l’intervalle par défaut est de 30 secondes.  
  
## <a name="examples"></a>Exemples  
 Dans cet exemple, la relecture distribuée tire beaucoup de son comportement d'un fichier de configuration de relecture modifié, `DReplay.exe.replay.config`.  
  
-   Le paramètre **-m** spécifie qu’un ordinateur nommé `controller1` agit en tant que contrôleur. Le nom d'ordinateur doit être spécifié quand le service contrôleur s'exécute sur un autre ordinateur.  
  
-   Le paramètre **-d** spécifie l’emplacement du fichier intermédiaire sur le contrôleur, `c:\WorkingDir`.  
  
-   Le paramètre **-o** spécifie que chaque client spécifié capture l’activité de relecture et l’enregistre dans un fichier de trace de résultats. Remarque : l'élément `<ResultTrace>` dans le fichier de configuration peut être utilisé pour spécifier si le nombre de lignes et le jeu de résultats doivent être enregistrés.  
  
-   Le paramètre **-w** spécifie que les ordinateurs `client1` à `client4` participent en tant que clients à la relecture distribuée.  
  
-   Le paramètre **-c** est utilisé pour pointer vers le fichier de configuration modifié `DReplay.exe.replay.config`.  
  
-   Le paramètre **-s** n’est pas obligatoire, car l’élément `<Server>` est spécifié dans l’élément `<ReplayOptions>` du fichier de configuration de relecture `DReplay.exe.replay.config`.  
  
 L'étape de relecture d'événement est initialisée avec la syntaxe suivante, lorsque l'outil d'administration est exécuté à partir d'un autre ordinateur que le contrôleur :  
  
```  
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config  
```  
  
 Pour spécifier un mode de mise en séquence synchrone, l'élément `<SequencingMode>` du fichier `DReplay.exe.replay.config` est défini comme égal à la valeur `synchronization`. La section `<ResultTrace>` du fichier de configuration de relecture est modifiée pour spécifier que le nombre de lignes doit être enregistré. Ces modifications sont illustrées dans l'exemple XML suivant :  
  
```  
<?xml version='1.0'?>  
<Options>  
    <ReplayOptions>  
        <Server>server_name\replay_target_instance</Server>  
        <SequencingMode>synchronization</SequencingMode>  
        <ConnectTimeScale></ConnectTimeScale>  
        <ThinkTimeScale></ThinkTimeScale>  
        <HealthmonInterval>60</HealthmonInterval>  
        <QueryTimeout>3600</QueryTimeout>  
        <ThreadsPerClient></ThreadsPerClient>  
    </ReplayOptions>  
    <OutputOptions>  
        <ResultTrace>  
            <RecordRowCount>Yes</RecordRowCount>  
            <RecordResultSet>No</RecordResultSet>  
        </ResultTrace>  
    </OutputOptions>  
</Options>  
```  
  
 Pour spécifier un mode de séquencement en simultané (stress), l'élément `<SequencingMode>` du fichier `DReplay.exe.replay.config` est défini comme égal à la valeur `stress`. Les éléments `<ConnectTimeScale>` et `<ThinkTimeScale>` ont la valeur `50` (pour spécifier 50 pour cent). Pour plus d'informations sur le délai de connexion et le temps de réflexion, consultez [Configure Distributed Replay](configure-distributed-replay.md). Ces modifications sont illustrées dans l'exemple XML suivant :  
  
```  
<?xml version='1.0'?>  
<Options>  
    <ReplayOptions>  
        <Server>server_name\replay_target_instance_name</Server>  
        <SequencingMode>stress</SequencingMode>  
        <ConnectTimeScale>50</ConnectTimeScale>  
        <ThinkTimeScale>50</ThinkTimeScale>  
        <HealthmonInterval>60</HealthmonInterval>  
        <QueryTimeout>3600</QueryTimeout>  
        <ThreadsPerClient></ThreadsPerClient>  
    </ReplayOptions>  
    <OutputOptions>  
        <ResultTrace>  
            <RecordRowCount>Yes</RecordRowCount>  
            <RecordResultSet>No</RecordResultSet>  
        </ResultTrace>  
    </OutputOptions>  
</Options>  
```  
  
## <a name="permissions"></a>Autorisations  
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.  
  
 Pour plus d’informations, voir [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Relire les données de trace](replay-trace-data.md)   
 [Examiner les résultats de relecture](review-the-replay-results.md)   
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)   
 [Configurer Distributed Replay](configure-distributed-replay.md)   
 [Forum de Distributed Replay SQL Server](https://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [Utilisation de Distributed Replay pour le test de charge de votre SQL Server-partie 2](https://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx)   
 [Utilisation de Distributed Replay pour le test de charge de votre SQL Server-partie 1](https://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)  
  
  
