---
title: DLL de traçage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace DLLs [ODBC]
- tracing options [ODBC], trace DLLs
ms.assetid: 5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6fe910c93beac676e5fb0f663b740c03a826c326
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985225"
---
# <a name="trace-dll"></a>DLL de traçage
La DLL qui effectue le suivi est un des composants ODBC. La trace de la DLL est actuellement fourni en tant qu’exemple DLL dans le composant ODBC du SDK Windows et a été précédemment inclus le Kit de développement logiciel Microsoft Data Access composants (MDAC). Par conséquent, l’entrée de Registre, une interface et un exemple de code pour la DLL de trace sont disponibles. Cette DLL peut être remplacée par une trace de la DLL produite par un utilisateur ODBC ou un fournisseur tiers. Une DLL de traçage personnalisé doit disposer d’un nom différent de la DLL de trace exemple d’origine. DLL de trace doivent être installés dans le répertoire système, ou ils ne seront pas chargé. Les chaînes de connexion ne seront pas passées à la DLL de la trace par le Gestionnaire de pilotes.  
  
 La trace de la DLL effectue le suivi des arguments d’entrée, les arguments de sortie, les arguments différées, les codes de retour et les SQLSTATE. Lorsque le traçage est activé, le Gestionnaire de pilotes appelle la DLL de trace à deux endroits : une fois lors de l’entrée de fonction (avant la validation d’argument) et à nouveau juste avant le retour de la fonction.  
  
 Lorsqu’une application appelle une fonction, le Gestionnaire de pilotes appelle une fonction de trace dans la trace de la DLL avant l’appel de la fonction dans le pilote ou le traitement de l’appel lui-même. Chaque fonction ODBC a une fonction de trace correspondante (le préfixe *Trace*) qui est identique à la fonction ODBC à l’exception du nom. Lorsque la fonction de trace est appelée, la DLL de trace capture les arguments d’entrée et retourne un code de retour. Étant donné que la trace de la DLL est appelée avant que le Gestionnaire de pilote valide d’arguments, les appels de fonction non valide sont suivis, donc les erreurs de transition d’état et les arguments non valides sont enregistrés.  
  
 Après avoir appelé la fonction de trace dans la trace de la DLL, le Gestionnaire de pilotes appelle la fonction ODBC dans le pilote. Il appelle ensuite **TraceReturn** dans la trace de la DLL. Cette fonction accepte deux arguments : la valeur retournée par la DLL de trace pour la fonction de trace et le code de retour retournée par le pilote pour le Gestionnaire de pilote pour la fonction ODBC (ou la valeur retournée par le Gestionnaire de pilote lui-même s’il traité la fonction). La fonction utilise la valeur retournée par la fonction de trace pour manipuler les valeurs d’argument d’entrée capturée. Il écrit le code retourné pour la fonction ODBC dans le fichier journal (ou affiche de façon dynamique, si activé). Il déréférence les pointeurs d’argument de sortie et enregistre les valeurs d’argument de sortie.
