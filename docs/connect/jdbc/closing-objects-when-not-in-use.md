---
title: Fermeture d’objets lorsqu’ils ne sont pas utilisés | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2a9539599848f86a84cd03838c1fa7412c24fb1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957305"
---
# <a name="closing-objects-when-not-in-use"></a>Fermeture d'objets inutilisés
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lorsque vous utilisez les objets de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], en particulier [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) ou l’un des objets Statement, par exemple [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) ou [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), fermez-les explicitement à l’aide de leurs méthodes close lorsqu’ils ne sont plus nécessaires. Cela améliore les performances en libérant les ressources de pilote et de serveur le plus tôt possible, au lieu d'attendre que le garbage collector de la machine virtuelle Java ne le fasse pour vous.  
  
 La fermeture des objets est particulièrement importante pour conserver un bon accès simultané sur le serveur lorsque vous utilisez des arrêts de défilement. Les arrêts de défilement dans la dernière mémoire tampon d'extraction accédée sont maintenus jusqu'à la fermeture du jeu de résultats. De même, les handles préparés par instruction sont maintenus jusqu'à ce que l'instruction soit fermée. Si vous réutilisez une connexion pour plusieurs instructions, le fait de fermer les instructions avant de leur permettre de sortir de portée permettra au serveur de nettoyer plus tôt les handles préparés.  
  
## <a name="see-also"></a>Voir aussi  
 [Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
