---
title: Fichiers et numéros de Version | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7936eaf327f9df3cb0f3d8545d7bf557ef1471ac
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098037"
---
# <a name="files-and-version-numbers"></a>Fichiers et numéros de version
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Requis tous les composants de SQL Server Management Object (SMO) sont inclus dans le package NuGet de Microsoft.SqlServer.SqlManagementObjects. SMO est implémenté dans plusieurs assemblys managés. Vous pouvez développer des applications SMO sur un client ou sur un serveur.  

> > [!Important]
> > La version de fichier des assemblys SMO est affichée comme majeures. **0**. Build.Revision. Mais la version d’assembly incorporé est majeure. **100**. Build.Revision. Pour cela, vous permettant de séparer la version de SMO utilisée dans chaque application afin de mises à jour à un n’affecte pas les autres.
> > 
> > Pour cette raison, vous devez **pas** installer ces versions des assemblys au Global Assembly Cache (GAC). Cela peut entraîner des autres applications, telles que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio, pour arrêter l’exécution. 
  
|Fichier|Description|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|Assure la prise en charge de la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|Assure la prise en charge de la programmation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Celle-ci n'est requise que dans les programmes qui accèdent au Service Broker.|  
|Microsoft.SqlServer.Smo.dll|Contient la plupart des classes SMO.|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Assure la prise en charge des classes SMO.|  
|Microsoft.SqlServer.WmiEnum.dll|Contient les classes du fournisseur WMI (Windows Management Instrumentation). Celles-ci sont uniquement requises pour les programmes qui utilisent les classes du fournisseur WMI.|  
|Microsoft.SqlServer.RegSvrEnum.dll|Contient les classes de serveurs inscrits. Celles-ci sont uniquement requises pour les programmes qui utilisent les classes de serveurs inscrits.|  
  
  
