---
title: Capturer des données d’événement de déclencheur de connexion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1566d1404b7be2af520d26c557550ffb1c3feca7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "72689865"
---
# <a name="capture-logon-trigger-event-data"></a>Capturer des données d'événements de déclencheurs de connexion
[!INCLUDE[tsql-appliesto-ss2008-appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]
  Pour capturer des données XML relatives à des événements LOGON à utiliser dans des déclencheurs de connexion, utilisez la fonction [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md) . L'événement LOGON retourne le schéma des données d'événement suivant :  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 Contient `LOGON`.  
  
 `<PostTime>`  
 Contient l'heure de demande d'établissement d'une session.  
  
 `<SID>`  
 Contient le flux binaire encodé en base 64 du numéro d'identification de sécurité (SID) correspondant au nom de connexion spécifié.  
  
 `<ClientHost>`  
 Contient le nom d'hôte du client à partir duquel a été établie la connexion. La valeur est '`<local_machine>`' si le nom du serveur et du client sont identiques. Sinon, la valeur est l'adresse IP du client.  
  
 `<IsPooled>`  
 Valeur égale à `1` si la connexion est réutilisée à l'aide du groupement de connexions. Sinon, la valeur est `0`.  
  
  
