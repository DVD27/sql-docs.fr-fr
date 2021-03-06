---
title: Traçage et relecture d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f441cceed84b873b31c7d4691b08a541a0aee06f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030158"
---
# <a name="tracing-and-replaying-events"></a>Événements de traçage et de relecture
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Dans SMO, le **Trace** et **relecture** des objets dans le <xref:Microsoft.SqlServer.Management.Trace> espace de noms fournissent un accès par programme à la [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] fonctionnalités, qui sont utilisée pour surveiller une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ou [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Vous pouvez capturer et enregistrer des données sur chaque événement dans un fichier ou dans une table en vue d'une analyse ultérieure. Par exemple, vous pouvez surveiller un environnement de production pour savoir quelles sont les procédures qui compromettent les performances en s'exécutant trop lentement.  
  
 Les objets **Trace** et **Replay** fournissent un jeu d'objets qui peuvent être utilisés pour créer des traces sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ces objets peuvent être utilisés au sein de vos propres applications pour créer manuellement des traces pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. En outre, les objets SMO **Trace** peuvent être utilisés pour lire des fichiers et des tables SQL Trace créés en surveillant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ou l'enregistrement DTS.  
  
 Les objets SMO **Trace** vous permettent de réaliser les fonctions suivantes :  
  
-   Créer une trace.  
  
-   Définir des filtres sur la trace.  
  
-   Définir les événements qui sont tracés.  
  
-   Arrêter ou démarrer une trace.  
  
-   Lire des fichiers ou des tables de trace.  
  
-   Obtenir des informations sur les événements d'une trace.  
  
-   Obtenir des informations sur les filtres d'une trace.  
  
-   Manipuler des données de trace par programme.  
  
-   Écrire des fichiers ou des tables de trace.  
  
-   Relire des fichiers ou des tables de trace.  
  
 Les données de trace des objets **Trace** et **Replay** peuvent être utilisées par l'application SMO ou être examinées manuellement en utilisant [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). Les données de trace sont également compatibles avec les procédures stockées [SQL Trace](../../../relational-databases/sql-trace/sql-trace.md) qui proposent également des fonctionnalités de suivi.  
  
 Les objets de trace SMO résident dans l'espace de noms <xref:Microsoft.SqlServer.Management.Trace>, qui requiert une référence au fichier Microsoft.SQLServer.ConnectionInfo.dll.  
  
 Le **Trace** et **relecture** objets nécessitent un [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> objet pour établir une connexion avec l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) objet réside dans le [Microsoft.SqlServer.Management.Common](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common) espace de noms, qui requiert une référence au fichier Microsoft.SQLServer.ConnectionInfo.dll.  
  
> [!NOTE]  
>  Les objets **Trace** et **Replay** ne sont pas pris en charge sur une plate-forme 64 bits.  
  
  
