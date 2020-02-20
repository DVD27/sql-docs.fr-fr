---
title: Versions précédentes de SSDT
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: “”
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 5d32e301-0f44-4916-b0db-76e8322c0ab7
author: markingmyname
ms.author: maghan
manager: jroth
ms.custom: seo-lt-2019
ms.date: 09/05/2018
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 07504e19591b1f64aac77ebbc825bea58931b536
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75688574"
---
# <a name="previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi"></a>Versions antérieures de SQL Server Data Tools (SSDT et SSDT-BI)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
SQL Server Data Tools (SSDT) fournit des modèles de projet et des aires de conception permettant de créer des types de contenu SQL Server (bases de données relationnelles, modèles Analysis Services, rapports Reporting Services et packages Integration Services).  
  
SSDT offre une compatibilité descendante, ce qui signifie que vous pouvez toujours utiliser [la version de SSDT la plus récente](download-sql-server-data-tools-ssdt.md) pour concevoir et déployer des bases de données, des modèles, des rapports et des packages qui s’exécutent sur des versions plus anciennes de SQL Server.  
  
> [!NOTE]  
> Historiquement, le shell Visual Studio utilisé pour créer des types de contenu SQL Server a été publié sous différents noms, notamment **SQL Server Data Tools**, **SQL Server Data Tools - Business Intelligence**et **Business Intelligence Development Studio**. Les versions précédentes étaient fournies avec des ensembles distincts de modèles de projet. Pour obtenir tous les modèles de projet regroupés dans un SSDT, vous devez disposer de [la version la plus récente](download-sql-server-data-tools-ssdt.md). Sinon, vous devrez probablement installer plusieurs versions précédentes pour obtenir tous les modèles utilisés dans SQL Server.  Un seul shell est installé par version de Visual Studio ; l’installation d’un deuxième SSDT ajoute simplement les modèles manquants.  

## <a name="recent-downloads"></a>Téléchargements récents

Voici les derniers téléchargements au cas où vous rencontreriez des problèmes avec la dernière version, ce qui est peu probable.

|Version de SSDT| Visual Studio 2017|
|:---|:---|
|15.9.2|[SSDT pour VS2017 15.9.2](https://go.microsoft.com/fwlink/?linkid=2095463)|
|15.9.1|[SSDT pour VS2017 15.9.1](https://go.microsoft.com/fwlink/?linkid=2086373)|
|15.9.0|[SSDT pour VS2017 15.9.0](https://go.microsoft.com/fwlink/?linkid=2052454)|
|15.8.2|[SSDT pour VS2017 15.8.2](https://go.microsoft.com/fwlink/?linkid=2038031)|
|15.8.0|[SSDT pour VS2017 15.8.0](https://go.microsoft.com/fwlink/?linkid=2014060)|
|15.7.1|[SSDT pour VS2017 15.7.1](https://go.microsoft.com/fwlink/?LinkId=875613)|
|15.7.0|[SSDT pour VS2017 15.7.0](https://go.microsoft.com/fwlink/?LinkId=874716)|
|15.6.0|[SSDT pour VS2017 15.6.0](https://go.microsoft.com/fwlink/?LinkId=871368)|

<br>

|Version de SSDT| Visual Studio 2015|
|:---|:---|
|17.4|[SSDT pour VS2015 17.4](https://go.microsoft.com/fwlink/?linkid=863440)|
|17.3|[SSDT pour VS2015 17.3](https://go.microsoft.com/fwlink/?linkid=858660)|
|16.5|[SSDT pour VS2015 16.5](https://go.microsoft.com/fwlink/?LinkID=832313)|  

<br>

|Version de SSDT| Visual Studio 2013|
|:---|:---|
|16.5|[SSDT pour VS2013 16.5](https://go.microsoft.com/fwlink/?LinkID=832308)|  

<br>


\* SSDT prend en charge les deux dernières versions de Visual Studio. Avec la publication de Visual Studio 2017, SSDT pour VS2013 n’est plus mis à jour. Pour plus d’informations, consultez la section *FAQ* de [ce billet de blog de l’équipe SSDT](https://blogs.msdn.microsoft.com/ssdt/2017/03/10/sql-server-data-tools-17-0-rc-and-ssdt-in-vs2017/).

  
## <a name="links-to-download-pages"></a>Liens vers des pages de téléchargement 
**Moteur de base de données relationnelle SQL**  
  
Fournit des modèles pour la création de bases de données relationnelles pour le SGBDR et Azure SQL Database. SSDT n’est pas lié à une version en ce qui concerne la conception de base de données relationnelle. Vous pouvez utiliser la version 2012 ou 2013 de Visual Studio avec n’importe quelle version du moteur de base de données SQL Server ou Azure SQL Database.  
  
**Concepteurs de bases de données**  
  
-   [Télécharger SSDT pour Visual Studio 2013](https://msdn.microsoft.com/dn864412)  
  
-   [Télécharger SSDT pour Visual Studio 2012](https://msdn.microsoft.com/jj650015)  
  
-   **SSDT pour Visual Studio 2010** n’est plus disponible. Choisissez une version plus récente. Les versions plus récentes de SSDT s’exécutent côte à côte avec les installations existantes de Visual Studio 2010. Il n’est pas nécessaire que SSDT corresponde à la version complète de Visual Studio sur votre ordinateur.  
  
Les clients Visual Studio 2013 peuvent télécharger une version préliminaire de SSDT pour essayer de nouvelles fonctionnalités qui ne figurent pas encore dans la version finale du produit.  
  
**SQL BI : Analysis Services, Reporting Services, Integration services**  
  
Les modèles BI sont utilisés pour créer des modèles SSAS, des rapports SSRS et des packages SSIS. Les concepteurs BI sont liés à des versions spécifiques de SQL Server. Pour utiliser les nouvelles fonctionnalités BI, installez un concepteur BI d’une version plus récente.  
  
**Concepteurs BI**  
  
[Télécharger SSDT-BI pour Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=42313) (SQL Server 2014, SQL Server 2012, SQL Server 2008 et 2008 R2)  
  
[Télécharger SSDT-BI pour Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843) (SQL Server 2014, SQL Server 2012, SQL Server 2008 et 2008 R2)  
  
BIDS (Business Intelligence Development Studio) est installé via le programme d’installation de SQL Server. Il n’existe pas de téléchargement web. (SQL Server 2008 et 2008 R2)  
  
Pour SQL Server 2012 ou 2014, vous pouvez utiliser **SSDT-BI pour Visual Studio 2012** ou **SSDT-BI fou Visual Studio 2013**. La seule différence entre les deux est la version de Visual Studio.  
  
## <a name="see-also"></a> Voir aussi  
[Télécharger SQL Server Data Tools &#40;SSDT&#41;](../ssdt/download-sql-server-data-tools-ssdt.md)  
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
[Outils et utilitaires SQL](../tools/overview-sql-tools.md)
