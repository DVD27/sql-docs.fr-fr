---
title: Autres annotations (SQLXML)
description: Affichez une liste d’annotations SQLXML avec une description de la façon dont chacune d’elles est interprétée par le chargement en masse XML.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 30e59d3fc049d56e8142f241dc5c75c054db837c
ms.sourcegitcommit: 6593b3b6365283bb76c31102743cdccc175622fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84306258"
---
# <a name="annotation-interpretation---other-annotations"></a>Interprétation des annotations - Autres annotations
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Outre les annotations présentées dans les rubriques précédentes de cette section, le chargement en masse XML interprète les annotations suivantes, comme suit :  
  
 **sql:id-prefix**  
 Si conformément au schéma, des préfixes sont ajoutés aux données XML, le chargement en masse XML supprime ces préfixes avant d'envoyer les données à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **sql:use-cdata**  
 Le chargement en masse XML lit le texte qui est stocké dans les sections CDATA et l'envoie à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **sql:url-encode**  
 Le chargement en masse XML ne prend pas en charge cette annotation. Par exemple, vous ne pouvez pas spécifier une URL dans l'entrée de données XML et vous attendre à ce que le chargement en masse XML lise les données à cet emplacement et les stocke dans la base de données.  
  
 **sql:is-mapping-schema**  
 Le chargement en masse XML ne prend pas en charge cette annotation, ni **sql:id**.  
  
> [!NOTE]  
>  Le chargement en masse XML ne prend pas en charge les schémas de mappage insérés.  
  
 **sql:key-fields**  
 Le chargement en masse XML ignore toujours cette annotation.  
  
## <a name="see-also"></a>Voir aussi  
 [Interprétation des annotations &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
  
  
