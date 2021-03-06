---
title: Propriétés personnalisées des sources XML | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 32afa6d65929fda676f7eebb1bc78ab1d05cd789
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074017"
---
# <a name="xml-source-custom-properties"></a>Propriétés personnalisées des sources XML

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La source XML comporte des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la source XML. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Entier|Mode utilisé pour accéder aux données XML.|  
|UseInlineSchema|Booléen|Valeur qui indique si une définition de schéma inséré doit être utilisée dans la source XML. La valeur par défaut de cette propriété est **False**.|  
|XMLData|String|Fichier ou variables à partir desquels les données XML sont extraites.<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
|XMLSchemaDefinition|String|Chemin d'accès et nom de fichier du fichier de définition de schéma (.xsd).<br /><br /> Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.|  
  
 Le tableau suivant décrit les propriétés personnalisées de la sortie de la source XML. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|RowsetID|String|Valeur qui identifie l'ensemble de lignes associé à la sortie.|  
  
 Les colonnes de sortie de la source XML ne possèdent pas de propriétés personnalisées.  
  
 Pour plus d'informations, consultez [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
