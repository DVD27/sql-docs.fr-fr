---
title: Méthode RemoveCertificate (classe ServerSettings) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9fb16415d3422035f67722f36c05cca10d1a3248
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62735902"
---
# <a name="removecertificate-method-serversettings-class"></a>Méthode RemoveCertificate (classe ServerSettings)
  Supprime le certificat de sécurité actuel de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a>Éléments  
 *dessin*  
 Objet de [classe ServerSettings](serversettings-class.md) qui représente les paramètres du serveur sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur u`int32` égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
