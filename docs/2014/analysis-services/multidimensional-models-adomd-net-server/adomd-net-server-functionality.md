---
title: Fonctionnalités du serveur ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95e0627e4f794050438ba392be6911d661f243aa
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537385"
---
# <a name="adomdnet-server-functionality"></a>Fonctionnalités serveur ADOMD.NET
  Tous les objets serveur ADOMD.NET fournissent un accès en lecture seule aux données et aux métadonnées présentes sur le serveur. Pour récupérer les données et les métadonnées, vous devez utiliser le modèle d'objet serveur ADOMD.NET, car le modèle d'objet serveur ne prend pas en charge les ensembles de lignes de schéma.  
  
 Avec les objets serveur ADOMD.NET, vous pouvez créer une fonction définie par l’utilisateur (UDF) ou une procédure stockée pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Ces méthodes in-process sont appelées par l'intermédiaire d'instructions de requête créées dans des langages tels que MDX (Multidimensional Expressions), DMX (Data Mining Extensions) ou SQL. Ces méthodes in-process fournissent également des fonctionnalités supplémentaires sans les temps d'attente inhérents aux communications réseau.  
  
> [!NOTE]  
>  L'objet <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> ne prend en charge que le langage DMX.  
  
## <a name="what-is-a-udf"></a>Qu'est qu'une fonction définie par l'utilisateur ?  
 Une fonction *définie* par l’un est une méthode qui présente les caractéristiques suivantes :  
  
-   Vous pouvez appeler une fonction définie par l'utilisteur dans le contexte d'une requête.  
  
-   Une fonction définie par l'utilisateur peut prendre un nombre illimité de paramètres.  
  
-   Une fonction définie par l'utilisateur peut retourner divers types de données.  
  
 L'exemple suivant utilise la fonction définie par l'utilisateur fictive `FinalSalesNumber` :  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a>Qu'est-ce qu'une procédure stockée ?  
 Une *procédure stockée* est une méthode qui présente les caractéristiques suivantes :  
  
-   Vous appelez une procédure stockée seule avec l’instruction MDX [Call](/sql/mdx/mdx-data-manipulation-call) .  
  
-   Une procédure stockée peut prendre un nombre illimité de paramètres.  
  
-   Une procédure stockée peut retourner un jeu de données, un `IDataReader` ou un résultat vide.  
  
 L'exemple suivant utilise la procédure stockée fictive `FinalSalesNumbers` :  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du serveur ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
