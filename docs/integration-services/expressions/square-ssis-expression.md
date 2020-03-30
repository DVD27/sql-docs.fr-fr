---
title: SQUARE (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 06bf3ea82f026a36fece8266354e79992473df44
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71288643"
---
# <a name="square-ssis-expression"></a>SQUARE (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Renvoie le carré d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique d'un type de données numérique. Pour plus d’informations, consultez [Types de données Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 La fonction SQUARE renvoie un résultat NULL si l'argument est NULL.  
  
 L'argument est converti vers le type de données DT_R8 avant le calcul du carré.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie le carré de 12. Le résultat retourné est 144.  
  
```  
SQUARE(12)  
```  
  
 L'exemple suivant renvoie le carré du résultat de la soustraction des valeurs de deux colonnes. Si **Value1** contient 12 et **Value2** contient 4, la fonction SQUARE retourne 64.  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 L'exemple suivant renvoie la longueur du troisième côté d'un triangle rectangle en appliquant la fonction SQUARE à deux variables, puis en calculant la racine carrée de leur somme. Si la variable **Side1** a pour valeur 3 et que la variable **Side2** a pour valeur 4, la fonction SQRT renvoie 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  Dans les expressions, les noms de variables comportent toujours le préfixe \@.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
