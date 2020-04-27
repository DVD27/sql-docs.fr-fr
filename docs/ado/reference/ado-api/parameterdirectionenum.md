---
title: ParameterDirectionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 68aaa0bfb8aa72c9e94a8b5db65768fe85895f0e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917739"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Spécifie si le [paramètre](../../../ado/reference/ado-api/parameter-object.md) représente un paramètre d’entrée, un paramètre de sortie, à la fois un paramètre d’entrée et un paramètre de sortie, ou la valeur de retour d’une procédure stockée.  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|Par défaut. Indique que le paramètre représente un paramètre d’entrée.|  
|**adParamInputOutput**|3|Indique que le paramètre représente à la fois un paramètre d’entrée et un paramètre de sortie.|  
|**adParamOutput**|2|Indique que le paramètre représente un paramètre de sortie.|  
|**adParamReturnValue**|4|Indique que le paramètre représente une valeur de retour.|  
|**adParamUnknown**|0|Indique que la direction du paramètre est inconnue.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums. ParameterDirection. OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[CreateParameter, méthode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Direction, propriété](../../../ado/reference/ado-api/direction-property.md)|
