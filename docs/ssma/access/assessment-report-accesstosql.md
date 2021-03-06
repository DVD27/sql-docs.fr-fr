---
title: Rapport d’évaluation (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c28fb4cf5d110e01b156fc6ce985b2cb2fb7bfe1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67910686"
---
# <a name="assessment-report-accesstosql"></a>Rapport d’évaluation (AccessToSQL)
La fenêtre de rapport d’évaluation affiche les résultats de la conversion d’objets de base de données à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, et peut également aider à vous estimer le coût et complexité de vos projets de migration.  
  
Pour créer un rapport d’évaluation, sélectionner les objets à convertir dans l’Explorateur de métadonnées source, avec le bouton droit **bases de données**, puis sélectionnez **créer un rapport**. Vous pouvez également afficher ce rapport automatiquement après la conversion de schémas. Toutefois, le nom du rapport sera rapport de Conversion. Pour plus d’informations, consultez [paramètres de projet (GUI) (SSMA courant)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
## <a name="options"></a>Options  
**Volet Explorateur**  
Contient une hiérarchie d’objets dans le rapport d’évaluation. Développez les dossiers pour afficher les sous-composants et les objets individuels. Lorsque vous cliquez sur une catégorie ou un objet, les statistiques de conversion de cette catégorie ou d’un objet apparaissent dans le volet de détails.  
  
**Volet d’informations**  
Affiche les messages de statistiques ou d’une erreur et d’avertissement pour l’objet sélectionné de la conversion. Par exemple, si le dossier Tables est sélectionné, le volet d’informations affiche le nombre de clés étrangères, les index, les clés primaires et les tables qui ont été convertis.  
  
**Volet messages**  
Affiche les erreurs, avertissements et les messages d’information qui ont été générées lorsque le rapport d’évaluation a été créé. Les messages sont regroupés par numéro.  
  
Pour afficher les détails du message, cliquez sur **erreurs**, **avertissements**, ou **Messages**, puis développez un message. SSMA affiche la liste des objets qui présentent cette erreur. Cliquez sur un objet pour afficher tous les détails de la conversion de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
[Reference(Access) d’Interface utilisateur](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
