---
title: Extensions Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b671200dce3b5be1e01e40b09ff285563c4d4f6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62985776"
---
# <a name="reporting-services-extensions"></a>Extensions Reporting Services
  L'architecture modulaire de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est conçue à des fins d'extensibilité. Une API de code managé est disponible afin de vous permettre de développer, installer et gérer facilement des extensions consommées par de nombreux composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Vous pouvez créer des assemblys privés ou partagés à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] l’aide de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] l’et ajouter de nouvelles fonctionnalités pour répondre à vos besoins en constante évolution de l’entreprise.  
  
 L'architecture d'extensibilité unique de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] permet aux développeurs d'étendre des fonctionnalités spécifiques du produit et de ses composants. Il existe actuellement une prise en charge générale pour étendre les fonctions de traitement de données de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. L'API de traitement de données comprend des constructions et des conventions du fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] couramment utilisées, qui permettent aux développeurs d'ajouter des fonctions de traitement de données supplémentaires à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Ces extensions pour le traitement des données ajoutent des fonctionnalités au serveur de rapports et au Concepteur de rapports, ce qui se traduit par une intégration transparente des données personnalisées aux rapports.  
  
 Une autre extension prise en charge est l'extension de remise. L'API de remise est entièrement intégrée à l'architecture [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], ce qui permet d'utiliser une grande variété de mécanismes de remise lors de l'envoi de notifications de rapport aux utilisateurs. Vous pouvez étendre le serveur de rapports pour fournir une remise personnalisée aux utilisateurs et vous pouvez étendre les pages de gestion d'abonnement du Gestionnaire de rapports pour prendre en charge les abonnements qui utilisent des extensions de remise personnalisées.  
  
 Une autre extension du serveur de rapports, RDCE (Report Definition Customization Extension), peut personnaliser dynamiquement une définition de rapport avant que celle-ci ne soit passée au moteur de traitement. Vous pouvez personnaliser des rapports en fonction de facteurs tels que des utilisateurs ou des langues. Par exemple, vous pouvez implémenter des vues adaptées à différents utilisateurs, tels que des responsables ou des membres d'un service, ou vous pouvez personnaliser un rapport pour générer une disposition différente selon qu'il est rendu en français ou en arabe.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Considérations sur la sécurité pour les extensions](security-considerations-for-extensions.md)  
 Décrit les problèmes de sécurité relatifs au développement et au déploiement d'extensions [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implémentation d'une extension pour le traitement des données](data-processing/implementing-a-data-processing-extension.md)  
 Décrit les spécifications et les étapes relatives à l'implémentation d'une extension pour le traitement des données pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implémentation d'une extension de remise](delivery-extension/implementing-a-delivery-extension.md)  
 Décrit les spécifications et les étapes relatives à l'implémentation d'une extension de remise pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implémentation d'une extension de rendu](rendering-extension/implementing-a-rendering-extension.md)  
 Contient une introduction au développement d'extensions de rendu.  
  
 [Implémentation d'une extension de sécurité](security-extension/implementing-a-security-extension.md)  
 Décrit les spécifications et les étapes relatives à l'implémentation d'une extension de sécurité [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Bibliothèque d'extensions Reporting Services](reporting-services-extension-library.md)  
 Contient la référence de programmation pour la bibliothèque API d'extension pour les fonctionnalités d'extensibilité de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
  
