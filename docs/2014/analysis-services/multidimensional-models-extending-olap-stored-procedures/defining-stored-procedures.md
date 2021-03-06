---
title: Définition de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 69daca3a13cf5318e102002f0edfcb98b80ff9d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62702772"
---
# <a name="defining-stored-procedures"></a>Définition de procédures stockées
  Vous pouvez utiliser des procédures stockées pour appeler des routines externes à partir de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Vous pouvez écrire les routines externes appelées par une procédure stockée dans n'importe quel langage CLR (Common Language Runtime), comme C, C++, C#, Visual Basic ou Visual Basic .NET. Une procédure stockée peut être créée une fois et être ensuite appelée à partir de nombreux contextes, par exemple par d'autres procédures stockées, par des mesures calculées ou par des applications clientes. Les procédures stockées simplifient le développement et l'implémentation des bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en permettant de développer une fois du code commun et de le stoker dans un emplacement unique. Les procédures stockées peuvent être utilisées pour ajouter à vos applications des fonctionnalités métier qui ne sont pas fournies par les fonctionnalités natives de MDX.  
  
 Cette section contient les informations nécessaires pour comprendre, concevoir et mettre en œuvre des procédures stockées.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Conception de procédures stockées](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Explique comment concevoir des assemblys pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Création de procédures stockées](creating-stored-procedures.md)|Explique comment créer des assemblys pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Appel de procédures stockées](calling-stored-procedures.md)|Fournit des informations sur l'utilisation des assemblys dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Accès au contexte de requête dans les procédures stockées](accessing-query-context-in-stored-procedures.md)|Explique comment accéder aux informations d'étendue et de contexte avec des assemblys.|  
|[Définition de la sécurité des procédures stockées](setting-security-for-stored-procedures.md)|Explique comment configurer la sécurité des assemblys dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Débogage de procédures stockées](debugging-stored-procedures.md)|Explique comment déboguer les assemblys dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèles multidimensionnels](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
