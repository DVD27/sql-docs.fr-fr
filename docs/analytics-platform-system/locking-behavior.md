---
title: Comportement de verrouillage - Parallel Data Warehouse | Microsoft Docs
description: Découvrez comment Parallel Data Warehouse utilise le verrouillage pour garantir l’intégrité des transactions et de maintenir la cohérence des bases de données lorsque plusieurs utilisateurs accèdent aux données en même temps.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d93743c83d6315e6ab9484445f344b06f80be845
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960643"
---
# <a name="locking-behavior-in-parallel-data-warehouse"></a>Comportement de verrouillage dans Parallel Data Warehouse
Découvrez comment Parallel Data Warehouse utilise le verrouillage pour garantir l’intégrité des transactions et de maintenir la cohérence des bases de données lorsque plusieurs utilisateurs accèdent aux données en même temps.  
  
## <a name="Basics"></a>Principes fondamentaux de verrouillage  
**Modes**  
  
SQL Server PDW prend en charge quatre modes de verrouillage :  
  
Exclusive  
Le verrou exclusif interdit l’écriture ou de lecture à partir de l’objet verrouillé jusqu'à ce que la transaction détenant que le verrou exclusif se termine. Aucuns verrous de n’importe quel mode ne sont autorisées pendant que le verrou exclusif est en vigueur. Par exemple, DROP TABLE et CREATE DATABASE utilisent un verrou exclusif.  
  
Partagés  
Le verrou partagé empêche l’émission d’un verrou exclusif sur l’objet affecté, mais permet à tous les autres modes de verrouillage. Par exemple, l’instruction SELECT lance un verrou partagé et par conséquent permet plusieurs requêtes accéder aux données sélectionnées simultanément, mais empêche les mises à jour les enregistrements lors de la lecture jusqu'à la fin de l’instruction SELECT.  
  
ExclusiveUpdate  
Le verrou ExclusiveUpdate interdit l’écriture dans l’objet verrouillé, mais n’autorise pas la lecture par le biais du verrou partagé. Aucun autre verrou n’est autorisées pendant que le verrou ExclusiveUpdate est en vigueur. Par exemple, la base de données de sauvegarde et de restaurer la base de données utilisent un verrou de mise à jour Exclusive.  
  
SharedUpdate  
Le verrou SharedUpdate interdit les modes de verrouillage exclusif et ExclusiveUpdate et permet des modes de verrouillage partagé et SharedUpdate sur l’objet. SharedUpdate modifie un objet, mais ne restreint pas l’accès en lecture à celui-ci lors de la modification. Par exemple, insérer et mise à jour utiliser un verrou SharedUpdate.  
  
**Classes de ressources**  
  
Verrous sont maintenus sur les classes d’objets suivantes : Base de données, schéma, objet (table, vue ou procédure), APPLICATION (utilisé en interne), EXTERNALDATASOURCE, EXTERNALFILEFORMAT et SCHEMARESOLUTION (une base de données au niveau lock effectuée lors de la création, modification ou suppression des objets de schéma ou les utilisateurs de base de données). Ces classes d’objets peuvent apparaître dans la colonne object_type de [sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md).  
  
## <a name="Remarks"></a>Remarques d’ordre général  
Les verrous sont applicables aux bases de données, des tables ou des vues.  
  
SQL Server PDW n’implémente pas tous les niveaux d’isolation configurables. Il prend en charge le niveau d’isolement READ_UNCOMMITTED tel que défini par la norme ANSI. Toutefois, depuis la lecture d’opérations sont exécutées sous READ_UNCOMMITTED, très peu d’opérations bloquantes réellement se produire ou entraîner des conflits dans le système.  
  
SQL Server PDW s’appuie sur le moteur SQL Server sous-jacent pour implémenter le contrôle d’accès concurrentiel et de verrouillage. Si les opérations provoquer un blocage de SQL Server sous-jacent dans le même nœud, SQL Server PDW tire parti de la capacité de détection de blocage de SQL Server et met fin à une des instructions de blocage.  
  
> [!NOTE]  
> SQL Server n’autorise pas les instructions qui sont en attente de verrous soient bloquées par des demandes de verrou plus récentes. SQL Server PDW n’a pas entièrement implémentée ce processus. Dans SQL Server PDW, les demandes continues de nouveaux verrous partagés peuvent parfois bloquer une demande précédente (mais en attente) pour un verrou exclusif. Par exemple, un **mise à jour** instruction (ce qui nécessite un verrou exclusif) peut être bloquée par des verrous partagés sont accordées pour la série de **sélectionnez** instructions. Pour résoudre un processus bloqué (identifiables par le [sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md) DVM), arrêter l’envoi de demandes de nouveau jusqu'à ce que le verrou exclusif a été satisfait.  
  
## <a name="lock-definition-table"></a>Tableau de définition de verrou  
SQL Server prend en charge les types suivants de verrous. Pas tous les types de verrou sont disponibles sur le nœud de contrôle, mais peuvent se produire sur les nœuds de calcul.  
  
-   SCH-S (stabilité du schéma). Garantit que l'élément d'un schéma, tel qu'une table ou un index, n'est pas supprimé alors qu'une session contient un verrou de stabilité du schéma sur l'élément du schéma.  
  
-   SCH-M (modification du schéma). Doit être détenu par toute session destinée à modifier le schéma de la ressource spécifiée. Garantit qu'aucune autre session ne fait référence à l'objet indiqué.  
  
-   S (partagé). La session détenant le verrou peut disposer d'un accès partagé à la ressource.  
  
-   U (mise à jour). Indique qu'un verrouillage de mise à jour a été posé sur des ressources qui peuvent finalement être mises à jour. Utilisé pour empêcher l'occurrence d'une forme de blocage courante qui apparaît lorsque plusieurs sessions verrouillent les ressources pour une mise à jour potentielle ultérieure.  
  
-   X (exclusif). La session détenant le verrou peut disposer d'un accès exclusif à la ressource.  
  
-   EST (Intent partagé). Indique l'intention de placer des verrous S sur certaines ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   IU (mise à jour intentionnelle). Indique l'intention de placer des verrous U sur certaines ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   IX (Intent exclusif). Indique l'intention de placer des verrous X sur certaines ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   SIU (partagé mise à jour intentionnelle). Signale des accès partagés à une ressource dans le but de poser des verrous de mise à jour sur les ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   SIX (partage intentionnel exclusif). Signale des accès partagés à une ressource dans le but de poser des verrous exclusifs sur les ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   UIX (mise à jour intentionnelle Exclusive). Signale un verrou de mise à jour sur une ressource dans le but de poser des verrous exclusifs sur les ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   BU. Utilisé par les opérations en bloc.  
  
-   RangeS_S (verrou d’étendue de clés partagés et de ressources partagées). Indique une analyse de plage sérialisable.  
  
-   RangeS_U (verrou d’étendue de clés partagés et les ressources de mise à jour). Indique une analyse de mise à jour sérialisable.  
  
-   RangeI_N (verrou insérer des clés et de ressources Null). Utilisé pour tester les étendues avant l'insertion d'une nouvelle clé dans un index.  
  
-   RangeI_S. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et S.  
  
-   RangeI_U. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et U.  
  
-   RangeI_X. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et X.  
  
-   RangeX_S. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et RangeS_S.  
  
-   RangeX_U. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et RangeS_U.  
  
-   RangeX_X (verrou de clés exclusifs et de ressources exclusives). Verrou de conversion utilisé lors de la mise à jour d'une clé dans une étendue.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
