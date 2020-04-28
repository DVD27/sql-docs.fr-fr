---
title: Référence de configuration Web
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e9d3cd20fc219a7159de0b271dafcc0e9fb2c3ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728829"
---
# <a name="web-configuration-reference-master-data-services"></a>Référence de la configuration Web (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] utilise un fichier Web.config pour contenir les paramètres de configuration qui permettent à Internet Information Services (IIS) d’héberger l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] et le service web. Ce fichier Web.config se trouve dans le dossier WebApplication du chemin d'installation de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations sur le chemin et les autorisations, consultez [Autorisations d’accès aux dossiers et aux fichiers &#40;Master Data Services&#41;](../master-data-services/folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Éléments Web.Config  
 Le fichier Web. config contient un élément [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] personnalisé, ** \<MasterDataServices>**, en plus des éléments de configuration IIS, .NET Framework, ASP.net et Windows Communication Foundation (WCF) standard. Le tableau suivant décrit les éléments inclus dans le fichier Web.config.  
  
|Élément de configuration|Description|  
|---------------------------|-----------------|  
|**masterDataServices**|Élément personnalisé. Connecte le service Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] à une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**connectionStrings**|Élément ASP.NET. Pour plus d’informations, consultez [connectionStrings, élément (Schéma des paramètres ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178347) dans MSDN Library.|  
|**System. Web**|Élément ASP.NET. Pour plus d’informations, consultez [system.web, élément (Schéma des paramètres ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178348) dans MSDN Library.|  
|**du**|Élément .NET Framework. Pour plus d’informations, consultez [ \<Startup>, élément](https://go.microsoft.com/fwlink/?LinkId=178349) dans MSDN Library.|  
|**Language**|Élément .NET Framework. Pour plus d’informations, consultez [ \<Runtime> Element](https://go.microsoft.com/fwlink/?LinkId=178350) dans MSDN Library.|  
|**system.codedom**|Élément .NET Framework. Pour plus d’informations, consultez [ \<System. CodeDom>, élément](https://go.microsoft.com/fwlink/?LinkId=178351) dans MSDN Library.|  
|**System. Web. extensions**|Élément ASP.NET. Pour plus d’informations, consultez [system.web.extensions, élément (Schéma des paramètres ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178352) dans MSDN Library.|  
|**system.webServer**|Groupe de sections qui contient des éléments IIS. Pour plus d’informations, consultez [system.webServer, groupe de sections \[Schéma des paramètres IIS 7\]](https://go.microsoft.com/fwlink/?LinkId=178353) dans MSDN Library.|  
|**system.serviceModel**|Élément WCF. Pour plus d’informations, consultez [ \<System. ServiceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) dans MSDN Library.|  
|**system.diagnostics**|Élément .NET Framework. Pour plus d’informations, consultez [ \<System. Diagnostics>, élément](https://go.microsoft.com/fwlink/?LinkId=178355) dans MSDN Library.|  
|**Rend**|Élément ASP.NET. Pour plus d’informations, consultez [appSettings, élément (Schéma des paramètres généraux)](https://go.microsoft.com/fwlink/?LinkId=178356) dans MSDN Library.|  
  
## <a name="masterdataservices-element"></a>Élément masterDataServices  
 L' ** \<élément MasterDataServices>** est un élément personnalisé qui permet de connecter un [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] service Web à une [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Éléments et attributs  
  
|Élément|Description|  
|----------|-----------------|  
|**instancié**|Élément enfant. Contient des attributs qui spécifient les informations concernant le service Web et la chaîne de connexion à la base de données.|  
|**virtualPath**|Attribut. Spécifie le chemin d'accès virtuel de l'application Web et du service Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Correspond à l’attribut **path** de l’élément **\<application>** sous l’élément **\<site>** dans le fichier ApplicationHost.config IIS.|  
|**siteName**|Attribut. Spécifie le nom du site qui héberge l'application Web et le service Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Correspond à l’attribut **name** de l’élément **\<site>** sous l’élément **\<sites>** dans le fichier ApplicationHost.config IIS.|  
|**connectionName**|Attribut. Spécifie le nom de la connexion à utiliser. Correspond à l’attribut **name** de l’élément **\<add>** sous l’élément **\<connectionStrings>** dans Web.config.|  
|**serviceName**|Attribut. Spécifie le nom du service Web. Correspond à l’attribut **name** de l’élément **\<service>** sous l’élément **\<services>** dans Web.config.|  
  
### <a name="example"></a>Exemple  
 L'exemple suivant présente un service nommé MDS1 sur le site Contoso et le chemin d'accès /MDS, utilisant une chaîne de connexion spécifiée par MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
