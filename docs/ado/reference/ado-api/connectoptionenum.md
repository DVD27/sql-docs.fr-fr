---
title: ConnectOptionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 819fb89d7f8c43e76ba9260a72fafa68084bf880
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933448"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Spécifie si le [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet doit retourner une fois la connexion est établie (synchrone) ou avant (de façon asynchrone).  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Ouvre la connexion de façon asynchrone. Le [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) événement peut être utilisé pour déterminer quand la connexion est disponible.|  
|**adConnectUnspecified**|-1|Valeur par défaut. Ouvre la connexion de façon synchrone.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
