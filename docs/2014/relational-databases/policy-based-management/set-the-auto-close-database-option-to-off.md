---
title: Définir l’option de base de données AUTO_CLOSE sur OFF | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a4353653f4a39a3e7b6dca0a22e8de358ce65c08
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62691506"
---
# <a name="set-the-autoclose-database-option-to-off"></a>Définir l'option de base de données AUTO_CLOSE sur OFF
  Cette règle vérifie si l'option AUTO_ CLOSE est désactivée (OFF). Lorsqu'elle est définie sur ON, cette option peut entraîner une dégradation des performances sur les bases de données fréquemment sollicitées en raison de la surcharge causée par l'ouverture et la fermeture de la base de données après chaque connexion. AUTO_CLOSE vide également le cache de procédure après chaque connexion.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 En cas d'accès fréquent à une base de données, définissez l'option AUTO_CLOSE sur OFF pour la base de données.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
