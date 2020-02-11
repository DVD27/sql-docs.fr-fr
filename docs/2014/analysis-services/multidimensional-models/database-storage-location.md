---
title: Emplacement de stockage de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2dd3659aed11e4e1cee791fcb5e541471320c82a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075903"
---
# <a name="database-storage-location"></a>Emplacement de stockage de la base de données
  Il existe souvent des situations où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (dba) souhaite qu'une certaine base de données réside en dehors du dossier des données du serveur. Ces situations sont souvent générées par des exigences opérationnelles, telles que l'amélioration des performances ou le développement du stockage. Pour ces situations, la `DbStorageLocation` propriété de base de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] données permet à l’administrateur de base de données de spécifier l’emplacement de la base de données sur un disque local ou un périphérique réseau.  
  
## <a name="dbstoragelocation-database-property"></a>Propriété de base de données DbStorageLocation  
 La propriété de base de données `DbStorageLocation` spécifie le dossier où [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée et gère l'ensemble des données de base de données et des fichiers de métadonnées. Tous les fichiers de métadonnées sont stockés dans le dossier `DbStorageLocation`, à l'exception du fichier de métadonnées de base de données, stocké dans le dossier de données de serveur. Il existe deux considérations importantes lors de la définition de la valeur de propriété de base de données `DbStorageLocation` :  
  
-   La propriété de base de données `DbStorageLocation` doit être définie avec un chemin d'accès au dossier UNC existant ou avec une chaîne vide. Une chaîne vide est la valeur par défaut pour le dossier de données de serveur. Si le dossier n'existe pas, une erreur est déclenchée lorsque vous exécutez une commande `Create`, `Attach` ou `Alter`.  
  
-   La propriété de base de données `DbStorageLocation` ne peut pas être définie pour pointer sur le dossier de données de serveur ou sur l'un de ses sous-dossiers. Si l'emplacement pointe sur le dossier de données de serveur ou l'un de ses sous-dossiers, une erreur est déclenchée lorsque vous exécutez une commande `Create`, `Attach` ou `Alter`.  
  
> [!IMPORTANT]  
>  Nous vous recommandons de définir votre chemin d'accès UNC pour l'utilisation d'un réseau de zone de stockage (SAN), d'un réseau basé sur iSCSI ou d'un disque attaché localement. Tout chemin d'accès UNC menant à un partage réseau ou toute solution de stockage à distance à latence élevée conduit à une installation non prise en charge.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Comparaison entre DbStorageLocation et StorageLocation  
 
  `DbStorageLocation` spécifie le dossier où réside l'ensemble des données de base de données et des fichiers de métadonnées, alors que `StorageLocation` spécifie le dossier où se trouvent la ou les partitions d'un cube. 
  `StorageLocation` peut être défini indépendamment de `DbStorageLocation`. Il s’agit d’une décision du dba [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fondée sur les résultats attendus et, dans de nombreux cas, les utilisations d’une propriété ou d’une autre se chevauchent.  
  
## <a name="dbstoragelocation-usage"></a>Utilisation de DbStorageLocation  
 La `DbStorageLocation` propriété de base de données est utilisée dans `Create` le cadre d’une `Detach` / `Attach` commande de base de données dans `Backup` / `Restore` une séquence de commandes de base de `Synchronize` données, dans une séquence de commandes de base de données ou dans une commande de base de données. La modification de la propriété de base de données `DbStorageLocation` est considérée comme modification structurelle de l'objet de base de données. Toutes les métadonnées doivent alors être recréées et les données traitées à nouveau.  
  
> [!IMPORTANT]  
>  Vous ne devez pas modifier l'emplacement de stockage de base de données en utilisant une commande `Alter`. Au lieu de cela, nous vous recommandons d’utiliser `Detach` / `Attach` une séquence de commandes de base de données (consultez [déplacer une base de données Analysis Services](move-an-analysis-services-database.md), [attacher et détacher des bases de données Analysis Services](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Attacher et détacher des bases de données Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](move-an-analysis-services-database.md)   
 [Élément DbStorageLocation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)   
 [Créer un élément &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)   
 [Élément Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Synchroniser l’élément &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)  
  
  
