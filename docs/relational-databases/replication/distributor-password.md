---
title: Mot de passe du serveur de distribution | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: c9a5e8924139cf01a75bf48407c769a839a77f5e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770654"
---
# <a name="distributor-password"></a>Mot de passe du serveur de distribution
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Si, dans la page **Serveurs de publication** de cet Assistant, vous avez autorisé un ou plusieurs serveurs de publication à utiliser ce serveur comme serveur de distribution distant, vous devez définir un mot de passe pour la connexion que la réplication établit entre le serveur de publication et le serveur de distribution distant à l'aide de la connexion **distributor_admin** . Dans la page **Mot de passe d'administration** de l'Assistant Nouvelle publication ou de l'Assistant Configurer le serveur de distribution, vous devez entrer le même mot de passe pour chaque serveur de publication qui utilise le serveur de distribution. Pour plus d’informations sur la sécurité des serveurs de distribution, consultez [Sécuriser le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="options"></a>Options  
 **Mot de passe**  
 Entrez un mot de passe fort pour la connexion entre le serveur de publication et le serveur de distribution distant.  
  
 **Confirmer le mot de passe**  
 Entrez à nouveau le mot de passe pour confirmer la première saisie.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
