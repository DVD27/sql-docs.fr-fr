---
title: Exécuter Windows PowerShell à partir de SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 239a031c64a8f195a5731d9ff9930b9b0d345034
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049095"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>Exécuter Windows PowerShell à partir de SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Vous pouvez démarrer des sessions Windows PowerShell à partir de l' **Explorateur d'objets** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] lance Windows PowerShell, charge le module **SqlServer** et affecte au contexte de chemin le nœud associé dans l’arborescence de **l’Explorateur d’objets**.  
  

> [!NOTE]
> Il existe deux modules SQL Server PowerShell : **SqlServer** et **SQLPS**. Le module **SQLPS** fait partie de l’installation de SQL Server (à des fins de compatibilité descendante), mais il n’est plus mis à jour. Le module PowerShell le plus récent est **SqlServer**. Le module **SqlServer** contient les versions mises à jour des applets de commande disponibles dans **SQLPS**, ainsi que de nouvelles applets de commande pour prendre en charge les dernières fonctionnalités SQL.  
> Des versions précédentes du module **SqlServer** *étaient* fournies avec SQL Server Management Studio (SSMS), mais uniquement avec les versions 16.x de SSMS. Pour utiliser PowerShell avec SSMS 17.0 et ultérieur, vous devez installer le module **SqlServer** à partir de PowerShell Gallery.
> Pour installer le module **SqlServer**, consultez [Installer SQL Server PowerShell](download-sql-server-ps-module.md).



Quand vous spécifiez l’exécution de PowerShell pour un objet dans l’ **Explorateur d’objets**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] démarre une session Windows PowerShell dans laquelle les composants logiciels enfichables [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell ont été chargés et inscrits. Le chemin de la session est prédéfini avec l’emplacement de l’objet sur lequel vous avez cliqué avec le bouton droit dans l’Explorateur d’objets. Par exemple, si vous cliquez avec le bouton droit sur l’objet de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] dans l’Explorateur d’objets et que vous sélectionnez **Démarrer PowerShell**, le chemin Windows PowerShell est défini comme suit :  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="run-powershell"></a>Exécuter PowerShell  
 **Pour exécuter PowerShell à partir de SQL Server Management Studio**  
  
1.  Ouvrez l' **Explorateur d'objets**.  
  
2.  Accédez au nœud de l'objet à utiliser.  
  
3.  Cliquez avec le bouton droit sur l’objet et sélectionnez **Démarrer PowerShell**.  
  
## <a name="permissions"></a>Autorisations  
 S’il a été ouvert à partir de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], PowerShell ne fonctionne pas avec les privilèges d’administrateur, ce qui peut bloquer certaines activités comme les appels à WMI.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
