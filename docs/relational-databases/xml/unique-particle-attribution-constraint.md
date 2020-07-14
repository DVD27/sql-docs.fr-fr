---
title: Contrainte d’attribution de particule unique | Microsoft Docs
description: Découvrez comment la règle de contrainte d’attribution de particule unique rejette un schéma XSD s’il contient un type associé à un modèle de contenu potentiellement ambigu.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
f1_keywords:
- unique particle attribution
helpviewer_keywords:
- schema collections [SQL Server], unique particle attribution
- XML schema collections [SQL Server], unique particle attribution
- UPA constraint rule
- unique particle attribution constraint rule
ms.assetid: 6bb879e9-a5ee-402e-94e4-fe8cec5966b0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d7b6de76fdb5310a5121908779d4565a4b6ff1c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729829"
---
# <a name="unique-particle-attribution-constraint"></a>Contrainte d'attribution de particule unique
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Dans XSD, les modèles de contenu complexe sont soumis à la règle de la contrainte d'attribution de particule unique. Cette règle requiert que chaque élément d'un document d'instance corresponde sans ambiguïté à exactement une particule `<xsd:element>` ou `<xsd:any>` dans le modèle de contenu de son parent. Tout schéma qui contient un type avec un modèle de contenu potentiellement ambigu est rejeté.  
  
 Les causes d'ambiguïté les plus courantes sont les caractères génériques et les particules `<xsd:any>` ayant des plages d'occurrences variables, telles que minOccurs < maxOccurs. Par exemple, le modèle de contenu suivant est ambigu car un élément <`e1`> peut correspondre à l’élément `<xsd:element>` ou à l’élément `<xsd:any>`.  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
            <xsd:element name="e1"/>  
            <xsd:any namespace="##any"/>  
        </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 Le modèle de contenu suivant est également ambigu :  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:sequence>  
            <xsd:element name="e1" maxOccurs="2"/>  
            <xsd:element name="e2" minOccurs="0"/>  
            <xsd:element name="e1"/>  
        </xsd:sequence>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 Bien qu'un document tel que `<root><e1/><e2/><e1/></root>` puisse être validé sans ambiguïté, un document tel que `<root><e1/><e1/></root>` ne le peut pas car il est difficile de déterminer à quel élément `<xsd:element>` correspond le second élément `<e1/>` . Même si certains documents peuvent être validés sans ambiguïté, le schéma est rejeté en raison d'une ambiguïté potentielle.  
  
 Pour qu'un modèle de contenu soit valide, il doit être possible de valider n'importe quelle instance sans ambiguïté, indépendamment des éléments à venir. Imaginons par exemple le modèle de contenu suivant :  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e2"/>  
           </xsd:sequence>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e3"/>  
           </xsd:sequence>  
       </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 Pour un document tel que `<root><e1/><e3/></root>`, la séquence `<e1/><e3/>` correspond sans ambiguïté à la deuxième séquence `<xsd:sequence>`. Toutefois, étant donné que l'élément `<xsd:element>` auquel correspond `<e1/>` ne peut pas être déterminé sans tenir compte de `<e3/>`, le modèle de contenu enfreint la règle de la contrainte d'attribution de particule unique.  
  
## <a name="finding-more-information"></a>Sources d'informations complémentaires  
 Le document suivant est publié par le World Wide Web Consortium (W3C) et contient la description technique de la contrainte d'attribution de particule unique :  
  
 « XML Schema Part 1: Structures Second Edition, W3C Proposed Edited Recommendation » :  
  
-   Section 3.8.6 : Constraints on Model Group Schema Components  
  
-   Appendix H : Analysis of the Unique Particle Attribution Constraint (non-normative)  
  
 Pour lire le document, consultez [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881).  
  
## <a name="see-also"></a>Voir aussi  
 [Collections de schémas XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
