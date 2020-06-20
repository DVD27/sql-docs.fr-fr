---
title: Spécifier des mappages de types de données pour un Serveur de publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26331e3864940b9c7f2a2588e3d3cbfa9944c900
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060350"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a>Spécifier des mappages de types de données pour un Serveur de publication Oracle
  Cette rubrique explique comment spécifier des mappages de type de données pour un Serveur de publication Oracle dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Bien qu'un jeu de mappages de type de données par défaut soit fourni pour les serveurs de publication Oracle, il peut être nécessaire de spécifier des mappages différents pour une publication donnée.  
  
 **Dans cette rubrique**  
  
-   **Pour spécifier des mappages de type de données pour un Serveur de publication Oracle, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifiez les mappages de type de données sous l’onglet **mappage de données** de la boîte de dialogue Propriétés de l' **article- \<Article> ** . Elle est disponible dans la page **Articles** de l’Assistant Nouvelle publication et dans la boîte de dialogue Propriétés de la **publication- \<Publication> ** . Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication à partir d’une base de données Oracle](create-a-publication-from-an-oracle-database.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-a-data-type-mapping"></a>Pour spécifier un mappage de types de données  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou dans la boîte de dialogue Propriétés de la **publication- \<Publication> ** , sélectionnez une table, puis cliquez sur Propriétés de **l’article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de Table en surbrillance**.  
  
3.  Sous l’onglet **mappage de données** de la boîte de dialogue Propriétés de l' **article \<Article> -** , sélectionnez mappages dans la colonne type de données de l' **abonné** :  
  
    -   Pour certains types de données, il existe uniquement une seule possibilité de mappage dans laquelle la colonne de la grille de propriétés est en lecture seule.  
  
    -   Pour certains types, vous pouvez sélectionner plus d'un type. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande d'utiliser le mappage par défaut si l'application ne nécessite pas un mappage différent. Pour plus d'informations, voir [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez spécifier des mappages de type de données personnalisés par programme à l'aide des procédures stockées de réplication. Vous pouvez également définir les mappages par défaut qui sont utilisés lors du mappage des types de données entre [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] système de gestion de base de données (SGBD) non-. Pour plus d'informations, voir [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a>Pour définir des mappages de type de données personnalisés lors de la création d'un article appartenant à une publication Oracle  
  
1.  S'il n'en existe pas encore, créez une publication Oracle.  
  
2.  Sur le serveur de distribution, exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql). Spécifiez la valeur **0** pour **\@use_default_datatypes**. Pour plus d’informations, consultez [définir un Article](define-an-article.md).  
  
3.  Sur le serveur de distribution, exécutez [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) pour afficher le mappage existant pour une colonne dans un article publié.  
  
4.  Sur le serveur de distribution, exécutez [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql). Spécifiez le nom du serveur de publication ** \@ Oracle pour le serveur de publication**, ainsi que la ** \@ publication**, ** \@ l’article**et la ** \@ colonne** pour définir la colonne publiée. Spécifiez le nom du [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type de données vers lequel effectuer le mappage pour le ** \@ type**, ainsi que la ** \@ longueur**, la ** \@ précision**et l' ** \@ échelle**, le cas échéant.  
  
5.  Sur le serveur de distribution, exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Cela crée la vue utilisée pour générer l'instantané à partir de la publication Oracle.  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a>Pour spécifier un mappage comme mappage par défaut pour un type de données  
  
1.  (Facultatif) Exécutez [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql)sur une base de données quelconque du serveur de distribution. Spécifiez ** \@ source_dbms**, ** \@ source_type**, ** \@ destination_dbms**, ** \@ destination_version**et tout autre paramètre nécessaire pour identifier le SGBD source. Les informations sur le type de données actuellement mappé dans le SGBD de destination sont retournées à l'aide des paramètres de sortie.  
  
2.  (Facultatif) Exécutez [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)sur une base de données quelconque du serveur de distribution. Spécifiez ** \@ source_dbms** et tous les autres paramètres nécessaires pour filtrer le jeu de résultats. Notez la valeur de **mapping_id** pour le mappage souhaité dans le jeu de résultats.  
  
3.  Exécutez [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)sur une base de données quelconque du serveur de distribution.  
  
    -   Si vous connaissez la valeur souhaitée de **mapping_id** obtenue à l’étape 2, spécifiez-la pour **\@mapping_id**.  
  
    -   Si vous ne connaissez pas **mapping_id**, spécifiez les paramètres **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type** et tous les autres paramètres éventuellement requis pour identifier un mappage existant.  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a>Pour rechercher les types de données valides pour un type de données Oracle donné  
  
1.  Exécutez [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)sur une base de données quelconque du serveur de distribution. Spécifiez la valeur **Oracle** pour ** \@ source_dbms** et tous les autres paramètres nécessaires pour filtrer le jeu de résultats.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple modifie une colonne avec le type de données Oracle NUMBER afin qu'elle soit mappée vers le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]`numeric`(38,38), à la place du type de données par défaut `float`.  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 Cet exemple de requête retourne les mappages par défaut et de remplacement pour le type de données Oracle 9 `CHAR`.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 Cet exemple de requête retourne les mappages par défaut pour le type de données Oracle 9 `NUMBER` lorsqu'il est spécifié sans échelle ni précision.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de type de données pour les serveurs de publication Oracle](../non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Réplication de bases de données hétérogènes](../non-sql/heterogeneous-database-replication.md)   
 [Concepts des procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md)   
 [Configurer un serveur de publication Oracle](../non-sql/configure-an-oracle-publisher.md)  
  
  
