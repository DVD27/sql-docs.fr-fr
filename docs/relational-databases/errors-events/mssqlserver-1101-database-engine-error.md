---
title: MSSQLSERVER_1101 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 676f0d1d131e8cc1a1c5265384bcd53cf11e9dab
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68116179"
---
# <a name="mssqlserver_1101"></a>MSSQLSERVER_1101
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1101|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NOALLOCPG|  
|Texte du message|Impossible d’allouer une nouvelle page pour la base de données ’%.*ls’ en raison d’un espace disque insuffisant dans le groupe de fichiers ’%.\*ls’. Créez l'espace nécessaire en supprimant des objets dans le groupe de fichiers, en ajoutant des fichiers supplémentaires au groupe de fichiers ou en définissant Autogrowth à ON pour les fichiers existants dans le groupe de fichiers.|  
  
## <a name="explanation"></a>Explication  
Il n’y a pas d’espace disque disponible dans un groupe de fichiers.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Les actions ci-dessous peuvent éventuellement créer de l'espace disponible dans le groupe de fichiers.  
  
-   Activez la croissance automatique.  
  
-   Ajoutez d'autres fichiers au groupe de fichiers.  
  
-   Libérez de l'espace disque en supprimant les index ou les tables inutiles dans le groupe de fichiers.  
  
