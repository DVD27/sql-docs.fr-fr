---
title: Nouvelle colonne dans la sortie de sp_helptrigger peut avoir un impact sur les applications | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 33d47c858a03766260e8ed8c098fef79e9e4a82f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093738"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>La nouvelle colonne dans la sortie de sp_helptrigger peut avoir un impact sur des applications
  trigger_schemaias la dernière colonne du jeu de résultats retournée par le système sp_helptrigger de procédure stockée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Pour obtenir des informations sur les déclencheurs définis sur une table particulière, interrogez l'affichage catalogue sys.triggers.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Vérifiez l'emploi de sp_helptrigger dans vos applications. Vous devrez peut-être modifier vos applications pour tenir compte de cette colonne supplémentaire. Vous pouvez également utiliser l'affichage catalogue sys.triggers à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
