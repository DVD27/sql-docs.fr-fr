---
title: Compléter des extraits de code Transact-SQL
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2109b236bc13e8335e619ed90b8ee9a33ca08844
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254004"
---
# <a name="complete-transact-sql-snippets"></a>Compléter des extraits de code Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Une fois un extrait de code [!INCLUDE[tsql](../../includes/tsql-md.md)] inséré dans un script, vous modifiez le contenu de l'extrait de code pour générer une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] complète.  
  
## <a name="completing-snippets"></a>Compléter des extraits de code  
 Lorsque vous ajoutez un extrait de code [!INCLUDE[tsql](../../includes/tsql-md.md)] à votre script, l'instruction de l'extrait de code insérée présente un ou plusieurs points de remplacement, mis en surbrillance. Si vous placez le pointeur de votre souris sur un point de remplacement, une info-bulle apparaît avec une description de l'élément syntaxique que vous pouvez spécifier. L’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] reconnaît l’extrait de code comme un élément distinct du script environnant jusqu’à ce que vous fermiez le fichier source. Les points de remplacement restent actifs jusqu'à la fermeture du fichier source.  
  
 Vous pouvez également ajouter des éléments syntaxiques supplémentaires au code du modèle inséré par un extrait de code. Par exemple, le modèle d'extrait de code Create Table génère deux définitions de colonne ; vous devez ajouter des définitions de colonne supplémentaires pour créer une table avec plus de deux colonnes.  
  
#### <a name="completing-the-snippet-statement"></a>Compléter l'instruction de l'extrait de code  
  
1.  Utilisez la touche TABULATION pour passer d'un point de remplacement au suivant. Utilisez SHIFT+TAB pour revenir au point de remplacement précédent.  
  
2.  Cliquez sur CTRL+SPACE pour appeler IntelliSense.  
  
3.  Sélectionnez un élément dans la liste ou tapez le code de remplacement de votre choix.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer des extraits de code Transact-SQL](../../relational-databases/scripting/insert-transact-sql-snippets.md)   
 [Insérer des extraits de code d’entourage (surround-with) Transact-SQL](../../relational-databases/scripting/insert-surround-with-transact-sql-snippets.md)  
  
  
