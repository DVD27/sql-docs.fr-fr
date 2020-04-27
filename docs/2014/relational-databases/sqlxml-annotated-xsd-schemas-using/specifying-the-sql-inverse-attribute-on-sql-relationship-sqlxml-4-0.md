---
title: 'Spécification de l’attribut SQL : inverse sur SQL : Relationship (SQLXML 4,0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e1f1e7e34ce3ae80d18c13a4cafd0d60128a3b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013629"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Spécification de l'attribut sql:inverse sur sql:relationship (SQLXML 4.0)
  L'attribut `sql:inverse` est utile uniquement lorsque le schéma XSD est utilisé pour le chargement en masse ou par un code de mise à jour (updategram). L' `sql:inverse` attribut peut être spécifié sur l' ** \<élément SQL : Relationship>** . Dans les codes de mise à jour, la logique de code de mise à jour interprète le schéma pour déterminer les tables et colonnes mises à jour par l'opération de code de mise à jour. Les relations parent-enfant spécifiées dans le schéma déterminent l'ordre dans lequel les enregistrements sont modifiés (insérés ou supprimés).  
  
 Si vous avez un schéma XSD dans lequel la relation parent-enfant est spécifiée dans l'ordre inverse de la relation clé primaire/clé étrangère entre les colonnes de base de données correspondantes, l'opération d'insertion ou de suppression du code de mise à jour échouera à cause de la violation de clé primaire/clé étrangère. Dans ce cas, l' `sql:inverse` attribut est spécifié (`sql:inverse="true"`) dans l' ** \<élément SQL : Relationship>** , et la logique mise à jour inverse son interprétation de la relation parent-enfant spécifiée dans le schéma.  
  
 L'attribut `sql:inverse` prend une valeur booléenne (0=faux, 1=vrai). Les valeurs acceptables sont 0, 1, true et false.  
  
 Pour obtenir un exemple fonctionnel à `sql:inverse` l’aide de l’annotation, consultez [spécification d’un schéma de mappage annoté dans un mise à jour](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4,0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
