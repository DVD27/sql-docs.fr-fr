---
title: Exécution de la Console SSMA (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Script file commands, Database connection commands
- Script file commands, Manageability commands
- Script file commands, Migration commands
- Script file commands, Migration preparation commands
- Script file commands, project commands
- Script file commands, Report commands
- Script file commands, Script generation commands
ms.assetid: e3e9f7e4-0619-4861-a202-3d5d39953b26
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d309a1d0bbdf21c94458771e38aa67fd3eb3fe4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102992"
---
# <a name="executing-the-ssma-console-mysqltosql"></a>Exécution de la console SSMA (MySQLToSQL)
Microsoft vous fournit un ensemble robuste de script de commandes de fichier pour exécuter et contrôler les activités SSMA.  
  
L’application console utilise certaines commandes de fichier de script standard comme énuméré dans cette section.  
  
## <a name="project--script-file-commands"></a>Commandes de fichier de Script de projet  
**Commande**  
  
Créer-nouveau projet :   
                   Crée un nouveau projet SSMA.  
  
Les commandes de projet gèrent la création de projets, ouvrir, enregistrer et quitter des projets.  
  
**Script**  
  
1.  `project-folder` Indique le dossier du projet créé.  
  
2.  `project-name` Indique le nom du projet. {string}  
  
3.  `overwrite-if-exists`Attribut facultatif indique si un projet existant doit être remplacé. {valeur booléenne}  
  
4.  `project-type:`Attribut facultatif. Indique le projet par exemple, « sql server 2005 » projet ou projet de « sql server 2008 » ou « sql server 2012 » ou « sql-server-2014 » projet ou projet de « sql azure ». Valeur par défaut est « sql server 2008 ».  
  
**Exemple de syntaxe :**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type=="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"   (optional)  
  
/>  
```  
Attribut 'Remplacer-if-exists' est **false** par défaut.  
  
L’attribut « type de projet » est **sql-server-2008** par défaut.  
  
**Commande**  
  
Open-projet :   
                  Ouvre un projet existant.  
  
**Script**  
  
1.  `project-folder` Indique le dossier du projet créé. La commande échoue si le dossier spécifié n’existe pas.  {string}  
  
2.  `project-name` Indique le nom du projet. La commande échoue si le projet spécifié n’existe pas.  {string}  
  
**Exemple de syntaxe :**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
> [!IMPORTANT]  
> Application Console pour SSMA pour MySQL prend en charge la compatibilité descendante. Vous ne pourrez pas ouvrir les projets créés par une version précédente de SSMA.  
  
**Commande**  
  
projet de l’enregistrement : Enregistre le projet de migration.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<save-project/>  
```  
**Commande**  
  
projet-fermer  
                  : Ferme le projet de migration.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<save-project/>  
```  
**Commande**  
  
projet-fermer  
                  : Ferme le projet de migration.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
Attribut « if-modifié » est facultatif, **ignorer** par défaut.  
  
## <a name="database-connection-script-file-commands"></a>Commandes de fichier de Script de connexion de base de données  
Les commandes de la connexion de base de données permettent de se connecter à la base de données.  
  
1.  Le **Parcourir** fonctionnalité de l’interface utilisateur n’est pas prise en charge dans la console.  
  
2.  Le **l’authentification windows** et **port** paramètres ne sont pas applicables lors de la connexion à SQL Azure.  
  
3.  Pour plus d’informations sur la « Création de fichiers de Script », consultez [création de fichiers de Script &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md).  
  
**Commande**  
  
se connecter--base de données source  
  
-   Effectue la connexion à la base de données source et charge les métadonnées de niveau élevée de la base de données source mais pas toutes les métadonnées.  
  
-   Si la connexion à la source ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution  
  
**Script**  
  
Définition de serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script.  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Commande**  
  
force-load-source/target-database  
  
-   Charge les métadonnées de la source.  
  
-   Utile pour travailler sur le projet de migration hors connexion.  
  
-   Si la connexion à la source/cible ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution  
  
**Script**  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
**Exemple de syntaxe :**  
  
```xml  
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Commande**  
  
se reconnecter--base de données source  
  
1.  Se reconnecte à la base de données source mais ne se charge pas toutes les métadonnées contrairement à la commande connect--base de données source.  
  
2.  Si la (connexion avec la source re) ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Commande**  
  
se connecter--base de données cible  
  
1.  Se connecte à la base de données SQL Server ou SQL Azure cible et charge entièrement les métadonnées de niveau élevée de la base de données cible mais pas les métadonnées.  
  
2.  Si la connexion à la cible ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Script**  
  
Définition de serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Commande**  
  
se reconnecter--base de données cible  
  
1.  Se reconnecte à la base de données cible, mais ne se charge pas toutes les métadonnées, contrairement à la commande connect--base de données cible.  
  
2.  Si la (connexion à la cible re) ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Commandes de fichier de Script de rapport  
Les commandes de rapport génèrent des rapports sur les performances de diverses activités de la Console SSMA.  
  
**Commande**  
  
generate-assessment-report  
  
1.  Génère des rapports d’évaluation sur la base de données source.  
  
2.  Si la connexion de base de données source n’est pas effectuée avant d’exécuter cette commande, une erreur est générée et l’application de console se ferme.  
  
3.  Échec de connexion au serveur de base de données source pendant l’exécution de la commande, entraîne également l’arrêt de l’application de console.  
  
**Script**  
  
1.  `assessment-report-folder:` Spécifie le dossier dans lequel le rapport d’évaluation peut être stockées. (attribut facultatif)  
  
2.  `object-name:` Spécifie l’ou les objets pris en compte pour la génération de rapports d’évaluation (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
3.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
4.  `assessment-report-overwrite:` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
5.  `write-summary-report-to:` Spécifie le chemin d’accès où le rapport de synthèse est généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **AssessmentReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<generate-assessment-report  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
>  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration--script-file-commands"></a>Commandes de fichier de Script de migration  
Les commandes de Migration convertir le schéma de base de données cible au schéma source et migre les données vers le serveur cible.  
  
La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreurs détaillées : Résumé uniquement sur le nœud racine d’arborescence objet source.  
  
**Commande**  
  
convert-schema  
  
1.  Effectue une conversion de schéma à partir de la source vers le schéma cible.  
  
2.  Si la connexion de base de données source ou cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données source ou cible échoue pendant l’exécution de commande, une erreur est générée et l’application de console se ferme.  
  
**Script**  
  
1.  `conversion-report-folder:` Spécifie le dossier dans lequel le rapport d’évaluation peut être stockées. (attribut facultatif)  
  
2.  `object-name:` Spécifie l’ou les objets pris en compte pour la conversion de schéma (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
3.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
4.  `conversion-report-overwrite:` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
5.  `write-summary-report-to:` Spécifie le chemin d’accès où le rapport de synthèse est généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **SchemaConversionReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapport de synthèse a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<convert-schema  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<convert-schema  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
      <metabase-object object-name="<object-names>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Commande**  
  
migrer des données  
  
1.  Migre les données source vers la cible.  
  
**Script**  
  
1.  `object-name:` Spécifie les objets de source pris en compte pour la migration de données (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
2.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
3.  `write-summary-report-to:` Spécifie le chemin d’accès où le rapport de synthèse est généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **DataMigrationReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="true" verbose="true">  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <data-migration-connection  
  
         source-use-last-used="true"/source-server="<server-unique-name>"  
  
         target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
ou Gestionnaire de configuration  
  
```xml  
<migrate-data  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="true" verbose="true"/>  
```  
  
## <a name="migration-preparation-script-file-command"></a>Commande de fichier de Script de préparation migration  
La commande de préparation de la Migration lance le mappage de schéma entre les bases de données source et cible.  
  
**Commande**  
  
schéma de mappage  
  
Mappage de schéma de base de données source vers le schéma cible.  
  
**Script**  
  
1.  `source-schema` Spécifie le schéma source que nous avons l’intention de migrer.  
  
2.  `sql-server-schema` Spécifie le schéma cible que nous voulons être migrés.  
  
**Exemple de syntaxe :**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Commandes de fichier de Script de la facilité de gestion  
Les commandes de la facilité de gestion permettent de synchroniser les objets de base de données cible avec la base de données source.  
  
> [!NOTE]  
> La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreurs détaillées : Résumé uniquement sur le nœud racine d’arborescence objet source.  
  
**Commande**  
  
synchroniser la cible  
  
1.  Synchronise les objets cibles avec la base de données cible.  
  
2.  Si cette commande est exécutée sur la base de données source, une erreur s’est produite.  
  
3.  Si la connexion de base de données cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données cible échoue pendant l’exécution de commande, une erreur est générée et l’application de console se ferme.  
  
**Script**  
  
1.  `object-name:` Spécifie l’ou les objets pris en compte pour la synchronisation avec la base de données cible (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
2.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
3.  `on-error:` Spécifie s’il faut spécifier des erreurs de synchronisation comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
    -   Rapport total en tant qu’avertissement  
  
    -   rapport-each-sous-avertissement  
  
    -   Échec-script  
  
4.  `report-errors-to:` Spécifie l’emplacement du rapport d’erreurs pour l’opération de synchronisation (attribut facultatif) si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **TargetSynchronizationReport.XML** est créé.  
  
**Exemple de syntaxe :**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<synchronize-target>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
**Commande**  
  
actualisation de base de données  
  
1.  Actualise les objets de la source à partir de la base de données.  
  
2.  Si cette commande est exécutée sur la base de données cible, une erreur est générée.  
  
**Script**  
  
1.  `object-name:` Spécifie les objets de source pris en compte pour l’actualisation à partir de la base de données source (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
2.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
3.  `on-error:` Spécifie s’il faut spécifier des erreurs de synchronisation comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
    -   Rapport total en tant qu’avertissement  
  
    -   rapport-each-sous-avertissement  
  
    -   Échec-script  
  
4.  `report-errors-to:` Spécifie l’emplacement du rapport d’erreurs pour l’opération de synchronisation (attribut facultatif) si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **SourceDBRefreshReport.XML** est créé.  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
**Exemple de syntaxe :**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<refresh-from-database>  
  
   <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Commandes de fichier de Script de génération script  
Les commandes de génération du Script effectuent deux tâches : Ils permettent d’enregistrer la sortie dans un fichier de script de console et enregistrer la sortie de T-SQL dans la console ou un fichier basé sur le paramètre que vous spécifiez.  
  
**Commande**  
  
Enregistrer en tant que script  
  
Utilisé pour enregistrer les Scripts des objets dans un fichier mentionné lorsque la métabase = cible, il s’agit d’une alternative à la commande de synchronisation là où nous obtenir les scripts dans et exécutez le même sur la base de données cible.  
  
**Script**  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
1.  `object-name:` Spécifie l’ou les objets dont les scripts doivent être enregistrés. (Il peut avoir les noms d’objets individuels ou un nom d’objet de groupe)  
  
2.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
3.  `metabase:` Spécifie s’il s’agit de la source ou cible de la métabase.  
  
4.  `destination:` Spécifie le chemin d’accès ou le dossier dans lequel le script doit être enregistré, si le nom de fichier n’est indiqué ensuite un nom de fichier dans le format (valeur d’attribut object_name) .out  
  
5.  `overwrite:` Si true elle remplace si le même nom de fichier existe. Il peut avoir les valeurs (true/false).  
  
**Exemple de syntaxe :**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file-name/folder-name>"  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file-name/folder-name>"  
  
      <metabase-object object-name="<object-name>"  
  
            object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Commande**  
  
instruction CONVERT-sql  
  
1.  `context` Spécifie le nom de schéma.  
  
2.  `destination` Spécifie si la sortie doit être stockée dans un fichier.  
  
    Si cet attribut n’est pas spécifié, l’instruction T-SQL convertie s’affiche sur la console. (attribut facultatif)  
  
3.  `conversion-report-folder` Spécifie le dossier dans lequel le rapport d’évaluation peut être stockées. (attribut facultatif)  
  
4.  `conversion-report-overwrite` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
5.  `write-converted-sql-to` Spécifie le fichier (ou) le chemin d’accès du dossier où le code T-SQL converti doit être stocké. Quand un chemin d’accès du dossier est spécifié avec la `sql-files` attribut, chaque fichier source a une cible correspondante fichier T-SQL créé sous le dossier spécifié. Quand un chemin d’accès du dossier est spécifié avec la `sql` attribut, le code T-SQL converti est écrit dans un fichier nommé Result.out sous le dossier spécifié.  
  
6.  `sql` Spécifie les instructions sql de MySQL à convertir, une ou plusieurs instructions peuvent être séparés à utiliser un « ; »  
  
7.  `sql-files` Spécifie le chemin d’accès des fichiers de sql qui doit être converti en code T-SQL.  
  
8.  `write-summary-report-to` Spécifie le chemin d’accès où le rapport de synthèse est généré. Si seul le chemin du dossier est mentionné, puis de fichiers par nom **ConvertSQLReport.XML** est créé. (attribut facultatif)  
  
    Rapport de création possède 2 plus sous-catégories, reportages.., :  
  
    -   erreurs de rapport (= « true/false », la valeur par défaut en tant que « false » (attributs facultatifs)).  
  
    -   verbose (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs)).  
  
**Script**  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
**Exemple de syntaxe :**  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="stdout/file"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql="SELECT 1 FROM DUAL;">  
  
      <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
ou Gestionnaire de configuration  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
ou Gestionnaire de configuration  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>Étape suivante  
Pour plus d’informations sur les options de ligne de commande, consultez [les Options de ligne de commande dans la Console SSMA &#40;MySQLToSQL&#41; ](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md) .  
  
Pour plus d’informations sur les exemples de fichiers de script console, consultez [fonctionne avec les exemples de fichiers de Script de Console &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
L’étape suivante varie selon les spécifications de votre projet :  
  
1.  Pour spécifier un mot de passe ou d’exportation / importation des mots de passe, consultez [la gestion des mots de passe &#40;MySQLToSQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
2.  Pour générer des rapports, consultez [génération de rapports &#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
3.  Pour résoudre les problèmes dans la console, consultez [dépannage &#40;MySQLToSQL&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
