---
title: AcceptStop, propriété (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- AcceptStop Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ff1d3f0a184c928a103abeaa6e957ebd5f9ba314
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67929767"
---
# <a name="acceptstop-property-sqlservice-class"></a>Propriété AcceptStop (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient la valeur de propriété booléenne qui spécifie si le service peut être arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.AcceptStop [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Un [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) objet qui représente le service  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur booléenne qui spécifie si le service peut être arrêté : **true** si le service peut être arrêté, ou **false** si le service ne peut pas être arrêté.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
