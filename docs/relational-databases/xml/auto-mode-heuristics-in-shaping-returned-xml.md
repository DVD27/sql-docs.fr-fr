---
title: Heuristique du mode AUTO permettant de définir la forme des données XML renvoyées | Microsoft Docs
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||=azuresqldb-mi-current||>=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions
ms.openlocfilehash: 408589a38ae9b01777110bbab1fb3b20c380a6c6
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68029338"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a>Heuristique du mode AUTO permettant de définir la forme des données XML renvoyées

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Le mode AUTO détermine la forme des données XML renvoyées en fonction de la requête. Lors de la définition de l'imbrication des éléments, l'heuristique du mode AUTO compare les valeurs de colonnes de lignes adjacentes. Les colonnes de tous les types, sauf **ntext**, **text**, **image**et **xml**, sont comparées. Les colonnes de type **(n)varchar(max)** et **varbinary(max)** sont comparées.  
  
 L'exemple suivant illustre l'heuristique du mode AUTO qui détermine la forme des données XML obtenues :  
  
```sql
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
ORDER BY T1.Id
FOR XML AUTO;
```  
  
 Pour déterminer à quel endroit commence un nouvel élément <`T1`>, toutes les valeurs de colonne de T1, sauf **ntext**, **text**, **image** et **xml**, sont comparées si la clé de la table T1 n’est pas spécifiée. Ensuite, supposons que la colonne **Name** soit de type **nvarchar(40)** et que l’instruction SELECT renvoie l’ensemble de lignes suivant :  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 L'heuristique du mode AUTO compare toutes les valeurs de la table T1, les colonnes Id et Name. Étant donné que les deux premières lignes contiennent les mêmes valeurs pour les colonnes Id et Name, un élément \<T1> possédant deux éléments enfants \<T2> est ajouté au résultat.  
  
 Voici le document XML renvoyé :  
  
```xml
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 Supposons maintenant que la colonne Name soit de type **text** . L'heuristique du mode AUTO ne compare pas les valeurs de ce type. Au lieu de cela, elle considère que les valeurs ne sont pas identiques. Cela aboutit à la génération de données XML suivante :  
  
```xml
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode AUTO avec FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)  
  
  
