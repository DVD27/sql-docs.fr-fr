---
title: MONTH (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], MONTH
- MONTH function
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 54c699bff247ccf66200f08b6779c80ab1ad84d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941211"
---
# <a name="month-ssis-expression"></a>MONTH (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Renvoie un entier qui représente la partie mois d'une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MONTH(date)  
```  
  
## <a name="arguments"></a>Arguments  
 *date*  
 Date à n'importe quel format de date.  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction MONTH renvoie un résultat NULL si l'argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  La validation de l'expression échoue lorsqu'un littéral de date est explicitement converti en un des types de données de date suivants : DT_DBTIMESTAMPOFFSET et DT_DBTIMESTAMP2.  
  
 L'utilisation de la fonction MONTH est plus directe mais équivalente à celle de la fonction DATEPART("Month", date).  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie le chiffre représentant le mois dans un littéral de date. Si le format de la date est « mm/jj/aaaa », l'exemple renvoie 11.  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 L’exemple suivant renvoie l’entier qui représente le mois dans la colonne **ModifiedDate** .  
  
```  
MONTH(ModifiedDate)  
```  
  
 L'exemple suivant renvoie l'entier qui représente le mois de la date actuelle.  
  
```  
MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATEADD &#40;expression SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;expression SSIS&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;expression SSIS&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;expression SSIS&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [YEAR &#40;expression SSIS&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
