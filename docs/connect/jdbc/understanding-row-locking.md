---
title: Présentation du verrouillage de ligne | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2f7887768d7155ab2f7ff2b0a12c1b713bddced
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920306"
---
# <a name="understanding-row-locking"></a>Présentation du verrouillage de ligne

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilise des verrous de ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces verrous implémentent les contrôles de concurrence entre plusieurs utilisateurs qui effectuent simultanément des modifications dans une base de données. Par défaut, les transactions et verrous sont gérés sur la base de chaque connexion. Par exemple, si une application ouvre deux connexions JDBC, les verrous acquis par une connexion ne peuvent pas être partagés avec l'autre connexion. Aucune connexion ne peut acquérir des verrous qui seraient en conflit avec les verrous détenus par l'autre connexion.

> [!NOTE]  
> Si le verrouillage de ligne est utilisé, toutes les lignes dans la mémoire tampon d'extraction sont verrouillées ; par conséquent, un très grand paramètre pour la taille d'extraction peut affecter la concurrence.

Le verrouillage est utilisé pour garantir l'intégrité transactionnelle et la cohérence de base de données. Le verrouillage empêche les utilisateurs de lire des données qui sont en cours de modification par d'autres utilisateurs et empêche plusieurs utilisateurs de modifier simultanément les mêmes données. Si le verrouillage n'est pas utilisé, les données dans la base de données peuvent devenir logiquement incorrectes et les requêtes exécutées contre ces données peuvent produire des résultats inattendus.

> [!NOTE]  
> Pour plus d’informations sur le verrouillage de ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez la rubrique « Verrouillage du [!INCLUDE[ssDE](../../includes/ssde_md.md)] » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a>Voir aussi

[Gestion des jeux de résultats avec le pilote JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)
