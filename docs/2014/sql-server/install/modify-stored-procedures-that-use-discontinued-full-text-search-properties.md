---
title: Modifier les procédures stockées qui utilisent des propriétés de recherche en texte intégral supprimées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5204b27fb4745f8005a328dc62503f7db418387d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093848"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a>Modifier les procédures stockées qui utilisent des propriétés de recherche en texte intégral obsolètes
  Pour garantir le bon fonctionnement de vos procédures stockées, vous devez modifier les procédures existantes et supprimer les propriétés et les paramètres liées au texte intégral qui n'existent plus ou sont déconseillés.  
  
## <a name="component"></a>Composant  
 Recherche en texte intégral  
  
## <a name="description"></a>Description  
 Les propriétés et paramètres suivants associés à la recherche en texte intégral ont été supprimés.  
  
-   **DataTimeout**  
  
-   **ConnectTimeout**  
  
-   **Clean_up**  
  
-   **LogSize**  
  
 Les propriétés et paramètres suivants associés à la recherche en texte intégral ont été supprimés ou déconseillés.  
  
-   'Path' du catalogue de texte intégral. Le catalogue de texte intégral est un objet logique sans chemin d'accès de fichier spécifique dans le système.  
  
-   L'activation/désactivation de SP_FULLTEXT_DATABASE n'a plus aucun effet puisque les bases de données sont activées pour la recherche en texte intégral à tous moments et par défaut dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez vos procédures stockées de manière à supprimer ces propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
