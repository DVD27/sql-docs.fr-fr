---
title: Unicode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e0044a2e2efbf0d8921a07ed4679806ba50bcd1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087563"
---
# <a name="unicode"></a>Unicode
La norme Unicode définit l’encodage des caractères dans de nombreux langages.  
  
 Pour plus d’informations sur la norme Unicode, consultez [du Unicode Consortium](https://www.unicode.org).  
  
 La norme Unicode définit un jeu de caractères universels. Une page de codes Windows ANSI définit un jeu de caractères, contenant généralement des caractères pour une langue. Il peut être plus difficile à écrire une application qui est nécessaire pour utiliser les pages de codes différentes.  
  
 Unicode ne nécessite pas une page de codes. Chaque point de code est mappé à un caractère unique dans un langage quelconque.  
  
 Actuellement, l’encodage que ODBC prend en charge d’Unicode uniquement est UCS-2, qui utilise un entier 16 bits (longueur fixe) pour représenter un caractère. Unicode aux applications de travailler dans différentes langues.  
  
 Le Gestionnaire de pilotes ODBC 3.5 (ou version ultérieure) prend en charge Unicode. Cela affecte les deux domaines majeurs : appels de fonction et les types de données string. Les arguments de chaîne de gestionnaire de pilotes maps (fonction) et les données de type chaîne comme requis par l’application et le pilote, qui peuvent être compatibles Unicode soit compatible ANSI. Ces deux zones sont décrites en détail dans les sections, [Arguments de la fonction Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md) et [les données Unicode](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Le Gestionnaire de pilotes ODBC 3.5 (ou version ultérieure) prend en charge l’utilisation d’un pilote d’Unicode avec une application Unicode et une application ANSI. Il prend également en charge l’utilisation d’un pilote ANSI avec une application ANSI. Le Gestionnaire de pilotes offre limitée mappage Unicode en ANSI pour une application Unicode fonctionne avec un pilote ANSI.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Arguments des fonctions Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Données Unicode](../../../odbc/reference/develop-app/unicode-data.md)
