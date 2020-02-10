---
title: Éditeur de source de fichier plat (page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f8fda95b51f568098b0ac9fc13b8a204adb71c51
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058610"
---
# <a name="flat-file-source-editor-columns-page"></a>Éditeur de source de fichier plat (page Colonnes)
  Utilisez le nœud **Colonnes** de la boîte de dialogue **Éditeur de source de fichier plat** pour mapper une colonne de sortie à chaque colonne externe (source).  
  
> [!NOTE]  
>  La `FileNameColumnName` propriété de la source de fichier plat et `FastParse` la propriété de ses colonnes de sortie ne sont pas disponibles dans l' **éditeur de source de fichier plat**, mais elles peuvent être définies à l’aide de l' **éditeur avancé**. Pour plus d'informations sur ces propriétés, consultez la section sur la source de fichier plat de [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).  
  
 Pour en savoir plus sur la source de fichier plat, consultez [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Options  
 **Colonnes externes disponibles**  
 Affiche la liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table.  
  
 **Colonne externe**  
 Affiche les colonnes externes (sources) dans l'ordre de lecture de la tâche. Vous pouvez modifier cet ordre en supprimant d'abord les colonnes sélectionnées dans la table, puis en choisissant des colonnes externes dans la liste selon un ordre différent.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; vous pouvez néanmoins choisir n'importe quel nom unique et significatif. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source de fichier plat &#40;page Gestionnaire de connexions&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [Éditeur de source de fichier plat &#40;page sortie d’erreur&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Gestionnaire de connexions de fichiers plats](connection-manager/file-connection-manager.md)  
  
  
