---
title: srv_pfieldex (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8bacfd4f955f60b17b439c8066a3b1cba2c52392
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63126954"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a>srv_pfieldex (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Retourne un pointeur vers des données qui contiennent le champ SRV_PROC demandé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *case*  
 Spécifie le champ *srvproc* à retourner.  
  
|Champ|Description|Type renvoyé|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|LCID du message de la session active.|ULONG*|  
|SRV_INSTANCENAME|Nom de l'instance (si elle est nommée) ; sinon, retourne NULL.|WCHAR*|  
  
 *Len*  
 Pointeur vers une variable **int** contenant la longueur de la valeur *field* retournée en octets. Si *len* a la valeur NULL, la longueur n’est pas retournée. Quand NULL est retourné **len* a la valeur 0.  
  
## <a name="returns"></a>Retours  
 Pointeur vers des données dont le type dépend de *field*. NULL est retourné quand *len* a la valeur 0 ou quand *srvproc* a la valeur NULL. Si *field* est inconnu, la valeur NULL est retournée. Quand NULL est retourné **len* a la valeur 0.  
  
> [!IMPORTANT]  
>  La mémoire tampon retournée à partir du serveur doit être en lecture seule. Dans le cas contraire, l'état du serveur peut être endommagé.  
  
## <a name="remarks"></a>Notes  
 **Note de sécurité** Vous devez examiner minutieusement le code source des procédures stockées étendues, et vous devez tester les dll compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
