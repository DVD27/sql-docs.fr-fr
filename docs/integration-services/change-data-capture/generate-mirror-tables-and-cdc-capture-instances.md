---
title: Générer des tables miroir et des instances de capture CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: dbefe9209072ec6e68e393bcef6f56360e6afe58
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68011377"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a>Générer des tables miroir et des instances de capture de données modifiées

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Utiliser la page Générer des tables miroir pour générer les tables miroir des tables incluses dans l'instance de capture de données modifiées  
  
 Cliquez sur **Exécuter** pour créer les tables miroir. La progression de la création de chaque table s'affiche, ainsi qu'un message pour vous indiquer si chaque table miroir s'est terminée correctement ou avec des erreurs. Si des erreurs se produisent, cliquez sur **Détails** pour afficher la boîte de dialogue contenant une explication de l'erreur.  
  
 En cas d'échec de la création de l'une des tables, vous pouvez choisir de continuer ou de supprimer toutes les tables ayant échoué avant de continuer. Une fois l'exécution de l'Assistant terminée, vous pouvez décider de corriger la table dans la base de données source Oracle ou de ne pas l'utiliser dans l'instance de capture de données modifiées. Si vous corrigez la table, vous pouvez l'ajouter lorsque vous [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
 Cliquez sur **Suivant** pour ouvrir la page [Finish](../../integration-services/change-data-capture/finish.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer l’instance de base de données de modifications SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)  
  
  
