---
title: '&lt;xsd:redefine&gt;, élément | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 59eafff14c6a0cc7752817a31648b64bd5edc907
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702447"
---
# <a name="the-ltxsdredefinegt-element"></a>Élément &lt;xsd:redefine&gt;
  L’élément W3C XSD **redefine** assure la prise en charge de la redéfinition des composants de schéma. Toutefois, la prise en charge de cette directive est potentiellement coûteuse pour les performances et requiert également que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] revalide toutes les instances du `xml` type de données associées au schéma redéfini. Par conséquent, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge cet élément. Les schémas XML qui incluent l’élément **\<xsd:redefine>** sont rejetés par le serveur.  
  
 Au lieu d'utiliser cet élément, vous pouvez mettre à jour un schéma ou ses composants en procédant comme suit :  
  
1.  Créez une nouvelle collection de schémas XML en y incluant les composants de schéma modifiés.  
  
2.  Retapez tous les `xml` types de données (XML DT) qui utilisent la collection de schémas XML à redéfinir pour utiliser la nouvelle collection de schémas XML à la place. Pour cela, utilisez l'option ALTER COLUMN de la commande ALTER TABLE pour retaper les colonnes ou modifiez les contraintes de collection de schémas XML sur les variables ou les paramètres.  
  
3.  Supprimez l'ancienne version de la collection de schémas XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
