---
title: Méthodes de traitement par lot | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b7ec19101b1abcb2e0fb825923cce7a237149dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63020133"
---
# <a name="batching-methods"></a>Méthodes de traitement par lot
  L'utilisation d'en-têtes SOAP dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vous permet d'inclure plusieurs méthodes Web Service dans une même opération. Les méthodes sont exécutées dans la portée d'une transaction de base de données unique, dans l'ordre de leur appel.  
  
 La restauration est un avantage offert par l'utilisation de plusieurs méthodes de traitements par lots. En cas d'erreur sur un appel de méthode au cours de l'exécution d'un lot, le serveur de rapports arrête l'exécution du lot et restaure les opérations précédentes. Cette opération est utile lorsqu'un appel de méthode dépend de l'achèvement réussi d'autres appels de méthode dans ce lot.  
  
 Le service Web ne fournit pas de sémantique de verrouillage pour les traitements par lots de plusieurs méthodes. Les lignes dans la base de données du serveur de rapports ne sont pas verrouillées pour la mise à jour tant que le message n'a pas été envoyé au serveur et la commande Execute appelée.  
  
 Il n'y a pas non plus de contrôles concurrentiels pour garantir que la base de données n'a pas changé depuis la dernière lecture des données. Si deux clients modifient le même élément, la dernière mise à jour réussit si les paramètres sont encore valides (par exemple, l'élément n'a pas été renommé).  
  
 L'exemple suivant appelle la méthode <xref:ReportService2005.ReportingService2005.CreateFolder%2A> trois fois et exécute ces appels comme un lot unique. Si un des appels à <xref:ReportService2005.ReportingService2005.CreateFolder%2A> échoue, le lot entier est annulé.  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 [Informations techniques de référence &#40;SSRS&#41;](../technical-reference-ssrs.md)   
 [Utilisation d’en-têtes SOAP Reporting Services](using-reporting-services-soap-headers.md)  
  
  
