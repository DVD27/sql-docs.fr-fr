---
title: srv_willconvert (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_willconvert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: c9930810e5f8253fb3ba3fdddb8fd16875bbcd9b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85026979"
---
# <a name="srv_willconvert-extended-stored-procedure-api"></a>srv_willconvert (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Détermine si une conversion de type de données spécifique est disponible au sein de la bibliothèque ODS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srctype*  
 Indique le type de données des données à convertir. Ce paramètre peut être n'importe lequel des types de données des API de procédure stockée étendue.  
  
 *desttype*  
 Indique le type de données vers lequel les données sources sont converties. Ce paramètre peut être n'importe lequel des types de données des API de procédure stockée étendue.  
  
## <a name="returns"></a>Retours  
 TRUE si la conversion de type de données est prise en charge ; FALSE, dans le cas contraire.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir une description de chaque type de données, consultez [Types de données &#40;API de procédure stockée étendue&#41;](data-types-extended-stored-procedure-api.md).  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_convert &#40;API de procédure stockée étendue&#41;](srv-convert-extended-stored-procedure-api.md)  
  
  
