---
title: Fonctionnalités Integration Services prises en charge par les éditions de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 08a38e8a907c32a2614b3bda07a3153141b127d5
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893823"
---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>Fonctionnalités Integration Services prises en charge par les éditions de SQL Server

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


 Cette rubrique fournit des détails sur les fonctionnalités de SQL Server Integration Services (SSIS) prises en charge par les différentes éditions de [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

Pour connaître les fonctionnalités prises en charge par les éditions Evaluation et Developer, consultez les fonctionnalités répertoriées pour Enterprise Edition dans les tableaux suivants.
  
Pour obtenir les notes de publication les plus récentes et des informations sur les nouveautés, consultez les articles suivants :
-   [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Nouveautés d’Integration Services dans SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Nouveautés d’Integration Services dans SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**Essayez SQL Server 2016 !**    

La version d’évaluation de SQL Server est disponible pendant une période d’évaluation de 180 jours.  
    
> [![Télécharger à partir du Centre d’évaluation](https://docs.microsoft.com/analysis-services/analysis-services/media/download.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) **[Télécharger SQL Server 2016 à partir du Centre d’évaluation](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a> Nouvelles fonctionnalités Integration Services dans SQL Server 2017
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Scale Out Master|Oui|||||
|Scale Out Worker|Oui|Oui <sup>1</sup>|TBD|TBD|TBD|
|Prise en charge de Microsoft Dynamics AX et Microsoft Dynamics CRM dans les composants OData <sup>2</sup>|Oui|Oui||||

<sup>1</sup> Si vous exécutez des packages qui nécessitent des fonctionnalités Entreprise uniquement dans Scale Out, les Scale Out Workers doivent également s’exécuter sur des instances de SQL Server Entreprise.

<sup>2</sup> Cette fonctionnalité est également prise en charge dans SQL Server 2016 avec Service Pack 1.

## <a name="IEWiz"></a> Assistant Importation et Exportation SQL Server

|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Assistant Importation et Exportation SQL Server|Oui|Oui|Oui|Oui|Oui|  

## <a name="IS"></a> Integration Services  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Connecteurs de source de données intégrés|Oui|Oui|||| 
|Tâches et transformations intégrées|Oui|Oui||||  
|Source et destination ODBC |Oui|Oui|||| 
|Connecteurs et tâches de sources de données Azure|Oui|Oui||||  
|Connecteurs et tâches Hadoop/HDFS|Oui|Oui||||  
|Outils de profilage de données de base|Oui|Oui|||| 

## <a name="ISAA"></a> Integration Services - sources et destinations avancées  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Source et destination Oracle hautes performances par Attunity|Oui|||||  
|Source et destination hautes performances Teradata par Attunity|Oui|||||  
|Source et destination SAP BW|Oui|||||  
|Destination d’apprentissage du modèle d’exploration de données|Oui|||||  
|Destination de traitement de dimension|Oui|||||  
|Destination de traitement de partition|Oui|||||  
  
## <a name="ISAT"></a> Integration Services - Tâches et transformations avancées  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Composants de capture de données modifiées par Attunity <sup>1</sup>|Oui|||||  
|Transformation de requête d'exploration de données|Oui|||||  
|Transformations de regroupement probable et de recherche floue|Oui|||||  
|Transformations d’extraction de terme et de recherche de terme|Oui|||||  

<sup>1</sup> Les composants de capture de données modifiées par Attunity nécessitent l’édition Entreprise. Le service de capture de données modifiées et le concepteur de capture de données modifiées, toutefois, ne nécessitent pas l’édition Entreprise. Vous pouvez utiliser le concepteur et le service sur un ordinateur où SSIS n’est pas installé.
