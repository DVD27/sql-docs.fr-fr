---
title: ObjectTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
author: rothja
ms.author: jroth
ms.openlocfilehash: d493218f31965c04b5a64321c4a1bf87a2518f6f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763790"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Spécifie le type d’objet de base de données pour lequel définir des autorisations ou la propriété.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|L’objet est une colonne.|  
|**adPermObjDatabase**|3|L’objet est une base de données.|  
|**adPermObjProcedure**|4|L’objet est une procédure.|  
|**adPermObjProviderSpecific**|-1|L’objet est un type défini par le fournisseur. Une erreur se produit si le paramètre *ObjectType* est **adPermObjProviderSpecific** et qu’un *ObjectTypeId* n’est pas fourni.|  
|**adPermObjTable**|1|L’objet est une table.|  
|**adPermObjView**|5|L’objet est une vue.|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[GetObjectOwner, méthode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[GetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[SetObjectOwner, méthode](../../../ado/reference/adox-api/setobjectowner-method.md)|[SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
