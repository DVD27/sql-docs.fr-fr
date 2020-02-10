---
title: 'Demande de références URL à des données BLOB à l’aide de SQL : encode (SQLXML 4,0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 153a88bcb31f65d4e6aff007cfbee7d1f7afc6df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013729"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Demande de références URL à des données BLOB à l'aide de sql:encode (SQLXML 4.0)
  Dans un schéma XSD annoté, lorsqu'un attribut (ou élément) est mappé à une colonne BLOB dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les données sont retournées au format encodé en base 64 dans XML.  
  
 Si vous souhaitez retourner une référence aux données (un URI) qui pourra être utilisée ultérieurement pour récupérer les données BLOB dans un format binaire, spécifiez l'annotation `sql:encode`. Vous pouvez spécifier `sql:encode` sur un attribut ou un élément de type simple.  
  
 Spécifiez l'annotation `sql:encode` pour indiquer qu'une URL au champ doit être retournée au lieu de la valeur du champ. 
  `sql:encode` dépend de la clé primaire pour générer une sélection singleton dans l'URL. La clé primaire peut être spécifiée à l' `sql:key-fields` aide de l’annotation.  
  
 La valeur « url » ou « default » peut être attribuée à l'annotation `sql:encode`. Une valeur « default » retourne des données au format encodé en base 64.  
  
 L'annotation `sql:encode` ne peut pas être utilisée avec `sql:use-cdata` ou sur les types d'attributs ID, IDREF, IDREFS, NMTOKEN ou NMTOKENS. Elle ne peut pas non plus être utilisée avec l’attribut **fixed** XSD.  
  
> [!NOTE]  
>  Les colonnes de type BLOB ne peuvent pas être utilisées en tant que partie d'une clé ou d'une clé étrangère.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>R. Spécification de sql:encode pour obtenir une référence URL à des données BLOB  
 Dans cet exemple, le schéma de mappage `sql:encode` spécifie sur l’attribut **LargePhoto** pour récupérer la référence URI à une photo de produit spécifique (au lieu de récupérer les données binaires dans un format encodé en base 64).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier en tant que sqlEncode.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom sqlEncodeT.xml dans le même répertoire où vous avez enregistré sqlEncode.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (sqlEncode.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le résultat obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
