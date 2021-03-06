---
title: 'Leçon 4 : Ajout de Redirection de flux d’erreurs | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 636c199e84eae9bd141bcb33fc5c06f35eac760b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62891326"
---
# <a name="lesson-4-adding-error-flow-redirection"></a>Leçon 4 : Ajout de redirection de flux d’erreurs
  Pour traiter les erreurs qui risquent de se produire dans le processus de transformation, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vous permet de décider par composant et par colonne comment traiter les données qui ne peuvent pas être transformées. Vous pouvez choisir d'ignorer une erreur dans certaines colonnes, de rediriger dans sa totalité la ligne qui a échoué ou simplement de faire échouer le composant. Par défaut, tous les composants de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sont configurés pour échouer lorsque des erreurs se produisent. Le fait de faire échouer un composant entraîne l'échec du package et l'arrêt de tous les traitements ultérieurs.  
  
 Au lieu de permettre l'arrêt de l'exécution du package à la suite d'échecs, il est recommandé de configurer et de traiter les erreurs de traitement potentielles au moment où elles se produisent dans la transformation. Si vous pouvez choisir d'ignorer les erreurs pour vous assurer que votre package s'exécute correctement, il est souvent préférable de rediriger la ligne qui a échoué vers un autre chemin de traitement où les données et l'erreur peuvent être rendues persistantes, étudiées et retraitées ultérieurement.  
  
 Dans cette leçon, vous allez créer une copie du package que vous avez développé dans [leçon 3 : Ajout de la journalisation](lesson-3-add-logging-with-ssis.md). Avec ce package, vous allez créer une version endommagée de l'un des exemples de fichiers de données. Ce fichier endommagé entraînera une erreur de traitement lors de l'exécution du package.  
  
 Pour gérer les données d'erreur, vous allez ajouter et configurer une destination de fichier plat chargée d'écrire dans un fichier toutes les lignes qui ne parviennent pas à détecter une valeur de recherche dans la transformation Lookup Currency Key.  
  
 Avant d'écrire les données d'erreur dans le fichier, vous devez inclure un composant Script qui utilise un script pour se procurer des descriptions sur les erreurs. Vous allez ensuite reconfigurer la transformation Lookup Currency Key pour réacheminer vers la transformation Script toutes les données qui n'ont pas pu être traitées.  
  
> [!IMPORTANT]  
>  Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d'informations sur l'installation et le déploiement d' **AdventureWorksDW2012**, consultez [Reporting Services Product Samples sur CodePlex](https://go.microsoft.com/fwlink/p/?LinkId=526910).  
  
## <a name="tasks-in-lesson"></a>Contenu de la leçon  
 Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du Package de la leçon 3](lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Étape 2 : Création d’un fichier endommagé](lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Étape 3 : Ajout de Redirection de flux d’erreurs](lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Étape 4 : Ajout d’une Destination de fichier plat](lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Étape 5 : Test de la leçon 4 du Package du didacticiel](lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
 [Étape 1 : Copie du Package de la leçon 3](lesson-4-1-copying-the-lesson-3-package.md)  
  
  
