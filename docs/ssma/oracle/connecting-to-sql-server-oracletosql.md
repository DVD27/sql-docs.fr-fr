---
title: Connexion à SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server,Synchronizing SQL Server Metadata
ms.assetid: 1b2a8059-1829-4904-a82f-9c06de1e245f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: cd8f0e57554f32d3b02a6e0e98d3a3645d683bac
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266164"
---
# <a name="connecting-to-sql-server-oracletosql"></a>Connexion à SQL Server (OracleToSQL)
Pour migrer des bases de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014, vous devez vous connecter à une de ces cibles des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque vous vous connectez, SSMA récupère les métadonnées sur toutes les bases de données dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et affiche les métadonnées de base de données dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées. SSMA stocke des informations sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous êtes connecté à, mais ne stocke pas les mots de passe.  
  
Votre connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reste active jusqu'à ce que vous fermez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous chargez des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et migrer les données.  
  
Métadonnées relatives à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas synchronisé automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, vous devez manuellement mettre à jour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées. Pour plus d’informations, consultez le « Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées » plus loin dans cette rubrique.  
  
## <a name="required-sql-server-permissions"></a>Autorisations requises de SQL Server  
Le compte qui est utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite des autorisations différentes selon les actions réalisées par le compte :  
  
-   Pour convertir des objets Oracle à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, pour mettre à jour des métadonnées à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou pour enregistrer la syntaxe converti vers des scripts, le compte doit disposer d’autorisation de se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour charger des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le compte doit être un membre de la **sysadmin** rôle de serveur. Cela est nécessaire pour installer les assemblys CLR.  
  
-   Pour migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le compte doit être un membre de la **sysadmin** rôle de serveur. Cela est nécessaire pour exécuter le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] packages de migration de données de l’Agent.  
  
-   Pour exécuter le code généré par SSMA, le compte doit avoir **Execute** autorisations pour toutes les fonctions définies par l’utilisateur dans le **ssma_oracle** schéma de la base de données cible. Ces fonctions fournissent des fonctionnalités équivalentes des fonctions de système Oracle et sont utilisées par les objets convertis.  
  
Si le compte qui est utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est pour effectuer la migration de toutes les tâches, le compte doit être un membre de la **sysadmin** rôle de serveur.  
  
## <a name="establishing-a-sql-server-connection"></a>L’établissement d’une connexion SQL Server  
Avant de convertir des objets de base de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe, vous devez établir une connexion à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où vous souhaitez migrer la base de données Oracle ou les bases de données.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données où les objets et les données seront migrées. Vous pouvez personnaliser ce mappage au niveau du schéma d’Oracle après vous être connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [mappage de schémas Oracle à des schémas de SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
> [!IMPORTANT]  
> Avant d’essayer de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assurez-vous que l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution et peut accepter les connexions.  
  
**Pour vous connecter à SQL Server**  
  
1.  Sur le **fichier** menu, sélectionnez **se connecter à SQL Server**.  
  
    Si vous aviez précédemment connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le nom de la commande sera **reconnexion à SQL Server**.  
  
2.  Dans la boîte de dialogue de connexion, entrez ou sélectionnez le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point ( **.** ).  
  
    -   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
    -   Si vous vous connectez à une instance nommée sur un autre ordinateur, entrez le nom d’ordinateur suivi d’une barre oblique inverse, puis sur le nom d’instance, tels que MyServer\MyInstance.  
  
3.  Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour accepter les connexions sur un port non défini par défaut, entrez le numéro de port qui est utilisé pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexions dans le **port du serveur** boîte. L’instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro de port par défaut est 1433. Pour les instances nommées, SSMA essaiera d’obtenir le numéro de port à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser.  
  
4.  Dans le **base de données** , entrez le nom de la base de données cible.  
  
    Cette option n’est pas disponible lorsque vous vous reconnectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Dans le **authentification** , sélectionnez le type d’authentification à utiliser pour la connexion. Pour utiliser le compte Windows actuel, sélectionnez **l’authentification Windows**. Pour utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, sélectionnez **l’authentification SQL Server**, puis indiquez le nom de connexion et le mot de passe.  
  
6.  Pour une connexion sécurisée, les deux contrôles sont ajoutés, le **chiffrer la connexion** et **TrustServerCertificate** cases à cocher. Uniquement lorsque **chiffrer la connexion** est activée, le **TrustServerCertificate** case à cocher est visible. Lorsque **chiffrer la connexion** est vérifiée (true) et **TrustServerCertificate** est désactivée (false), il valide le certificat SSL SQL Server. La validation du certificat de serveur est une partie de la négociation SSL qui garantit qu'il s'agit du serveur correct avec lequel établir une connexion. Pour ce faire, un certificat doit être installé sur le côté client, ainsi que sur le côté serveur.  
  
7.  Cliquer sur **Se connecter**.  
  
**Compatibilité de Version supérieure**  
  
-   Vous serez en mesure de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet de migration créé est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Vous serez en mesure de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet de migration créé est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, mais vous ne serez pas en mesure de se connecter à des versions inférieures par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Vous serez en mesure de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet créé est SQL Server 2012.  
  
||||||||  
|-|-|-|-|-|-|-|  
|**PROJET Visual Studio TYPE VERSION du serveur cible**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Version : 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Version : 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version:13.x)|Azure SQL DB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Oui|Oui|Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Oui|Oui|Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Oui|Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Oui||
|Azure SQL DB||||||Oui|
  
> [!IMPORTANT]
> Conversion des objets de base de données est effectuée selon le type de projet, mais pas conformément à la version de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous êtes connecté. Dans le cas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] projet 2005, Conversion est effectuée conformément [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 même si vous êtes connecté à une version ultérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisation des métadonnées du serveur SQL  
Métadonnées relatives à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données n’est pas automatiquement mis à jour. Les métadonnées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées est un instantané des métadonnées lorsque vous avez connecté tout d’abord à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou la dernière fois que vous avez mis à jour manuellement des métadonnées. Vous pouvez mettre à jour manuellement les métadonnées pour toutes les bases de données, ou pour n’importe quel base de données unique ou un objet de base de données.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, sélectionnez la case à cocher en regard de la base de données ou le schéma que vous souhaitez mettre à jour la base de données.  
  
    Par exemple, pour mettre à jour les métadonnées pour toutes les bases de données, activez la case à côté **bases de données**.  
  
3.  Avec le bouton droit **bases de données**, ou la base de données individuelle ou schéma de base de données, puis **synchroniser avec la base de données**.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données et des schémas, consultez [schémas Oracle de mappage de schémas SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
-   Pour personnaliser les options de configuration pour les projets, consultez [définition des Options de projet &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
-   Pour personnaliser le mappage des types de données source et cible, consultez [Oracle de mappage et les Types de données SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
-   Si vous n’avez pas à effectuer ces tâches, vous pouvez convertir les définitions d’objets de base de données Oracle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définitions d’objets. Pour plus d’informations, consultez [conversion des schémas Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration d’Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
