---
title: MSSQLSERVER_10537 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0121d16fd25659a40b9c7a05df154028227d8745
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781402"
---
# <a name="mssqlserver_10537"></a>MSSQLSERVER_10537
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|10537|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_DUP_ENABLED|  
|Texte du message|Impossible d’activer le repère de plan '%.*ls', car le repère de plan activé '%.\*ls' contient les mêmes étendue et valeur de décalage de départ que l’instruction. Désactivez le repère de plan existant avant d'activer le repère de plan spécifié.|  
  
## <a name="explanation"></a>Explication  
Un repère de plan existant contient les mêmes étendue et valeur de décalage de départ que l'instruction du repère de plan spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Désactivez le repère de plan existant avant d'activer le repère de plan spécifié.  
  
## <a name="see-also"></a>Voir aussi  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
