---
title: Éditeur de transformation d’Union totale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b62fb5e33311f1011911c40fc858723b218bac55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054832"
---
# <a name="union-all-transformation-editor"></a>Éditeur de transformation d'union totale
  La boîte de dialogue **Éditeur de transformation d'union totale** permet de fusionner plusieurs jeux de lignes d'entrée dans un seul jeu de lignes de sortie. En incluant la transformation d'union totale dans un flux de données, vous pouvez fusionner les données de plusieurs flux, créer des datasets complexes en imbriquant les transformations d'union totale et en refusionnant les lignes après avoir corrigé les erreurs contenues dans les données.  
  
 Pour en savoir plus sur la transformation d'union totale, consultez [Union All Transformation](data-flow/transformations/union-all-transformation.md).  
  
## <a name="options"></a>Options  
 **Nom de colonne de sortie**  
 Permet de saisir un alias pour chaque colonne. Par défaut, il s'agit du nom de la colonne d'entrée provenant de la première entrée (de référence). Vous pouvez toutefois choisir un nom unique descriptif.  
  
 **Entrée 1 d'union totale**  
 Sélectionnez cette option dans la liste des colonnes d'entrée disponibles dans la première entrée (de référence). Les métadonnées des colonnes mappées doivent correspondre.  
  
 **Entrée n d'union totale**  
 Sélectionnez cette option dans la liste des colonnes d'entrée disponibles dans à partir de la deuxième entrée. Les métadonnées des colonnes mappées doivent correspondre.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Fusionner des données à l’aide de la transformation d’Union totale](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Transformation de fusion](data-flow/transformations/merge-transformation.md)   
 [transformation de jointure de fusion](data-flow/transformations/merge-join-transformation.md)  
  
  
