---
title: Appliquer une Transformation XSL (fournisseur SQLXMLOLEDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8c9d73330063cf3f051695c5fd25c689bb6c4c10
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061400"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a>Application d'une transformation XSL (fournisseur SQLXMLOLEDB)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Dans cet exemple d'application ADO, une requête SQL est exécutée et le langage XSLT est appliqué au résultat. La définition de la propriété ClientSideXML sur True applique le traitement de l’ensemble de lignes du côté client. Le dialecte de commande a pour valeur {5d531cb2-e6ed-11d2-b252-00c04f681b71} car la requête SQL est spécifiée dans un modèle et que ce dialecte doit être spécifié lors de l'exécution d'un modèle. La propriété xsl Spécifie le fichier XSL à utiliser pour appliquer la transformation. La valeur de propriété de chemin d’accès de Base est utilisée pour rechercher le fichier XSL. Si vous spécifiez un chemin d’accès dans la valeur de la propriété xsl, le chemin d’accès est relatif le chemin d’accès qui est spécifié dans la propriété de chemin d’accès de Base.  
  
 Cet exemple indique comment utiliser les propriétés suivantes spécifiques au fournisseur SQLXMLOLEDB :  
  
-   ClientSideXML  
  
-   xsl  
  
 Dans cet exemple d'application ADO côté client, un modèle XML contenant une requête SQL est exécuté sur le serveur.  
  
 Étant donné que la propriété ClientSideXML est définie sur True, l’instruction SELECT sans la clause FOR XML est envoyée au serveur. Le serveur exécute la requête et retourne un ensemble de lignes au client. Le client applique ensuite la transformation FOR XML à l'ensemble de lignes et génère le document XML.  
  
 La propriété xsl est spécifiée dans l’application ; Par conséquent, la transformation XSL est appliquée au document XML qui est généré sur le client et le résultat est un tableau à deux colonnes.  
  
 Pour exécuter la commande de modèle, le dialecte de modèle XML - {5d531cb2-e6ed-11d2-b252-00c04f681b71} - doit être spécifié.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion. En outre, cet exemple spécifie l'utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client comme fournisseur de données, ce qui requiert l'installation d'un logiciel client réseau supplémentaire. Pour plus d’informations, consultez [configuration système requise pour SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 Le modèle XSL suit. Le résultat de l'application de ce modèle XSL est une table à deux colonnes.  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  
