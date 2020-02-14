---
title: max full-text crawl range (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 740d952640cef0400c379e9dfb25157331c9bfab
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68023755"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>max full-text crawl range (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **max full-text crawl range** pour optimiser l’utilisation du processeur, ce qui permet d’améliorer les performances de l’analyse durant une analyse complète. Avec cette option, vous pouvez spécifier le nombre de partitions que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit utiliser au cours d’une analyse d’index de recherche en texte intégral. Par exemple, s'il existe plusieurs processeurs et si leur utilisation n'est pas optimale, vous pouvez augmenter la valeur maximale de cette option. En plus de cette option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise d'autres facteurs, tels que le nombre de lignes d'une table et le nombre de processeurs, pour déterminer le nombre réel de partitions utilisées.  
  
 La valeur par défaut de cette option est 4, la valeur minimale est 1 et la valeur maximale est 256. Les modifications apportées à cette option affectent uniquement les analyses ultérieures. Les analyses en cours d'exécution ne seront pas affectées par une modification de cette option.  
  
 L’option **max full-text crawl range** est une option avancée. Si vous utilisez la procédure stockée système **sp_configure** pour modifier sa valeur, vous ne pouvez modifier l’option **max full-text crawl range** que si l’option **show advanced options** a la valeur 1. Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
