---
title: srv_alloc (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_alloc
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
author: rothja
ms.author: jroth
ms.openlocfilehash: 91b6f1ac9d8fcf551ebc786368791354a7d6c27e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68064194"
---
# <a name="srv_alloc-extended-stored-procedure-api"></a>srv_alloc (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Alloue la mémoire dynamiquement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
```  
  
## <a name="arguments"></a>Arguments  
 *size*  
 Spécifie le nombre d'octets à allouer.  
  
## <a name="returns"></a>Retours  
 Un pointeur vers l'espace qui vient d'être alloué. Si *size* octets ne peuvent pas être alloués, un pointeur Null est retourné.  
  
## <a name="remarks"></a>Notes  
 La fonction **srv_alloc** est équivalente à la fonction API [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **GlobalAlloc**. Les fonctions ordinaires de gestion de la mémoire du runtime C de l'API Windows peuvent être utilisées dans une application API de procédure stockée étendue.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
