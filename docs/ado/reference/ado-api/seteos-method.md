---
title: SetEOS, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 357778765f0c7ac59d924518340ca34226853fc0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916933"
---
# <a name="seteos-method"></a>SetEOS, méthode
Définit la position de la fin du flux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Notes  
 **SetEOS** met à jour la valeur de la [EOS](../../../ado/reference/ado-api/eos-property.md) propriété, en rendant actuel [Position](../../../ado/reference/ado-api/position-property-ado.md) la fin du flux. Tous les octets ou caractères qui suivent la position actuelle sont tronqués.  
  
 Étant donné que [écrire](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), et [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) ne tronquent aucune valeur supplémentaire existant **Stream** objets, vous pouvez tronquer ces octets ou caractères en définissant la nouvelle position de fin de flux avec **SetEOS**.  
  
> [!CAUTION]
>  Si vous définissez **EOS** à une position avant la fin du flux, vous perdrez toutes les données une fois que le nouvel **EOS** position.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
