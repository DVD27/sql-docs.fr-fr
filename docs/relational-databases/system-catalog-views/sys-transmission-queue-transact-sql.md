---
title: Sys.transmission_queue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- transmission_queue
- sys.transmission_queue_TSQL
- sys.transmission_queue
- transmission_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.transmission_queue catalog view
ms.assetid: f3515d1a-be8f-4a27-8058-8865f0919838
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7bd461a677a7bfab145846baaf09c0a8a62d6f8b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022598"
---
# <a name="systransmissionqueue-transact-sql"></a>sys.transmission_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne pour chaque message dans la file d'attente de transmission, comme indiqué dans le tableau suivant :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**conversation_handle**|**uniqueidentifier**|ID de la conversation à laquelle ce message appartient. Cette colonne n'accepte pas la valeur NULL.|  
|**to_service_name**|**nvarchar (256)**|Nom du service auquel ce message est destiné. Accepte la valeur NULL.|  
|**to_broker_instance**|**nvarchar(128)**|ID du Service Broker qui héberge le service auquel ce message est destiné. Accepte la valeur NULL.|  
|**from_service_name**|**nvarchar (256)**|Nom du service dont ce message provient. Accepte la valeur NULL.|  
|**service_contract_name**|**nvarchar (256)**|Nom du contrat respecté par la conversation pour ce message. Accepte la valeur NULL.|  
|**enqueue_time**|**datetime**|Heure à laquelle le message a été placé en file d'attente. Cette valeur utilise le temps universel indépendamment du fuseau horaire de l'instance. Cette colonne n'accepte pas la valeur NULL.|  
|**message_sequence_number**|**bigint**|Numéro de séquence du message. Cette colonne n'accepte pas la valeur NULL.|  
|**message_type_name**|**nvarchar (256)**|Nom du type de message pour le message. Accepte la valeur NULL.|  
|**is_conversation_error**|**bit**|Indique s'il s'agit d'un message d'erreur.<br /><br /> 0 = N'est pas un message d'erreur.<br /><br /> 1 = Message d'erreur.<br /><br /> Cette colonne n'accepte pas la valeur NULL.|  
|**is_end_of_dialog**|**bit**|Indique s'il s'agit d'un message de fin de conversation. Cette colonne n'accepte pas la valeur NULL.<br /><br /> 0 = N'est pas un message de fin de conversation.<br /><br /> 1 = Message de fin de conversation.<br /><br /> Cette colonne n'accepte pas la valeur NULL.|  
|**message_body**|**varbinary(max)**|Le corps de ce message. Accepte la valeur NULL.|  
|**transmission_status**|**nvarchar(4000)**|Motif pour lequel le message se trouve dans la file d'attente. Il s'agit généralement d'un message d'erreur qui explique pourquoi l'envoi du message a échoué. Si aucune donnée n'est indiquée, le message n'a pas encore été envoyé. Accepte la valeur NULL.|  
|**priority**|**tinyint**|Niveau de priorité assigné à ce message. Cette colonne n'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
