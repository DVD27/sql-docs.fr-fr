---
title: MSSQLSERVER_102 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee88ba8a77602fd50412669f96e1e16ddcdd37c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62870737"
---
# <a name="mssqlserver_102"></a>MSSQLSERVER_102
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|102|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|P_SYNTAXERR2|  
|Texte du message|Syntaxe incorrecte près de '%.*ls'.|  
  
## <a name="explanation"></a>Explication  
 Indique une erreur de syntaxe. Aucune information supplémentaire n'est disponible, car l'erreur empêche le [!INCLUDE[ssDE](../../includes/ssde-md.md)] de traiter l'instruction.  
  
 Cela peut être dû à une tentative de création d'une clé symétrique à l'aide du chiffrement RC4 ou RC4_128 déconseillé, hors du mode compatibilité 90 ou 100.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Recherchez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] pour les erreurs de syntaxe.  
  
 Si vous créez une clé symétrique à l'aide de RC4 ou RC4_128, sélectionnez un chiffrement plus récent, par exemple un des algorithmes AES. (Recommandé.) Si vous devez utiliser RC4, utilisez ALTER DATABASE SET COMPATIBILITY_LEVEL pour définir la base de données au niveau de compatibilité 90 ou 100. (Non recommandé.)  
  
  
