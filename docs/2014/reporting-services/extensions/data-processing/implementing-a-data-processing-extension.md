---
title: IMise en œuvre d’une extension pour le traitement des données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2efc74fa2ba84335fcb5e03b42125fb9c6782f43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164118"
---
# <a name="implementing-a-data-processing-extension"></a>Implémentation d'une extension pour le traitement des données
  Les extensions pour le traitement des données dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] vous permettent de vous connecter à une source de données et de récupérer des données. Elles servent également de pont entre une source de données et un dataset [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]les extensions pour le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] traitement des données sont modélisées après un sous-ensemble des interfaces de fournisseur de données.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble des extensions pour le traitement des données](data-processing-extensions-overview.md)  
 Explique comment écrire une extension personnalisée pour le traitement des données pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Préparation à l'implémentation d'une extension pour le traitement des données](preparing-to-implement-a-data-processing-extension.md)  
 Décrit les interfaces disponibles pour l'implémentation d'une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ainsi que l'implémentation d'une interface particulière.  
  
 [Création d'une bibliothèque d'extensions pour le traitement des données](creating-a-data-processing-extension-library.md)  
 Décrit l'assignation d'un espace de noms pour votre extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et la compilation de votre extension pour le traitement des données dans une DLL de bibliothèque.  
  
 [Implémentation d'une classe Connection pour une extension pour le traitement des données](implementing-a-connection-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’une connexion et comment implémenter votre propre classe **Connection** pour votre extension pour le traitement des données.  
  
 [Implémentation d'une classe Command pour une extension pour le traitement des données](implementing-a-command-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’une commande et comment implémenter votre propre classe **Command** pour votre extension pour le traitement des données.  
  
 [Implémentation d'une classe DataReader pour une extension pour le traitement des données](implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Décrit les attributs d’un lecteur de données et comment implémenter votre propre classe **DataReader** pour votre extension pour le traitement des données.  
  
 [Utilisation d'un dataset externe avec Reporting Services](using-an-external-dataset-with-reporting-services.md)  
 Décrit comment exposer vos objets **DataSet** personnalisés sur le serveur de rapports pour être exploité.  
  
 [Déploiement d'une extension pour le traitement des données](deploying-a-data-processing-extension.md)  
 Décrit comment déployer votre extension pour le traitement des données.  
  
 [Débogage du code des extensions pour le traitement des données](debugging-data-processing-extension-code.md)  
 Décrit comment déboguer le code dans vos extensions pour le traitement des données.  
  
 [Suppression d'une extension pour le traitement des données](removing-a-data-processing-extension.md)  
 Décrit comment supprimer une extension pour le traitement des données d'un serveur de rapports ou d'un Concepteur de rapports.  
  
 Pour un exemple d’extension pour le traitement des données totalement implémentée, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../reporting-services-extensions.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
