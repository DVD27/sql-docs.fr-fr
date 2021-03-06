---
title: Chargement d’objets blob Azure, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 392fcbf3a46b48b2032b5792321e9a22b3027341
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62832775"
---
# <a name="azure-blob-upload-task"></a>Tâche de chargement d’objets blob Azure
  La tâche de chargement des objets Blob Azure permet à un package SSIS charger des fichiers vers un stockage blob Azure.   
Pour ajouter une **tâche de chargement d’objets blob Azure**, faites-la glisser vers le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue de **l’Éditeur de tâche de chargement d’objets blob Azure** .  
  
 Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Field**|**Description**|  
|AzureStorageConnection|Spécifiez un gestionnaire de connexions Azure Storage existant ou créez-en un qui fait référence à un compte Azure Storage et pointe vers l’emplacement où les fichiers d’objets blob sont hébergés.|  
|BlobContainer|Spécifie le nom du conteneur d’objets blob qui contiendra les fichiers chargés en tant qu’objets blob.|  
|BlobDirectory|Spécifie le répertoire d’objets blob dans lequel le fichier chargé sera stocké en tant qu’objet blob de bloc. Le répertoire d’objets blob est une structure hiérarchique virtuelle. Si l’objet blob existe déjà, il sera remplacé.|  
|LocalDirectory|Spécifie le répertoire local qui contient les fichiers à charger.|  
|FileName|Spécifie un filtre de nom pour sélectionner des fichiers avec le modèle de nom spécifié. Par ex. MySheet*.xls\* inclut les fichiers MySheet001.xls et MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Spécifie un filtre d’intervalle de temps. Les fichiers modifiés après **TimeRangeFrom** et avant **TimeRangeTo** seront inclus.|  
  
  
