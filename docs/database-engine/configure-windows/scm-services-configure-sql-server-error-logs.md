---
title: Configurer les journaux des erreurs SQL Server | Microsoft Docs
description: En savoir plus sur le recyclage du journal des erreurs. Découvrez comment définir une taille maximale de fichier journal et comment définir le nombre de fichiers journaux précédents que SQL Server sauvegarde et les archives.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 060b3828c772a030ab095ae1bea857dc8eaa3b5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85651380"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>Services SCM - Configurer les journaux des erreurs SQL Server

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique indique comment consulter ou modifier la méthode de recyclage des journaux d'erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Pour ouvrir la boîte de dialogue Configurer les journaux d'erreurs SQL Server  

1. Dans l’Explorateur d’objets, développez l’instance de SQL Server, puis **Gestion**, cliquez avec le bouton droit sur **Journaux SQL Server**, puis sélectionnez **Configurer**.

2. Dans la boîte de dialogue **Configurer les journaux d'erreurs SQL Server** , choisissez l'une des options suivantes.

    a. Nombre de fichiers journaux

      **Limiter le nombre de fichiers de journaux d'erreurs avant qu'ils ne soient recyclés**

      Activez cette option pour limiter le nombre de journaux d'erreurs créés avant le recyclage. Un nouveau journal des erreurs est créé à chaque démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve des copies de sauvegarde des six derniers journaux, sauf si vous avez activé cette option et spécifié un autre nombre maximal de fichiers de journaux des erreurs ci-dessous.  
  
      **Nombre maximal de fichiers de journaux d'erreurs**

      Spécifiez le nombre maximal de fichiers journaux des erreurs archivés pouvant être créés avant le recyclage. La valeur par défaut est 6, en plus du fichier journal actuel. Cette valeur détermine le nombre de journaux de sauvegarde précédents que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve avant de les recycler.

    b. Taille du fichier journal

      **Taille maximale du fichier journal des erreurs en Ko**

      Vous pouvez définir la taille de chaque fichier en Ko. Si vous indiquez 0, la taille du journal est illimitée.
