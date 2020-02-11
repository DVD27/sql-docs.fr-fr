---
title: Remarques sur la sécurité des threads sur les fonctions d’API (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 926b2285bcce9a28579fffc4004c5454b2837392
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912434"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Remarques sur la cohérence des threads dans les fonctions de l’API (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle est thread-safe ; Toutefois, Oracle n’autorise pas plusieurs instructions simultanées sur une seule connexion. Le pilote applique cette restriction. En d’autres termes, dans les applications multithread, bien que n’importe quel thread puisse appeler le pilote ODBC pour Oracle à tout moment, le pilote bloque tout autre thread du pilote sur la même connexion jusqu’à ce que le thread d’origine quitte le pilote.  
  
 Le pilote n’est pas bloqué s’il y a deux instructions sur deux connexions différentes. Toutefois, s’il existe une seule connexion avec deux instructions, il existe un risque de blocage.
