---
title: Éditeur de destination SQL (page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d3bffc98a14c1a8bc672e9f15a4bad8b6f5a7dbe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055408"
---
# <a name="sql-destination-editor-connection-manager-page"></a>Éditeur de destination SQL (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination SQL** pour spécifier des informations sur la source de données et afficher un aperçu des résultats. La [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destination charge les données dans des tables ou des [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vues d’une base de données.  
  
 Pour en savoir plus sur la destination pour SQL Server, consultez [SQL Server Destination](data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une connexion en cliquant sur **Nouvelle**.  
  
 **Nouvelle**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** .  
  
 **Utiliser une table ou une vue**  
 Sélectionnez une table ou une vue existante dans la liste, ou créez une connexion en cliquant sur **Nouvelle**.  
  
 **Nouvelle**  
 Utilisez la boîte de dialogue **Créer une table** pour créer une table.  
  
> [!NOTE]  
>  Lorsque vous cliquez **New**sur nouveau [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , génère une instruction CREATE table par défaut basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table** . Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **PRÉVERSION**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Visualiser les résultats de la requête** . L'aperçu peut afficher jusqu'à 200 lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination SQL &#40;page Mappages&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [Éditeur de destination SQL &#40;page avancé&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md)   
 [Charger des données en masse à l'aide de la destination SQL Server](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
