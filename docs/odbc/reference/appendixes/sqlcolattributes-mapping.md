---
title: SQLColAttributes, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08abd0128a6fa2a478af0e9dc9c292ff973ace79
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064488"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes, mappage
Lorsqu’une application appelle **SQLColAttributes** via une application ODBC *3.x* pilote, l’appel à **SQLColAttributes** est mappé à **SQLColAttribute** comme suit :  
  
> [!NOTE]
>  Le préfixe utilisé dans *FieldIdentifier* valeurs dans ODBC *3.x* a été modifié depuis que ODBC utilisé dans *2.x*. Le nouveau préfixe est « SQL_DESC » ; le préfixe ancien a été « SQL_COLUMN ».  
  
1.  Si l’application est une application ODBC *2.x* application, *fDescType* est SQL_COLUMN_TYPE, et le type retourné est un type DATETIME concis, les mappages de gestionnaire de pilotes le retour des valeurs de date, time et timestamp codes.  
  
2.  Si *fDescType* est SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE ou SQL_COLUMN_COUNT, les appels du Gestionnaire de pilotes **SQLColAttribute** dans le pilote avec la *FieldIdentifier* argument mappé à SQL_DESC_NAME, SQL_DESC_NULLABLE ou SQL_DESC_COUNT, selon le cas *.* Toutes les autres valeurs de *fDescType* sont transmises au pilote.  
  
 Une application ODBC *3.x* pilote doit prendre en charge tous les ODBC *3.x* *FieldIdentifiers* répertoriés pour **SQLColAttribute**.  
  
 Une application ODBC *3.x* pilote doit prendre en charge SQL_COLUMN_PRECISION SQL_DESC_PRECISION, SQL_COLUMN_SCALE et SQL_DESC_SCALE et SQL_COLUMN_LENGTH et SQL_DESC_LENGTH. Ces valeurs sont différentes, car la précision, échelle et longueur sont définis différemment dans ODBC *3.x* qu’ils l’étaient dans ODBC *2.x*. Pour plus d’informations, consultez [taille de colonne, des chiffres décimaux, transférer la longueur en octets et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe d : Types de données.
