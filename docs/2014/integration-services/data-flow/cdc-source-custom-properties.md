---
title: Propriétés personnalisées des sources CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 744e9357-94a9-4202-abe8-1d3d202697e9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 618fc83b9e2bba73e41ea6925a70271060baaac5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62828116"
---
# <a name="cdc-source-custom-properties"></a>Propriétés personnalisées des sources CDC
  Le tableau suivant décrit les propriétés personnalisées de la source CDC. Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|Connexion|Connexion ADO.NET|Connexion ADO.NET à la base de données CDC [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour l'accès aux tables de modifications.|  
|StateVariable|String|Variable de package de chaîne SSIS qui gère l'état de capture de données modifiées de l'exécution de capture de données modifiées actuelle.|  
|CdcProcessingMode|Integer (énumération)|Ce mode détermine le mode de gestion du traitement. Les options possibles sont : **Tout**, **Tout avec les anciennes valeurs**, **NET**, **Net avec masque de mise à jour**et **Net avec fusion**.<br /><br /> Modes qui commencent par Tout (retourner toutes les modifications) et modes qui commencent par Net (retourner les modifications Net uniquement).<br /><br /> Les tables sans clé primaire peuvent uniquement accepter les valeurs ALL.<br /><br /> **Net avec masque de mise à jour** ajoute des colonnes booléennes avec le modèle de nom **__$\<nom-colonne>\__Changed** qui indique les colonnes modifiées dans la ligne de modification active.<br /><br /> Pour plus d’informations sur les valeurs de cette propriété, consultez [Éditeur de source CDC &#40;page Gestionnaire de connexions&#41;](../cdc-source-editor-connection-manager-page.md).|  
|CaptureInstance|String|Nom de l'instance de capture de données contenant la table CDC à lire. Une table source capturée peut contenir une ou deux instances capturées pour gérer la transition transparente de la définition de table lors des modifications de schéma. Si plusieurs instances de capture sont définies pour la table source qui est capturée, sélectionnez l'instance de capture à utiliser ici. Le nom par défaut de l’instance de capture pour une table [schema].[table] est \<schéma>_\<table>, mais le nom réel utilisé pour cette instance de capture peut être différent. La table réelle dans laquelle les données sont lues est la table CDC **cdc .\<instance-capture>_CT**.|  
|ReprocessingIndicator|Boolean|Valeur qui spécifie s’il faut ajouter la colonne **__$reprocessing** . Cette colonne de sortie spéciale permet au développeur SSIS de gérer différemment les erreurs de cohérence lorsqu'il travaille sur la plage de traitement initiale.<br /><br /> Si la valeur est **true**, la colonne  **__$reprocessing** est ajoutée.<br /><br /> Cette colonne a la valeur **true** quand la plage de traitement CDC chevauche la plage de traitement initiale (plage de NSE correspondant à la période de charge initiale) ou quand une plage de traitement CDC est retraitée suite à une erreur lors d’une exécution précédente. Cette colonne d'indicateur permet au développeur SSIS de gérer les erreurs différemment lors du retraitement des modifications (par exemple, les actions telles que la suppression d'une ligne inexistante et une insertion ayant échoué sur une clé dupliquée peuvent être ignorées).<br /><br /> La valeur par défaut est **false**.|  
|CommandTimeout|Integer|Cette valeur indique le délai d’attente (en secondes) à utiliser pour communiquer avec la base de données [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Cette valeur est utilisée lorsque le temps de réponse de la base de données est très lent et que la valeur par défaut (30 secondes) n'est pas suffisante.|  
  
 Pour plus d'informations sur la source CDC, consultez [CDC Source](cdc-source.md).  
  
  
