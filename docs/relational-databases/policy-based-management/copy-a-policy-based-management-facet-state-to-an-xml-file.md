---
title: Copier un état de facette de gestion basée sur des stratégies dans un fichier XML | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c0e3d197f8cb6b7b5bd05ed037fd32e938b5ad4f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68109736"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Copier un état de facette de gestion basée sur des stratégies dans un fichier XML
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment copier l'état d'une facette de gestion basée sur des stratégies dans un fichier XML dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour copier un état de facette dans un fichier XML à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les procédures de cette rubrique nécessite l’appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>Pour copier un état de facette dans un fichier XML  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un objet d’instance, une base de données ou un objet de base de données, puis cliquez sur **Facettes**.  
  
2.  Dans la boîte de dialogue **Afficher les facettes -** _nom_objet_, cliquez sur **Exporter l’état actuel en tant que stratégie**.  
  
3.  Dans la boîte de dialogue **Exporter en tant que stratégie** , tapez le nom et le chemin du fichier ou utilisez le bouton Parcourir ( **...** ) pour rechercher le fichier, puis tapez le nom du fichier XML. Pour plus d'informations sur les options disponibles dans cette boîte de dialogue, consultez [Export As Policy Dialog Box](../../relational-databases/policy-based-management/export-as-policy-dialog-box.md).  
  
4.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
