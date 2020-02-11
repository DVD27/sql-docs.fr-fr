---
title: Propriétés de Report Server (onglet Service) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2a2e1dbf-02b9-4893-aaf0-c0e4a2c9b4f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef0f55049e5ae9c96eed10fb1f39d7f3d95a19f9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62506770"
---
# <a name="report-server-properties-service-tab"></a>Propriétés de Report Server (onglet Service)
  Ce service est le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service Report Server. Les valeurs des propriétés en gris clair ne peuvent pas être modifiées à l'aide de cette application.  
  
## <a name="options"></a>Options  
 **Chemin d’accès binaire**  
 Affiche l'emplacement des fichiers programme utilisés par ce service.  
  
 **Contrôle d’erreur**  
 1 indique « SERVICE_ERROR_NORMAL ». Si le lancement du service échoue pendant le démarrage de l'ordinateur, le programme de démarrage consigne l'erreur et affiche une boîte de message, mais poursuit l'opération de démarrage. Cette valeur ne peut pas être modifiée.  
  
 **Code de sortie**  
 Lorsqu'une erreur se produit, le numéro d'erreur apparaît dans cette zone. Pour dépanner des incidents, recherchez ce numéro dans la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou communiquez-le au personnel en charge du support technique.  
  
 **Nom d’hôte**  
 Affiche le nom de l'ordinateur ou du cluster exécutant la recherche en texte intégral.  
  
 **Nom**  
 Indique le nom d'affichage du service.  
  
 **ID du processus**  
 Affiche l'ID de processus [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Type de service SQL**  
 Type de service fourni aux processus appelants. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installe plusieurs services.  
  
 **Mode de démarrage**  
 Les options disponibles pour ce service sont les suivantes :  
  
-   Manuel : ce service n'est pas automatiquement lancé au démarrage de l'ordinateur. Vous devez démarrer le service à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'un autre outil.  
  
-   Automatique : ce service essaie de se lancer au démarrage de cet ordinateur.  
  
-   Désactivé : ce service ne peut pas être démarré.  
  
 **State**  
 Indique si ce service est en cours d'exécution, arrêté ou désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Services SQL Server](../../../2014/tools/configuration-manager/sql-server-services.md)  
  
  
