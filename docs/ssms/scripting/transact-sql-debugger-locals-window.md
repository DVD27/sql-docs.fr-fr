---
title: Variables locales (fenêtre)
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 70ee1eee120c94e7f851bc37c3becf1983a57d09
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253049"
---
# <a name="transact-sql-debugger---locals-window"></a>Débogueur Transact-SQL - Fenêtre Variables locales

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fenêtre **Variables locales** affiche des informations sur les expressions locales dans l'étendue actuelle du débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] . L'étendue est définie selon le frame de pile des appels actuellement sélectionné dans la fenêtre **Pile des appels** . Vous devez être en mode débogage pour afficher les expressions locales.  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>Liste des tâches

**Pour accéder à la fenêtre Variables locales**
  
-   Dans le menu **Déboguer** , cliquez sur **Fenêtres**, puis sur **Variables locales**.  
  
 **Pour modifier la valeur d'une expression**  
  
-   Cliquez avec le bouton droit sur l’expression, puis sélectionnez **Modifier la valeur**.  
  
## <a name="columns"></a>Colonnes  
 **Nom**  
 Nom de l'expression locale. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] répertorie les variables, les paramètres et les fonctions système dont les noms commencent par @@.  
  
 **Valeur**  
 Affiche la valeur actuellement assignée à l'expression locale. Cette colonne est vide si aucune valeur n'a été assignée à l'expression.  
  
 Si la longueur d'une expression dépasse la largeur de la colonne **Valeur** , une info-bulle affiche la valeur complète lorsque vous placez le pointeur sur la cellule **Valeur** de cette expression.  
  
 La présence d'une icône de loupe dans une cellule **Valeur** indique que le visualiseur du débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] est disponible. Dans la liste, vous pouvez spécifier **Visualiseur de texte**, **Visualiseur XML**ou **Visualiseur HTML**. Pour démarrer un visualiseur du débogueur, cliquez sur l'icône de loupe. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ouvre une boîte de dialogue qui affiche les données dans un format adapté au type de données.  
  
 **Type**  
 Affiche le type de données de l'expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Informations du débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [Espion (fenêtre)](../../relational-databases/scripting/transact-sql-debugger-watch-window.md)   
 [Fenêtre Pile des appels](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Boîte de dialogue Espion express](../../relational-databases/scripting/transact-sql-debugger-quickwatch-dialog-box.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
