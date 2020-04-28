---
title: Définir l’option max degree of parallelism pour des performances optimales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 794dfea63b193ff79fb5831cb3a4e519d7d5f63e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62691384"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Définir l'option max degree of parallelism pour des performances optimales
  Cette règle détermine si l'option max degree of parallelism (MAXDOP) (degré maximum de parallélisme) est définie sur une valeur supérieure à 8. La définition d'une valeur supérieure à 8 conduit souvent à la consommation inutile de ressources et à la dégradation des performances.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Définissez l'option max degree of parallelism sur 8 ou une valeur supérieure à l'aide de sp_configure.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Article 329204 de la Base de connaissances Microsoft](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Configurer l’option de configuration de serveur max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
