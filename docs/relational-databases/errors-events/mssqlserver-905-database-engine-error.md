---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8035aa25564e8fe9c9781f5f89065cb7d1b40236
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67903877"
---
# <a name="mssqlserver_905"></a>MSSQLSERVER_905
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|905|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBSTARTUP_EE_PARTITIONING|  
|Texte du message|La base de données '%.*ls' ne peut pas être démarrée dans cette édition de SQL Server, car elle contient une fonction de partition '%.\*ls'. Seule l'édition Entreprise de SQL Server prend en charge le partitionnement.|  
  
## <a name="explanation"></a>Explication  
La base de données contient un ou plusieurs index ou tables partitionnés. Cette édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas utiliser le partitionnement. Par conséquent, la base de données ne peut pas être démarrée correctement. Les tables et les index partitionnés ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
Détachez la base de données à l'aide de la procédure stockée sp_detach_db. Déplacez les fichiers, si nécessaire, puis attachez la base de données à une instance d’une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prise en charge en utilisant CREATE DATABASE avec l’option FOR ATTACH ou FOR ATTACH_REBUILD_LOG. Désactivez le partitionnement sur toutes les tables et supprimez les fonctions de partitionnement. Détachez encore la base de données et rattachez-la au serveur actif.  
  
