---
title: Relire jusqu’à un point d’arrêt
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 046f916a5aba5add44c32cb9e761dd1858b86783
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307439"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a>Relecture jusqu'à un point d'arrêt (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette rubrique explique comment définir des points d'arrêt dans un fichier ou une table de trace que vous souhaitez relire à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. La définition de points d'arrêt dans un fichier ou une table de trace avant de démarrer la relecture de cette dernière vous permet de suspendre la relecture de la trace lorsque surviennent des événements spécifiques. L'utilisation de points d'arrêt pendant la relecture d'une trace n'empêche pas le débogage. Vous pouvez en effet fractionner la relecture de scripts de trace longs en petits segments, qui peuvent être analysés de façon incrémentielle.  
  
### <a name="to-replay-to-a-breakpoint"></a>Pour relire jusqu'à un point d'arrêt  
  
1.  Ouvrez le fichier de trace ou la table de trace à relire. Pour plus d’informations, consultez [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) ou l'Assistant Paramétrage du [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Vérifiez que le fichier de trace ou la table de trace que vous ouvrez contient les classes d'événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  Dans la fenêtre de trace, cliquez sur un événement à utiliser comme point d'arrêt. Pour définir un point d'arrêt, employez l'une des trois méthodes suivantes :  
  
    -   Appuyez sur F9.  
  
    -   Dans le menu **Relire** , cliquez sur **Basculer le point d’arrêt**.  
  
    -   Cliquez avec le bouton droit sur l’événement, puis cliquez sur **Basculer le point d’arrêt**.  
  
     Une puce rouge apparaît en regard de l'événement de trace sélectionné, indiquant qu'il s'agit du point d'arrêt.  
  
     Répétez cette étape pour définir plusieurs points d'arrêt.  
  
3.  Dans le menu **Relire** , cliquez sur **Démarrer**, puis connectez-vous au serveur sur lequel vous souhaitez relire la trace.  
  
4.  Dans la boîte de dialogue **Configuration de la relecture** , vérifiez les paramètres, puis cliquez sur **OK**.  
  
     La relecture démarre pour s'interrompre une fois le point d'arrêt atteint.  
  
5.  Appuyez sur F5 pour reprendre la relecture jusqu'au point d'arrêt suivant.  
  
6.  Répétez l'étape 5 jusqu'à la fin de la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Relire jusqu’à un curseur &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)   
 [Relire des traces](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
