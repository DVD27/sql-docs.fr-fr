---
title: Limitations des noms de colonne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], column names
- ODBC desktop database drivers [ODBC], column names
ms.assetid: 5a339f61-c52f-40ad-8deb-d785f72753d4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 14e62555db2e88c6573f3bdca0d4a1a2733d428b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006239"
---
# <a name="column-name-limitations"></a>Limitations des noms de colonne
Les noms de colonne peuvent contenir des caractères valides (par exemple, des espaces). Si les noms de colonnes contiennent des caractères à l’exception des lettres, des chiffres et des traits de soulignement, le nom doit être délimité en l’entourant de guillemets précédent (').  
  
 Lorsque le pilote Microsoft Access ou Microsoft Excel est utilisé, les noms de colonne sont limités à 64 caractères et noms longs génèrent une erreur. Lorsque le pilote Paradox est utilisé, le nom de colonne maximale est de 25 caractères. Lorsque le pilote de texte est utilisé, le nom de colonne maximale est de 64 caractères, et les noms plus longs sont tronqués.  
  
 Lorsque le pilote dBASE est utilisé, les caractères avec une valeur ASCII supérieure à 127 sont convertis en traits de soulignement.  
  
 Lorsque le pilote Microsoft Excel est utilisé, si les noms de colonne sont présents, ils doivent être dans la première ligne. Un nom qui, dans Microsoft Excel, utilisez le « ! » caractères doivent être encadrée de guillemets précédent ('). Le « ! » caractère est converti vers le caractère « $», car le « ! » caractère n’est pas valide dans un nom ODBC, même lorsque le nom est placé entre guillemets précédent. Tous les autres caractères valides de Microsoft Excel (à l’exception de la barre verticale (&#124;)) peut être utilisé dans un nom de colonne, y compris les espaces. Un identificateur délimité doit être utilisé pour un nom de colonne de Microsoft Excel pour inclure un espace. Les noms de colonne non spécifié seront remplacés par des noms générés par le pilote, par exemple, « Col1 » pour la première colonne.  
  
 Le caractère barre verticale (&#124;) ne peut pas être utilisé dans un nom de colonne, si le nom est indiqué entre guillemets précédent ou non.  
  
 Lorsque le pilote de texte est utilisé, le pilote fournit un nom par défaut si un nom de colonne n’est pas spécifié. Par exemple, le pilote appelle la première colonne F1, la deuxième colonne F2 et ainsi de suite.
