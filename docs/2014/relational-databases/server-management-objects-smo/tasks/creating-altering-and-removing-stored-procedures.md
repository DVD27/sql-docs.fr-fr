---
title: Création, modification et suppression de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc38e4f11b32c368626b0f84a352d3f9c00fa0f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211900"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>Création, modification et suppression des procédures stockées
  Dans SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects), les procédures stockées sont représentées par l'objet <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>.  
  
 La création d'un objet <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> dans SMO requiert la définition de la propriété <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> sur le script [!INCLUDE[tsql](../../../includes/tsql-md.md)] qui définit la procédure stockée. Paramètres requièrent le \@ doivent être créés individuellement à l’aide et utilisez le préfixe <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> objets et en ajoutant à la <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> collection de la <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> objet.  
  
## <a name="example"></a>Exemple  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) ou [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a>Création, modification et suppression d'une procédure stockée en Visual Basic  
 Cet exemple de code montre comment créer une procédure stockée pour la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . L'exemple retourne le nom d'un employé lorsque le numéro d'ID d'employé est fourni. La procédure stockée requiert un paramètre d'entrée pour spécifier le numéro d'ID d'employé et un paramètre de sortie pour retourner le nom de l'employé.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a>Création, modification et suppression d'une procédure stockée en Visual C#  
 Cet exemple de code montre comment créer une procédure stockée pour la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . L'exemple retourne le nom d'un employé lorsque le numéro d'ID d'employé est fourni (`BusinessEntityID`). La procédure stockée requiert un paramètre d'entrée pour spécifier le numéro d'ID d'employé et un paramètre de sortie pour retourner le nom de l'employé.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a>Création, modification et suppression d'une procédure stockée dans PowerShell  
 Cet exemple de code montre comment créer une procédure stockée pour la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . L'exemple retourne le nom d'un employé lorsque le numéro d'ID d'employé est fourni (`BusinessEntityID`). La procédure stockée requiert un paramètre d'entrée pour spécifier le numéro d'ID d'employé et un paramètre de sortie pour retourner le nom de l'employé.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
$sp  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure `  
-argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.   
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.   
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.   
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.   
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.   
$sp.Drop()  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
  
  
