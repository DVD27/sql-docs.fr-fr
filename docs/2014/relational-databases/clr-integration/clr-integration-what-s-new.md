---
title: Nouveautés de&#39;dans l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 45e4f0578d06eeafc545bea2b6374a37b8ef7cbc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874070"
---
# <a name="what39s-new-in-clr-integration"></a>Nouveautés de&#39;dans l’intégration du CLR
  Voici les nouvelles fonctionnalités apportées à l'intégration du CLR dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] :  
  
-   Dans la version 4 du CLR, les objets de base de données CLR n'interceptent plus des exceptions d'état endommagées. Ces exceptions sont maintenant interceptées dans l'intégration du CLR qui héberge la couche. Ces exceptions peuvent toujours être interceptées par les composants de base de données CLR en définissant un attribut de code ([\<legacyCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)). Toutefois, cette opération n'est pas recommandée car les résultats ne sont pas fiables lorsqu'une exception d'état endommagée se produit.  
  
-   En raison des strictes conditions de sécurité de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], les composants de base de données CLR continueront à utiliser le modèle de sécurité d'accès du code défini dans la version 2.0 du CLR.  
  
-   Dans la version 4 du CLR, une erreur de format dans une valeur `System.TimeSpan` générera un `System.FormatExceptions`. Avant la version 4 du CLR, une erreur de format dans une valeur `System.TimeSpan` était ignorée. Les applications de base de données qui s'appuient sur le comportement antérieur à la version 4 du CLR doivent s'exécuter avec un niveau de compatibilité de base de données (`ALTER DATABASE Compatibility Level`) de 100 ou inférieur. Pour plus d’informations, consultez [<TimeSpan_LegacyFormatMode élément>](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   La version 4 du CLR prend en charge Unicode 5.1. Les opérations de tri qui impliquent des accents et des symboles vont faire l'objet d'améliorations. Des problèmes de compatibilité peuvent survenir si votre application s'appuie sur un comportement de tri hérité. Pour activer le tri hérité, le niveau de compatibilité de la base de données (`ALTER DATABASE Compatibility Level`) doit être défini sur 100 ou inférieur. Pour prendre en charge cette fonctionnalité, [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] installe sort00001000.dll dans le répertoire du .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Pour plus d’informations, consultez [ \<CompatSortNLSVersion>, élément](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Les colonnes suivantes ont été ajoutées à [sys. dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`, `total_allocated_memory_kb`et `survived_memory_kb`.  
  
  
