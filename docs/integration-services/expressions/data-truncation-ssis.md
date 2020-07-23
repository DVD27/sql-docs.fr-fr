---
title: Troncation de données (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa36ccd8a161c15cf4d12d1f92bb1ec36b1ac0b2
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920629"
---
# <a name="data-truncation-ssis"></a>Troncation de données (SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  La conversion de valeurs de données d’un type vers un autre peut entraîner la troncation de certaines valeurs.  
  
 Cette troncation peut se produire dans les cas suivants :  
  
-   Conversion des données de chaîne du type *DT_WSTR* en données de type *DT_STR* avec la même longueur lorsque la chaîne d’origine contient des caractères codés sur deux octets.  
  
-   Conversion d’un entier du type *DT_I4* vers le type *DT_I2* (des chiffres significatifs risquent d’être perdus).  
  
-   Conversion d’un entier non signé en entier signé (des chiffres significatifs risquent d’être perdus).  
  
-   Conversion d’un nombre réel du type *DT_R8* vers le type *DT_R4* (des chiffres non significatifs risquent d’être perdus).  
  
-   Conversion d’un entier du type *DT_I4* vers le type *DT_R4* (des chiffres non significatifs risquent d’être perdus).  
  
 L'évaluateur d'expression identifie les conversions explicites pouvant provoquer une troncation et émet un avertissement lorsque l'expression est analysée. Par exemple, l'évaluateur d'expression émet un avertissement si vous convertissez une chaîne de 30 caractères en une chaîne de 20 caractères.  
  
 Toutefois, la troncation éventuelle des caractères n’est pas vérifiée au moment de l’exécution. Lors de l’exécution, les données sont tronquées sans avertissement. La plupart des transformations et des adaptateurs de données prennent en charge des sorties d’erreur pouvant gérer la disposition des lignes d’erreur.  
  
 Pour en savoir plus sur la gestion de la troncation des données, consultez [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md).  
  
  
