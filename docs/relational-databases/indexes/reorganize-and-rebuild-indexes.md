---
title: Réorganiser et reconstruire des index | Microsoft Docs
ms.custom: ''
ms.date: 11/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql13.swb.index.rebuild.f1
- sql13.swb.indexproperties.fragmentation.f1
- sql13.swb.index.reorg.f1
helpviewer_keywords:
- large object defragmenting
- indexes [SQL Server], reorganizing
- index reorganization [SQL Server]
- reorganizing indexes
- defragmenting large object data types
- index fragmentation [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- indexes [SQL Server], rebuilding
- defragmenting indexes
- nonclustered indexes [SQL Server], defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
- LOB data [SQL Server], defragmenting
- clustered indexes, defragmenting
ms.assetid: a28c684a-c4e9-4b24-a7ae-e248808b31e9
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 02cc19cb28a3141682786ca8192688c9c451fc43
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811156"
---
# <a name="reorganize-and-rebuild-indexes"></a>Réorganiser et reconstruire des index

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Cet article explique comment réorganiser ou reconstruire un index fragmenté dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] modifie automatiquement des index quand des opérations d’insertion, de mise à jour ou de suppression sont effectuées sur les données sous-jacentes. Au fil des modifications, les informations figurant dans l'index sont éparpillées dans la base de données (fragmentée). La fragmentation intervient lorsque des index possèdent des pages dans lesquelles l'organisation logique (reposant sur la valeur de la clé) ne correspond pas à l'organisation physique dans le fichier de données. Une fragmentation importante des index peut diminuer les performances des requêtes et ralentir la vitesse de réponse de votre application, en particulier les opérations d’analyse.

Vous pouvez remédier à la fragmentation des index en réorganisant un index ou en reconstruisant un index. Dans le cas d'index partitionnés reposant sur un schéma de partition, vous pouvez utiliser les méthodes suivantes sur la totalité ou sur une partition unique d'un index.
La reconstruction d'un index entraîne sa suppression puis sa recréation. Ceci permet d'éviter toute fragmentation, de libérer de l'espace disque en compactant les pages d'après le paramètre du facteur de remplissage spécifié ou déjà existant et en retriant les lignes de l'index en pages contiguës. Si `ALL` est précisé, tous les index sur la table sont supprimés puis reconstruits en une seule transaction.
La réorganisation d'un index utilise des ressources système minimes. En effet, elle défragmente le niveau feuille des index cluster et non cluster sur les tables et les vues en retriant les pages de niveau feuille de façon physique afin de resuivre l'ordre logique, c'est-à-dire de gauche à droite, des nœuds. Cette opération compacte également les pages d'index. Le compactage s'appuie sur la valeur du facteur de remplissage existante.

## <a name="BeforeYouBegin"></a> Avant de commencer

### <a name="Fragmentation"></a> Détection de la fragmentation

Lorsque vous déterminez la méthode de défragmentation à adopter, la première étape consiste à analyser l'index pour évaluer son degré de fragmentation. La fonction système [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)vous permet de détecter la fragmentation dans un index spécifique, dans tous les index d’une table ou d’une vue indexée, dans tous les index d’une base de données ou dans tous les index de l’ensemble des bases de données. Pour les index partitionnés, **sys.dm_db_index_physical_stats** procure aussi des informations de fragmentation pour chaque partition.

Le jeu de résultats retourné par la fonction **sys.dm_db_index_physical_stats** inclut les colonnes suivantes.

|colonne|Description|
|------------|-----------------|
|**avg_fragmentation_in_percent**|Pourcentage de fragmentation logique (pages non ordonnées dans un index).|
|**fragment_count**|Nombre de fragments (pages de feuille consécutives physiquement) dans l'index.|
|**avg_fragment_size_in_pages**|Nombre moyen de pages dans un fragment d'un index.|

Une fois le degré de fragmentation connu, utilisez le tableau suivant pour déterminer la méthode la mieux adaptée pour corriger la fragmentation.

|Valeur**avg_fragmentation_in_percent**|Instruction corrective|
|-----------------------------------------------|--------------------------|
|> 5 % et < = 30 %|ALTER INDEX REORGANIZE|
|> 30%|ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup>|

<sup>1</sup> La reconstruction d’un index peut être exécutée en ligne ou hors connexion. La réorganisation d'un index s'effectue toujours en ligne. Pour obtenir le même niveau de disponibilité qu'avec l'option de réorganisation, vous devez reconstruire les index en ligne.

> [!TIP]
> Ces valeurs fournissent des directives approximatives pour déterminer le point auquel vous devez basculer entre `ALTER INDEX REORGANIZE` et `ALTER INDEX REBUILD`. Toutefois, les valeurs réelles peuvent varier d'un cas à l'autre. Il est important que vous fassiez des essais pour déterminer le meilleur seuil pour votre environnement. Par exemple, si un index donné est principalement utilisé pour les opérations d’analyse, la suppression de la fragmentation peut améliorer les performances de ces opérations. L’avantage en matière de performances est moins perceptible pour les index utilisés principalement pour les opérations de recherche. De même, la suppression de la fragmentation dans un segment de mémoire (une table sans index cluster) est particulièrement utile pour les opérations d’analyse d’index non-cluster, mais n’a que peu d’effet dans les opérations de recherche.

Des niveaux très bas de fragmentation (inférieurs à 5 %) ne doivent pas être pris en compte par ces commandes, car l’avantage de la suppression d’un volume de fragmentation aussi réduit est quasiment toujours largement contrebalancé par le coût de la réorganisation ou de la reconstruction de l’index. Pour plus d’informations sur `ALTER INDEX REORGANIZE` et `ALTER INDEX REBUILD`, consultez [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).

> [!NOTE]
> Bien souvent, la reconstruction ou la réorganisation de petits index ne réduit pas la fragmentation. Les pages de petits index sont parfois stockées sur des extensions mixtes. Les extensions mixtes sont partagées par huit objets maximum ; par conséquent, la fragmentation dans un petit index peut ne pas être réduite après sa réorganisation ou sa reconstruction.

### <a name="index-defragmentation-considerations"></a>Considérations sur la défragmentation d’index
Dans certaines conditions, la recréation d’un index cluster recrée automatiquement tout index non-cluster qui référence la clé de clustering, si les identificateurs physiques ou logiques contenus dans les enregistrements d’index non-cluster doivent être modifiés.

Scénarios qui forcent la recréation automatique de tous les index non-cluster sur une table :

-  Création d’un index cluster sur une table
-  Suppression d’un index cluster, provoquant le stockage de la table en tant que segment de mémoire
-  Modification de la clé de clustering pour inclure ou exclure des colonnes

Scénarios qui ne nécessitent pas la recréation automatique de tous les index non-cluster sur une table :

-  Recréation d’un index cluster unique
-  Recréation d’un index cluster non unique
-  Modification du schéma d’index, telle que l’application d’un schéma de partitionnement à un index cluster ou le déplacement de l’index cluster vers un autre groupe de fichiers

### <a name="Restrictions"></a> Limitations et restrictions

Les index possédant plus de 128 extensions sont reconstruits en deux phases distinctes : une phase logique et une phase physique. Dans la phase logique, les unités d'allocation utilisées par l'index sont signalées comme devant être désallouées, les lignes de données sont copiées et triées, puis elles sont déplacées vers les nouvelles unités d'allocation ayant été créées pour stocker l'index reconstruit. Dans la phase physique, les unités d'allocation préalablement signalées pour être désallouées sont supprimées physiquement dans des transactions courtes qui interviennent en arrière-plan et nécessitent peu de verrous. Pour plus d’informations sur les étendues, consultez [Guide d’architecture des pages et des étendues](../../relational-databases/pages-and-extents-architecture-guide.md).

L’instruction `ALTER INDEX REORGANIZE` a besoin du fichier de données contenant l’index pour disposer d’espace, car l’opération peut uniquement allouer des pages de travail temporaires à un même fichier, mais pas à un autre fichier du groupe de fichiers. De ce fait, même si le groupe de fichiers a des pages libres, l’utilisateur peut toujours rencontrer l’erreur 1105 : `Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`

Il est possible de créer et de reconstruire des index non alignés sur une table constituée de plus de 1 000 partitions, mais cela n’est pas recommandé. Ces opérations peuvent entraîner une dégradation des performances ou une consommation de mémoire excessive.

Un index ne peut pas être réorganisé ou reconstruit si le groupe de fichiers dans lequel il se trouve est hors connexion ou en lecture seule. Si le mot clé `ALL` est spécifié et qu’un ou plusieurs index se trouvent dans un groupe de fichiers hors connexion ou en lecture seule, l’instruction échoue.

> [!IMPORTANT]
> Quand un index est créé ou reconstruit dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les statistiques sont créées ou mises à jour par l’analyse de toutes les lignes de la table.
>
> En revanche, à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les statistiques ne sont pas créées ou mises à jour par l’analyse de toutes les lignes de la table au moment où un index partitionné est créé ou reconstruit. Au lieu de cela, l’optimiseur de requête se sert de l’algorithme d’échantillonnage par défaut pour générer ces statistiques. Pour obtenir des statistiques sur les index partitionnés en analysant toutes les lignes de la table, utilisez `CREATE STATISTICS` ou `UPDATE STATISTICS` avec la clause `FULLSCAN`.

### <a name="Security"></a> Sécurité

#### <a name="Permissions"></a> Autorisations

Nécessite l’autorisation `ALTER` sur la table ou la vue. L’utilisateur doit être membre d’au moins l’un des rôles suivants :

- Rôle de base de données **db_ddladmin** <sup>1</sup>
- Rôle de base de données **db_owner**
- Rôle serveur **sysadmin**

<sup>1</sup> Le rôle de base de données **db_ddladmin** est le [moins privilégié](/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models).

## <a name="SSMSProcedureFrag"></a> Vérifier la fragmentation d’un index à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]

### <a name="to-check-the-fragmentation-of-an-index"></a>Pour vérifier la fragmentation d'un index

1. Dans l’Explorateur d’objets, développez la base de données qui contient la table sur laquelle vous souhaitez vérifier une fragmentation d’index.
2. Développez le dossier **Tables** .
3. Développez la table sur laquelle vous souhaitez vérifier une fragmentation d’index.
4. Développez le dossier **Index** .
5. Cliquez avec le bouton droit sur l’index dont vous voulez vérifier la fragmentation, puis sélectionnez **Propriétés**.
6. Sous **Sélectionner une page**, sélectionnez **Fragmentation**.

   Les informations suivantes sont disponibles dans la page **Fragmentation** :

   **Remplissage de la page** Indique le remplissage moyen des pages d'index, sous forme de pourcentage. 100% signifie que les pages d'index sont totalement remplies. 50% signifie qu'en moyenne, chaque page d'index est remplie à moitié.

   **Fragmentation totale** Pourcentage de fragmentation logique. Cette valeur indique le nombre de pages dans un index qui ne sont pas stockées dans l'ordre.

   **Taille moyenne de ligne** Taille moyenne d'une ligne de niveau feuille.

   **Profondeur** Nombre de niveaux dans l'index, notamment le niveau feuille.

   **Enregistrements transférés** Nombre d'enregistrements d'un segment qui contiennent des pointeurs avant vers un autre emplacement de données. (Cet état se produit pendant une mise à jour, lorsque l'espace disponible est insuffisant pour stocker la nouvelle ligne à l'emplacement d'origine.)

   **Lignes fantômes** Nombre de lignes marquées pour la suppression qui ne sont pas encore supprimées. Ces lignes seront supprimées par un thread de nettoyage, lorsque le serveur n'est pas occupé. Cette valeur ne comprend pas les lignes qui sont conservées à cause d'une transaction d'isolement d'instantané en suspens.

   **Type d'index** Type de l'index. Les valeurs possibles sont **Index cluster**, **Index non-cluster**et **XML primaire**. Les tables peuvent également être stockées en tant que segment (sans index), mais dans ce cas la page Propriétés de l'index est impossible à ouvrir.

   **Nombre de lignes de niveau feuille** Nombre de lignes de niveau feuille.

   **Taille maximale de ligne** Taille maximale des lignes de niveau feuille.

   **Taille minimale de ligne** Taille minimale des lignes de niveau feuille.

   **Pages** Nombre total de pages de données.

   **ID de partition** ID de partition de l'arbre B (B-tree) qui contient l'index.

   **Enregistrement de version fantôme** Nombre d'enregistrements fantômes étant conservés en raison d'une transaction d'isolement d'instantané en attente.

## <a name="TsqlProcedureFrag"></a> Vérifier la fragmentation d’un index à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]

### <a name="to-check-the-fragmentation-of-an-index"></a>Pour vérifier la fragmentation d'un index

L’exemple suivant recherche le pourcentage de fragmentation moyenne de tous les index dans la table HumanResources.Employee de la base de données AdventureWorks.

```sql
SELECT a.index_id, name, avg_fragmentation_in_percent
   FROM sys.dm_db_index_physical_stats
      (DB_ID
         (N'AdventureWorks2012')
         , OBJECT_ID(N'HumanResources.Employee')
         , NULL
         , NULL
         , NULL) AS a
   JOIN sys.indexes AS b
      ON a.object_id = b.object_id
      AND a.index_id = b.index_id;
```

L'instruction précédente retourne un jeu de résultats similaire au suivant.

```cmd
index_id    name                                                  avg_fragmentation_in_percent
----------- ----------------------------------------------------- ----------------------------
1           PK_Employee_BusinessEntityID                          0
2           IX_Employee_OrganizationalNode                        0
3           IX_Employee_OrganizationalLevel_OrganizationalNode    0
5           AK_Employee_LoginID                                   66.6666666666667
6           AK_Employee_NationalIDNumber                          50
7           AK_Employee_rowguid                                   0

(6 row(s) affected)
```

Pour plus d’informations, consultez [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).

## <a name="SSMSProcedureReorg"></a> Supprimer la fragmentation à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]

### <a name="to-reorganize-or-rebuild-an-index"></a>Pour réorganiser ou reconstruire un index

1. Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez réorganiser un index.
2. Développez le dossier **Tables** .
3. Développez la table sur laquelle vous souhaitez réorganiser un index.
4. Développez le dossier **Index** .
5. Cliquez avec le bouton droit sur l’index que vous souhaitez réorganiser et sélectionnez **Réorganiser**.
6. Dans la boîte de dialogue **Réorganiser les index** , vérifiez que l'index correct figure dans la grille **Index à réorganiser** , puis cliquez sur **OK**.
7. Cochez la case **Compacter les données de la colonne d’objets volumineux** pour indiquer que toutes les pages qui contiennent des données LOB seront aussi compactées.
8. Cliquez sur **OK.**

### <a name="to-reorganize-all-indexes-in-a-table"></a>Pour réorganiser tous les index d'une table

1. Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez réorganiser les index.
2. Développez le dossier **Tables** .
3. Développez la table sur laquelle vous souhaitez réorganiser les index.
4. Cliquez avec le bouton droit sur le dossier **Index** , puis sélectionnez **Réorganiser tout**.
5. Dans la boîte de dialogue **Réorganiser les index** , vérifiez que les index corrects sont dans **Index à réorganiser**. Pour supprimer un index de la grille **Index à réorganiser** , sélectionnez l'index et appuyez sur la touche SUPPR.
6. Cochez la case **Compacter les données de la colonne d’objets volumineux** pour indiquer que toutes les pages qui contiennent des données LOB seront aussi compactées.
7. Cliquez sur **OK.**

### <a name="to-rebuild-an-index"></a>Pour reconstruire un index

1. Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez réorganiser un index.
2. Développez le dossier **Tables** .
3. Développez la table sur laquelle vous souhaitez réorganiser un index.
4. Développez le dossier **Index** .
5. Cliquez avec le bouton droit sur l’index que vous souhaitez réorganiser et sélectionnez **Regénérer**.
6. Dans la boîte de dialogue **Reconstruire les index** , vérifiez que l'index correct figure dans la grille **Index à reconstruire** , puis cliquez sur **OK**.
7. Cochez la case **Compacter les données de la colonne d’objets volumineux** pour indiquer que toutes les pages qui contiennent des données LOB seront aussi compactées.
8. Cliquez sur **OK.**

## <a name="TsqlProcedureReorg"></a> Supprimer la fragmentation à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]

### <a name="to-reorganize-a-fragmented-index"></a>Pour réorganiser un index fragmenté

L'exemple suivant réorganise l’index `IX_Employee_OrganizationalLevel_OrganizationalNode` dans la table `HumanResources.Employee` de la base de données AdventureWorks.

```sql
ALTER INDEX IX_Employee_OrganizationalLevel_OrganizationalNode
   ON HumanResources.Employee
   REORGANIZE
;
```

### <a name="to-reorganize-all-indexes-in-a-table"></a>Pour réorganiser tous les index d'une table

L'exemple suivant réorganise tous les index dans la table HumanResources.Employee de la base de données AdventureWorks.

```sql
ALTER INDEX ALL ON HumanResources.Employee
   REORGANIZE
;
```

### <a name="to-rebuild-a-fragmented-index"></a>Pour reconstruire un index fragmenté

L'exemple suivant reconstruit un seul index portant sur la table `Employee` de la base de données AdventureWorks.

[!code-sql[IndexDDL#AlterIndex1](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_1.sql)]

### <a name="to-rebuild-all-indexes-in-a-table"></a>Pour reconstruire tous les index d'une table

L’exemple suivant reconstruit tous les index associés à la table dans la base de données AdventureWorks à l’aide du mot clé `ALL`. Trois options sont spécifiées.

[!code-sql[IndexDDL#AlterIndex2](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_2.sql)]

Pour plus d’informations, consultez [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md).

### <a name="automatic-index-and-statistics-management"></a>Gestion automatique des index et des statistiques

Tirez parti de solutions comme [Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag) pour gérer automatiquement la défragmentation des index et les mises à jour des statistiques pour une ou plusieurs bases de données. Cette procédure choisit automatiquement s’il faut reconstruire ou réorganiser un index en fonction de son niveau de fragmentation, entre autres, et mettre à jour les statistiques avec un seuil linéaire.

## <a name="see-also"></a>Voir aussi

- [Guide de conception d’index SQL Server](../../relational-databases/sql-server-index-design-guide.md)
- [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)
- [Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag)
- [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)
- [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)
