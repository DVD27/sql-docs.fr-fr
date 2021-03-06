---
title: Supprimer une instance de SQL Server de l’utilitaire SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.utility.remove.f1
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 49459743e2eb8af64b1c41910c660f713dbdb2a5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63035943"
---
# <a name="remove-an-instance-of-sql-server-from-the-sql-server-utility"></a>Supprimer une instance de SQL Server de l'utilitaire SQL Server
  Suivez la procédure suivante pour supprimer une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette procédure supprime l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du mode Liste de l’UCP et interrompt la collecte de données de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas désinstallée.  
  
> [!IMPORTANT]  
>  Avant d'utiliser cette procédure pour supprimer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , assurez-vous que les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Agent SQL Server s'exécutent sur l'instance à supprimer.  
  
1.  Depuis l’Explorateur de l’utilitaire dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **Instances gérées**. Observez le mode Liste des instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le volet de contenu de l’Explorateur de l’utilitaire.  
  
2.  Dans la colonne **Nom de l’instance SQL Server** du mode Liste, sélectionnez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à supprimer de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cliquez avec le bouton droit sur l’instance à supprimer et sélectionnez **Supprimer une instance gérée…** .  
  
3.  Spécifiez les informations d’identification avec des privilèges d’administrateur pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: Cliquez sur **connecter...** , vérifiez les informations contenues dans le **se connecter au serveur** boîte de dialogue zone, puis cliquez sur **Connect**. Les informations de connexion s’affichent sur le dialogue **Supprimer une instance gérée** .  
  
4.  Cliquez sur **OK**pour confirmer l’opération. Pour quitter l’installation, cliquez sur **Annuler**.  
  
## <a name="manually-remove-a-managed-instance-of-sql-server-from-a-sql-server-utility"></a>Supprimer manuellement une instance gérée de SQL Server d'un utilitaire SQL Server  
 Cette procédure supprime l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du mode Liste de l’UCP et interrompt la collecte de données de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas désinstallée.  
  
 Pour utiliser PowerShell pour supprimer une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ce script effectue les opérations suivantes :  
  
-   obtient l'UCP par le nom de l'instance du serveur ;  
  
-   supprime l’instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
 Notez qu'il est important de désigner l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par son nom exact, tel qu'il est enregistré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui respecte la casse, vous devez spécifier le nom de l’instance en respectant la casse exacte, telle qu’elle est retournée par @@SERVERNAME. Pour obtenir le nom de l'instance pour l'instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], exécutez la requête suivante sur l'instance gérée :  
  
```  
select @@SERVERNAME AS instance_name  
```  
  
 À ce stade, l’instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est complètement supprimée de l’UCP. Elle disparaît du mode Liste lorsque vous actualisez les données de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le résultat est identique à celui qu'obtient un utilisateur qui effectue avec succès l'opération de suppression d'instance gérée dans l'interface utilisateur SSMS.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser l'Explorateur de l'utilitaire pour gérer l'Utilitaire SQL Server](use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Résolution des problèmes liés à l'utilitaire SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
