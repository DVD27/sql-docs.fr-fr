---
title: Exécuter des fichiers de modèle avec la propriété CommandStream
description: Découvrez comment exécuter des fichiers modèles composés de requêtes SQL ou XPath en utilisant la propriété CommandStream de l’objet SqlXmlCommand.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a3b7922921c64c9afb7ef37be57db23a32470eaf
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388366"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a>Exécution de fichiers modèles à l'aide de la propriété CommandStream
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Cet exemple illustre comment les fichiers modèles qui composent les requêtes SQL ou XPath peuvent être spécifiés en utilisant la propriété CommandStream de l’objet SqlXmlCommand. Dans cette application, un fichierstreamobject est ouvert pour un fichier de commande, et le flux de fichiers est attribué comme le Commandeur qui est exécuté.  
  
 Dans l’exemple suivant, la propriété CommandType est spécifiée comme SqlXmlCommandType.Template (pas comme TemplateFile).  
  
 Il s'agit de l'exemple de modèle XML :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Il s'agit de l'exemple d'application C#. Pour tester l'application, enregistrez le modèle (TemplateFile.xml),  puis exécutez l'application. L'application exécute la requête spécifiée dans le modèle XML et affiche le document XML généré sur l'écran.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;        
      }  
  
      public static int Main(String[] args)  
      {  
         testParams();     
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Enregistrez le modèle XML (TemplateFile.xml) fourni dans cet exemple dans un dossier.  
  
2.  Enregistrer le code C (DocSample.cs) qui est fourni dans cet exemple dans le même dossier dans lequel le schéma est stocké. (Si vous stockez les fichiers dans un dossier différent, vous devrez modifier le code et spécifier le chemin d'accès approprié au répertoire pour le schéma de mappage.)  
  
3.  Compilez le code. Pour compiler le code à l'invite de commandes, utilisez :  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Un fichier exécutable (DocSample.exe) est alors créé.  
  
4.  À l'invite de commandes, exécutez DocSample.exe.  
  
  
