---
title: Types définis par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ce45cb7fb76c1b01b57d96d86e34b051dc73043
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80916945"
---
# <a name="user-defined-types"></a>Types définis par l'utilisateur

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les types définis par l’utilisateur (UDT) ont été introduits dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] pour permettre au développeur d’étendre le système de type scalaire du serveur en stockant des objets CLR (Common Language Runtime) dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les UDT peuvent contenir plusieurs éléments et avoir des comportements, contrairement aux types de données alias traditionnels qui ne comprennent qu’un seul type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Auparavant, les UDT étaient limités à une taille maximale de 8 kilo-octets. Dans [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)], les UDT supérieurs à 64 kilo-octets sont à présent pris en charge. La version 3.0 du pilote JDBC prend à présent également en charge les UDT supérieurs à 64 kilo-octets lorsque vous spécifiez le format UserDefined.

Il n'existe aucune modification du comportement pour les types définis par l'utilisateur (UDT) dont la taille est inférieure ou égale à 8 000 octets, mais les types définis par l'utilisateur plus volumineux sont pris en charge et affichent une taille « illimitée ».

## <a name="see-also"></a>Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
