---
title: Connexion à Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6d605a5ed646df46e90440780a08e32ae82ad390
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68099772"
---
# <a name="connect-to-oracle"></a>Connexion à Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Lorsque vous ajoutez ou modifiez les tables utilisées dans l'instance de capture de données modifiées pour la première fois, vous pouvez être invité à vous connecter à la base de données Oracle. Vous devez entrer les informations d'identification d'un utilisateur Oracle qui a accès au schéma des tables à capturer. Entrez les informations suivantes dans cette boîte de dialogue :  
  
 **Authentification**  
  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows** : sélectionnez cette option pour utiliser les informations d’identification actuelles de domaine Windows. Vous ne pouvez utiliser cette option que si la base de données Oracle est configurée pour utiliser l'authentification Windows.  
  
-   **Authentification Oracle** : si vous sélectionnez cette option, vous devez taper le **Nom d’utilisateur** et le **Mot de passe** de l’utilisateur dans la base de données Oracle à laquelle vous vous connectez.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des tables à une instance de capture de données modifiées](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  
