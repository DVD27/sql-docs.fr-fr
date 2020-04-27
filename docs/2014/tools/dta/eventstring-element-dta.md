---
title: Élément EventString (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30e46515fda5bf03a96e9f1168b470f635698d07
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211118"
---
# <a name="eventstring-element-dta"></a>EventString, élément (Assistant Paramétrage de base de données)
  Spécifie une charge de travail de script [!INCLUDE[tsql](../../includes/tsql-md.md)] directement dans le fichier d'entrée XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Weight`|facultatif. Spécifie le facteur de pondération de la requête (facteur d'importance) pour l'événement spécifié. Utilisez un type de données `float` pour spécifier la pondération. Par exemple, `Weight`="100.01". La valeur minimale que vous pouvez spécifier pour `Weight` est « 0 ».|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|`string`, la longueur est illimitée.|  
|**Valeur par défaut**|Aucune.|  
|**Occurrence**|Obligatoire une fois si aucun autre type de charge de travail n'est spécifié. Vous devez spécifier un élément enfant `EventString`, `File` ou `Database` pour le parent `Workload`, mais un seul type peut être utilisé. Par exemple, si vous spécifiez une charge de travail avec l'élément `EventString`, vous ne pouvez pas spécifier une charge de travail avec l'élément `File` dans le même fichier d'entrée XML.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Workload, élément &#40;Assistant Paramétrage de base de données&#41;](workload-element-dta.md)|  
|**Éléments enfants**|Aucune.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML avec une charge de travail Inline &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
