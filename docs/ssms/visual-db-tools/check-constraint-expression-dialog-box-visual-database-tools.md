---
title: Boîte de dialogue Expression de contrainte de validation
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: fcd0eacf11390947248208310eba3ddec40089ce
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75255500"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a>Boîte de dialogue Expression de contrainte de validation (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Lorsque vous rattachez une contrainte de validation à une table ou une colonne, vous devez inclure une expression SQL. Entrez l'expression de contrainte de validation dans la zone fournie à cet effet.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
Expression  
Entrez l'expression  
  
Vous pouvez créer une expression de contrainte simple pour valider les données en fonction d'une condition simple ou créer une expression complexe, à l'aide d'opérateurs booléens, pour valider les données en fonction de plusieurs conditions. Supposons, par exemple, que la table authors comporte une colonne zip nécessitant une chaîne de caractères de 5 chiffres. L'expression de contrainte suivante permet de s'assurer que seuls les nombres de 5 chiffres sont acceptés :  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
Ou imaginons que la table sales comporte une colonne qty dans laquelle il est nécessaire d'entrer des valeurs supérieures à 0. L'expression de contrainte suivante assure que cette colonne contiendra exclusivement des valeurs positives :  
  
```  
qty > 0  
```  
  
Ou supposons que la table orders indique le type de cartes de crédit qu'il est nécessaire de posséder pour passer une commande. La contrainte suivante garantit que seules les cartes de crédit Visa, MasterCard ou American Express sont acceptées :  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a>Pour définir une expression de contrainte  
Sous l'onglet Vérifier les contraintes des pages de propriétés, tapez l'expression dans la zone Expression de contrainte en respectant la syntaxe suivante :  
  
<pre>{constant | column_name | function | (subquery)}  
[{operator | AND | OR | NOT}  
{constant | column_name | function | (subquery)}...]</pre>  
  
La syntaxe SQL est constituée des paramètres suivants :  
  
|Paramètre|Description|  
|-------------|---------------|  
|constant|Valeur littérale (données numériques ou caractères). N'oubliez pas d'insérer les chaînes de caractères entre guillemets simples (').|  
|column_name|Spécifie une colonne.|  
|function|Fonction intégrée.|  
|operator|Opérateur arithmétique, de comparaison, de chaîne ou au niveau du bit.|  
|AND|Utilisez AND dans les expressions booléennes pour relier deux expressions. Les résultats sont retournés lorsque les deux expressions sont vraies.<br /><br />Lorsque AND et OR sont tous deux utilisés dans une instruction, AND est traité en premier. Vous pouvez changer l'ordre d'exécution en utilisant des parenthèses.|  
|OR|Utilisez OR dans les expressions booléennes pour relier plusieurs expressions. Les résultats sont retournés lorsque l'une ou l'autre des expressions est vraie.<br /><br />Lorsque AND et OR sont tous deux utilisés dans une instruction, OR est évalué après AND. Vous pouvez changer l'ordre d'exécution en utilisant des parenthèses.|  
|NOT|Inverse une expression booléenne (qui peut inclure des mots clés, tels que LIKE, NULL, BETWEEN, IN et EXISTS).<br /><br />Lorsqu'une instruction contient plusieurs opérateurs logiques, NOT est traité en premier. Vous pouvez changer l'ordre d'exécution en utilisant des parenthèses.|  
  
## <a name="see-also"></a>Voir aussi  
[Contraintes uniques et contraintes de validation](../../relational-databases/tables/unique-constraints-and-check-constraints.md)  
[Créer des contraintes uniques](../../relational-databases/tables/create-unique-constraints.md)  
  
