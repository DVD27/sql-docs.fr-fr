---
title: srv_paraminfo (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paraminfo
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f3c89eb2e6f810902e28e01c7e5ffbcdcc0375c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63127187"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a>srv_paraminfo (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Retourne des informations sur un paramètre. Cette fonction remplace les fonctions suivantes : [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md) et [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md). **srv_paraminfo** prend en charge les types de données dans les [types](data-types-extended-stored-procedure-api.md) de données et les données de longueur nulle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Handle d'une connexion cliente.  
  
 *n*  
 Nombre ordinal du paramètre à définir. Le premier paramètre est 1.  
  
 *pbType*  
 Type de données du paramètre.  
  
 *pcbMaxLen*  
 Pointeur vers la longueur maximale du paramètre.  
  
 *pcbActualLen*  
 Pointeur vers la longueur réelle du paramètre. La valeur 0 (\**pcbActualLen* == 0) indique des données de longueur nulle si **pfNull* a la valeur FALSE.  
  
 *pbData*  
 Pointeur vers la mémoire tampon des données de paramètre. Si *pbData* n’est pas NULL, l’API de procédure stockée étendue écrit \**pcbActualLen* octets de données dans \**pbData*. Si *pbData* est NULL, aucune donnée n’est écrite dans \**pbData*, mais la fonction retourne \**pbType*, \**pcbMaxLen*, \**pcbActualLen* et **pfNull*. Cette mémoire tampon doit être gérée par l'application.  
  
 *pfNull*  
 Pointeur vers un indicateur null. **pfNull* est défini sur true si la valeur du paramètre est null.  
  
## <a name="returns"></a>Retours  
 Si les informations sur le paramètre ont été obtenues avec succès, la valeur SUCCEED est retournée ; sinon, FAIL. La valeur FAIL est retournée en l’absence de procédure stockée distante active ou en l’absence d’un *n*ième paramètre de procédure stockée.  
  
## <a name="remarks"></a>Notes  
 **Note de sécurité** Vous devez examiner minutieusement le code source des procédures stockées étendues, et vous devez tester les dll compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence du programmeur sur les procédures stockées étendues](database-engine-extended-stored-procedures-reference.md)  
  
  
