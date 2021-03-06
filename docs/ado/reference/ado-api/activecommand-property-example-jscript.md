---
title: ActiveCommand, propriété-Exemple (JScript) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- ActiveCommand property [ADO], JScript example
ms.assetid: be09e2af-ba31-4168-8ccd-2461bb24e49a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ad96904c913cadc451bc7d4c67fb5e4f8c59c70
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67921660"
---
# <a name="activecommand-property-example-jscript"></a>ActiveCommand, exemple de propriété (JScript)
Cet exemple montre la [ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md) propriété. Coupez et collez le code suivant dans le bloc-notes ou un autre éditeur de texte et enregistrez-le en tant que **ActiveCommandJS.asp**.  
  
```  
<!-- BeginActiveCommandJS -->  
<%@LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<%  
    // user input  
    strName = new String(Request.Form("ContactName"))  
%>  
  
<html>  
  
<head>  
<title>ActiveCommand Property Example (JScript)</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
-->  
</style>  
</head>  
  
<body bgcolor="White">  
  
<h1>ActiveCommand Property Example (JScript)</h1>  
  
<%  
if (strName.length > 0)  
    {  
        // connection and recordset variables  
        var Cnxn = Server.CreateObject("ADODB.Connection")  
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
        var cmdContact = Server.CreateObject("ADODB.Command");  
        var rsContact = Server.CreateObject("ADODB.Recordset");  
        // display variables  
        var strMessage;  
  
        try  
        {  
            // open connection  
            Cnxn.Open(strCnxn);  
  
            // Open a recordset using a command object  
            cmdContact.CommandText = "SELECT ContactName FROM Customers WHERE City = ?";  
            cmdContact.ActiveConnection = Cnxn;  
            // create parameter and insert variable value  
            cmdContact.Parameters.Append(cmdContact.CreateParameter("ContactName", adChar, adParamInput, 30, strName));  
  
            rsContact = cmdContact.Execute();  
  
            while(!rsContact.EOF){  
                // start new line  
                strMessage = "<P>";  
  
                // get data  
                strMessage += rsContact("ContactName")  
  
                // end the line  
                strMessage += "</P>";  
  
                // show data  
                Response.Write(strMessage);  
  
                // get next record  
                rsContact.MoveNext;  
            }  
        }  
        catch (e)  
        {  
            Response.Write(e.message);  
        }  
        finally  
        {  
            // 'clean up  
            if (rsContact.State == adStateOpen)  
                rsContact.Close;  
            if (Cnxn.State == adStateOpen)  
                Cnxn.Close;  
            rsContact = null;  
            Cnxn = null;  
        }  
    }  
%>  
  
<hr>  
  
<form method="POST" action="ActiveCommandJS.asp">  
  <p align="left">Enter city of customer to find (e.g., Paris): <input type="text" name="ContactName" size="40" value=""></p>  
  <p align="left"><input type="submit" value="Submit" name="B1"><input type="reset" value="Reset" name="B2"></p>  
</form>  
</body>  
  
</html>  
<!-- EndActiveCommandJS -->  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveCommand, propriété (ADO)](../../../ado/reference/ado-api/activecommand-property-ado.md)   
 [Objet Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
