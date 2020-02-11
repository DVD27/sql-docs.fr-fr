---
title: Importer et exporter des données en bloc à l’aide de l’utilitaire bcp (SQL Server) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], bcp utility
- bulk importing [SQL Server], bcp utility
- bcp utility [SQL Server], about bcp utility
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: ''
ms.custom: ''
ms.date: 06/14/2017
ms.openlocfilehash: 7075bf87ed64686750bc4a267af431268987ff35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71708213"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a>Importer et exporter des données en bloc à l'aide de l'utilitaire bcp (SQL Server)

Cette rubrique est une présentation générale de l'utilisation de l' [utilitaire bcp](../../tools/bcp-utility.md) pour exporter des données à partir de n'importe quel emplacement d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant une instruction SELECT, vues partitionnées comprises.  
  
 L'utilitaire bcp (Bcp.exe) est un outil de ligne de commande qui fait appel à l'API BCP (Bulk Copy Program). L'utilitaire exécute les tâches suivantes :  
  
-   Exportations en bloc des données à partir d'une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un fichier de données.  
  
-   Exportations en bloc des données à partir d'une requête.  
  
-   Importations en bloc des données à partir d'un fichier de données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Génération des fichiers de format.  
  
 L’utilitaire bcp est accessible via la commande **bcp** . Pour utiliser la commande **bcp** afin d’importer des données en bloc, vous devez comprendre le schéma de la table et les types de données de ses colonnes, à moins que vous n’utilisiez un fichier de format pré-existant.  
  
 L'utilitaire bcp peut exporter des données à partir d'une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un fichier de données qui sera utilisé dans d'autres programmes. L'utilitaire permet également d'importer des données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un autre programme, généralement un autre système de gestion de base de données (SGBD). Les données sont d'abord exportées à partir du programme source dans un fichier de données, puis copiées, au cours d'une opération séparée, à partir du fichier de données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La commande **bcp** fournit des commutateurs qui vous permettent de spécifier le type de données du fichier de données ainsi que d’autres informations. Si ces commutateurs ne sont pas spécifiés, une commande bcp demande des informations de mise en forme, comme le type de champs de données dans un fichier de données. La commande vous propose ensuite de créer un fichier de format contenant vos réponses interactives. Ce fichier est le plus souvent utile si vous avez besoin de flexibilité pour de futures opérations d'importation-exportation en bloc. Vous pouvez spécifier le fichier de format lors de l’exécution ultérieure de commandes **bcp** pour des fichiers de données équivalents. Pour plus d’informations, consultez [Spécifier des formats de données pour la compatibilité lors de l’utilisation de bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).  
  
> [!NOTE]  
>  L'utilitaire bcp est écrit à l'aide de la copie en bloc ODBC  
  
 Pour obtenir une description de la syntaxe de la commande **bcp** , consultez [bcp Utility](../../tools/bcp-utility.md).  
  
## <a name="examples"></a>Exemples

 Pour obtenir des exemples de commande **bcp** , consultez :  
  
-   [Utilitaire bcp](../../tools/bcp-utility.md)  
  
-   [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Conserver les valeurs d’identité lors de l’importation en bloc de données &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Spécifiez les indicateurs de fin de champ et de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utilisez le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilisez le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilisez le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilisez le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a>Voir aussi

[Insérer &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) 
 [clause SELECT &#40;utilitaire Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) 
 [BCP](../../tools/bcp-utility.md)   
[Préparer l’importation en bloc de données &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md) 
 [Bulk Insert &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 
 [importation et l’exportation de données ](bulk-import-and-export-of-data-sql-server.md) 
en bloc &#40;SQL Server&#41;[OpenRowset &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) 
 [créer un fichier de format](create-a-format-file-sql-server.md) &#40;SQL Server&#41;