---
title: Élément de base de données de Configuration (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fbca62a5d32ed6b7ec30eb5d6dba6a82a2b80c64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298351"
---
# <a name="database-element-for-configuration-dta"></a>Database, élément pour les configurations (Assistant Paramétrage de base de données)
  Spécifie la base de données dans laquelle vous souhaitez que l'Assistant Paramétrage du moteur de base de données évalue la configuration hypothétique (spécifiée par l'élément `Configuration`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une ou plusieurs fois par élément `Server`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Server, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](server-element-for-configuration-dta.md)|  
|**Éléments enfants**|[Name, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](name-element-for-database-dta.md)<br /><br /> [Schema, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](schema-element-for-database-dta.md)<br /><br /> [Recommendation, élément &#40;Assistant Paramétrage de base de données&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **DatabaseTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Ne confondez pas cet élément `Database` avec celui dont le parent racine est l'élément `Server`, qui se trouve en haut du fichier d'entrée XML. Pour plus d’informations, consultez [Database, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](database-element-for-server-dta.md).  
  
## <a name="example"></a>Exemple  
 Pour un exemple d’utilisation de ce `Database` élément, consultez la [exemple de fichier d’entrée XML avec la Configuration spécifiée par l’utilisateur &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
