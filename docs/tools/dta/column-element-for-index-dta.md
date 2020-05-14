---
title: Column, élément pour les index (Assistant Paramétrage de base de données)
description: Dans l’utilitaire dta, l’élément Column pour les index spécifie les colonnes dans lesquelles l’index doit être créé pour une configuration spécifiée par l’utilisateur.
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
ms.openlocfilehash: 02900685d93eef62553d830494d25ec83ca83ce1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831625"
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
  
 **Type** : facultatif. Spécifie le type de colonne d'index. Utilisez un type de données **string** pour spécifier cet attribut avec l'une des valeurs autorisées suivantes :  
  
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
  
 **SortOrder** : facultatif. Spécifie l'ordre de tri de la colonne. Utilisez un type de données **string** pour spécifier un ordre de tri **"Ascending"** ou **"Descending"** comme suit :  
  
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
  
  
