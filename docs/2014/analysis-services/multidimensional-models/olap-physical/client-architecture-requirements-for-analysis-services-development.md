---
title: Exigences en matière d’architecture client pour le développement des services d’analyse (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- local mining models [Analysis Services]
- Analysis Services, architecture
- providers [Analysis Services]
- data pumps [Analysis Services]
- client architecture [Analysis Services]
- local cubes [Analysis Services]
ms.assetid: 03a8eb6b-159f-4a0a-afbe-06a2424b6090
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a69b2a2c8225c19dfb18a4b41b6fd1adc6aab266
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388024"
---
# <a name="client-architecture-requirements-for-analysis-services-development"></a>Spécifications relatives à l'architecture du client pour le développement d'Analysis Services
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge une architecture client [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mince. Le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] moteur de calcul est entièrement basé sur le serveur, de sorte que toutes les requêtes sont résolues sur le serveur. De ce fait, chaque requête n'exige qu'un seul aller-retour entre le client et le serveur, et les performances peuvent évoluer lorsque la complexité des requêtes augmente.

 Le protocole natif pour [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est XML for Analysis (XML/A). [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] fournit plusieurs interfaces d'accès aux données pour les applications clientes, mais tous ces composants communiquent avec une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l'aide de XML for Analysis.

 Plusieurs fournisseurs différents sont livrés avec [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour assurer la prise en charge de différents langages de programmation. Un fournisseur communique avec un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en envoyant du code XML/A dans des paquets SOAP sur TCP/IP ou sur HTTP à travers Internet Information Services (IIS). Une connexion HTTP utilise un objet COM instancié par les services IIS, appelé pompe de données (Data Pump), qui se comporte comme un tuyau pour les données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. La pompe de données n'examine pas du tout les données sous-jacentes contenues dans le flux HTTP, et le code de la bibliothèque de données lui-même ne permet d'accéder à aucune des structures de données sous-jacentes.

 ![Architecture de client logique pour Analysis Services](../../../analysis-services/dev-guide/media/as-clientarch9.gif "Architecture de client logique pour Analysis Services")

 Les applications clientes Win32 peuvent se connecter à un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l'aide des interfaces OLE DB pour OLAP ou du modèle d'objet de données Microsoft® ADO (ActiveX® Data Objects) pour les langages d'automation COM (Component Object Model) comme Microsoft Visual Basic®. Les applications écrites dans les langages .NET peuvent se connecter à un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l'aide des interfaces ADOMD.NET.

 Les applications existantes peuvent communiquer avec [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sans modification, simplement en utilisant l'un des fournisseurs [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].

|Langage de programmation|Interface d'accès aux données|
|--------------------------|---------------------------|
|C++|OLE DB pour OLAP|
|Visual Basic 6|ADO MD|
|Langages .NET|ADO MD.NET|
|Tout langage prenant en charge SOAP|XML for Analysis|

 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] possède une architecture Web dotée d'un niveau intermédiaire totalement évolutif qui permet son déploiement dans des organisations de toutes tailles. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] assure une vaste prise en charge de niveau intermédiaire pour les services Web. Les applications ASP sont prises en charge par OLE DB pour OLAP et ADO MD, les applications ASP.NET sont prises en charge par ADOMD.NET. Le niveau intermédiaire, illustré dans la figure suivante, peut évoluer pour s'adapter à plusieurs utilisateurs simultanés.

 ![Diagramme logique pour architecture intermédiaire](../../../analysis-services/dev-guide/media/as-midtierarch9.gif "Diagramme logique pour architecture intermédiaire")

 Les applications clientes et les applications de niveau intermédiaire peuvent communiquer directement avec [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], sans utiliser de fournisseur. Ces applications peuvent envoyer du code XML/A dans des paquets SOAP sur TCP/IP, HTTP ou HTTPS. Le client peut être écrit dans n'importe quel langage qui prend en charge SOAP. Les communications dans ce cas sont gérées le plus facilement par Internet Information Services (IIS) en utilisant le protocole HTTP, bien qu'une connexion directe au serveur utilisant TCP/IP puisse aussi être codée. Il s'agit de la solution de client la plus légère possible pour [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].

## <a name="analysis-services-in-tabular-or-sharepoint-mode"></a>Analysis Services en mode tabulaire ou SharePoint
 Dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le serveur peut être démarré en mode de moteur d'analyse en mémoire xVelocity (VertiPaq) pour les bases de données tabulaires et pour les classeurs [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] publiés sur un site SharePoint.

 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] et [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] sont les seuls environnements clients pris en charge pour la création et l'interrogation des bases de données en mémoire qui utilisent le mode SharePoint ou tabulaire, respectivement. La base de données PowerPivot intégrée [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] que vous créez en utilisant l’Excel et les outils est contenue dans le manuel Excel, et est enregistrée dans le cadre du fichier Excel .xlsx.

 Toutefois, un classeur [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] peut utiliser des données stockées dans un cube traditionnel si vous importez les données du cube dans le classeur. Vous pouvez également importer des données à partir d'un autre classeur [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] s'il a été publié sur un site SharePoint.

> [!NOTE]
>  Lorsque vous utilisez un cube comme une source de données pour un classeur [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)], les données que vous obtenez du cube sont définies comme une requête MDX ; toutefois, les données sont importées comme un instantané aplati. Vous ne pouvez pas utiliser les données en mode interactif ou actualiser les données du cube.

### <a name="interfaces-for-powerpivot-client"></a>Interfaces pour le client PowerPivot
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]interagit avec le moteur de stockage xVelocity in-memory analytics engine (VertiPaq) dans le cahier de travail en utilisant les interfaces et les langues établies pour les services d’analyse: AMO et ADOMD.NET, et MDX et XMLA. Dans le complément, les mesures sont définies en utilisant un langage de formule semblable à Excel, DAX (Data Analysis Expressions). Les expressions DAX sont incorporées dans les messages XMLA envoyés au serveur in-process.

### <a name="providers"></a>Fournisseurs
 Les [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] communications entre et Excel utilisent le fournisseur MSOLAP OLEDB (version 11.0). Dans le fournisseur MSOLAP, quatre modules différents ou transports peuvent être utilisés pour l'envoi de messages entre le client et serveur.

 **TCP/IP** Utilisé pour les connexions normales client-serveur.

 **HTTP (en)** Utilisé pour les connexions HTTP via le service de collecte de données SSAS, ou par un appel au composant SharePoint PowerPivot Web Service (WS).

 **INPROC (EN)** Utilisé pour les connexions au moteur en cours.

 **CANAL** Réservé aux communications avec le service système PowerPivot dans la ferme SharePoint.

## <a name="see-also"></a>Voir aussi
 [Composants serveur du moteur OLAP](olap-engine-server-components.md)


