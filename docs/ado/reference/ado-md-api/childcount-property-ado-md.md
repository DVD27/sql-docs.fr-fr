---
title: ChildCount, propriété (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8e6f6a7cb749ff2b22a1f7563b43ce07e060aab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67911553"
---
# <a name="childcount-property-ado-md"></a>ChildCount, propriété (ADO MD)
Indique le nombre de membres pour lesquels actuel [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objet est le parent dans une hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **Long** entier et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **ChildCount** propriété pour retourner une estimation du nombre d’enfants un **membre** a. Les enfants réelles d’un **membre** peuvent être retournés par la [enfants](../../../ado/reference/ado-md-api/children-property-ado-md.md) propriété.  
  
 Pour **membre** objets à partir d’un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) de l’objet, le nombre maximum renvoyé est 65 536. Si le nombre réel d’enfants dépasse 65 536, la valeur retournée sera toujours 65536. Par conséquent, l’application doit interpréter un **ChildCount** de 65 536 comme égale ou supérieure à 65 536 enfants.  
  
 Pour **membre** objets à partir d’un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) d’objet, utilisez la collection ADO [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété sur le **enfants** collection pour déterminer le nombre exact d’enfants. Peut être lente si le nombre d’enfants dans la collection est important de déterminer le nombre exact d’enfants.  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Enfants, propriété (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Members, collection (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
