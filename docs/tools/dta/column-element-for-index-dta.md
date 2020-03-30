---
title: Column, élément pour les index (Assistant Paramétrage de base de données)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.openlocfilehash: 008cba36af33c465c3a126dc3e101b8ebca28e36
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307888"
---
# <a name="column-element-for-index-dta"></a>Column, élément pour les index (Assistant Paramétrage de base de données)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Spécifie les colonnes sur lesquelles l'index est créé pour une configuration spécifiée par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
 **Type**: facultatif. Spécifie le type de colonne d'index. Utilisez un type de données **string** pour spécifier cet attribut avec l'une des valeurs autorisées suivantes :  
  
-   **KeyColumn**  
  
     Spécifie que la colonne est référencée par une clé d'index. Utilisez la syntaxe suivante pour définir cet attribut :  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Pour plus d’informations sur les colonnes clés, consultez [Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Spécifie que la colonne est une colonne non clé (au lieu d'une colonne clé). Utilisez la syntaxe suivante pour définir cet attribut :  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Pour plus d’informations sur les colonnes incluses, consultez [Créer des index avec colonnes incluses](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: facultatif. Spécifie l'ordre de tri de la colonne. Utilisez un type de données **string** pour spécifier un ordre de tri **"Ascending"** ou **"Descending"** comme suit :  
  
```  
<Column SortOrder="Ascending">  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Peut spécifié jusqu’à 1 024 colonnes pour l’élément **Index** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Index, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/index-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les colonnes &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
