---
title: Spécifier les paramètres d’informations des périphériques dans une URL | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 906a21de49d562d788f9a1384b31e080616c67c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65578439"
---
# <a name="specify-device-information-settings-in-a-url"></a>Spécifier les paramètres d'informations de périphérique dans une URL
  Les paramètres d'informations de périphérique sont des paramètres qui sont transmis à une extension de rendu. Si vous utilisez les méthodes du service Web Report Server [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour effectuer le rendu d’un rapport, un élément XML **DeviceInfo** est transmis en tant que paramètre d’entrée. Les éléments enfants de l’élément **DeviceInfo** sont spécifiques aux paramètres d’informations de périphérique de différentes extensions de rendu. Vous pouvez inclure des paramètres d’informations de périphérique dans une URL en utilisant la chaîne de paramètre *rc:tag=value* , où *tag* est le nom de l’élément des paramètres d’informations de périphérique en cours d’accès. Pour plus d’informations sur les paramètres d’informations de périphérique dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], consultez [Transmission de paramètres d’informations de périphérique aux extensions de rendu](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit le format du rapport spécifié sur JPEG en utilisant le paramètre d’informations de périphérique *OutputFormat* de l’extension de rendu d’image (les sauts de ligne ont été ajoutés pour la lisibilité) :  
  
```  
https://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Accès URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Référence de paramètre d'accès URL](../reporting-services/url-access-parameter-reference.md)  
  
  
