---
title: Gestionnaire de connexions SMTP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 948a7411c39191635245fdf0f6777538b1ef57fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62833086"
---
# <a name="smtp-connection-manager"></a>Gestionnaire de connexions SMTP
  Un gestionnaire de connexions SMTP permet à un package de se connecter à un serveur SMTP (Simple Mail Transfer Protocol). La tâche Envoyer un message incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise un gestionnaire de connexions SMTP.  
  
 Lorsque vous utilisez Microsoft Exchange comme serveur SMTP, vous pouvez être amené à configurer le gestionnaire de connexions SMTP de manière à utiliser l'authentification Windows. Les serveurs Exchange peuvent être configurés pour ne pas autoriser les connexions SMTP non authentifiées.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Configuration du gestionnaire de connexions SMTP  
 Lorsque vous ajoutez un gestionnaire de connexions SMTP à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion SMTP au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` du package. La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `SMTP`.  
  
 Vous pouvez configurer un gestionnaire de connexions SMTP de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion.  
  
-   Indiquez le nom d'un serveur SMTP.  
  
-   Spécifiez la méthode d'authentification à utiliser.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
-   Permet d'indiquer si les communications doivent être chiffrées à l'aide de SSL (Secure Sockets Layer) lors de l'envoi de messages électroniques.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions SMTP](../smtp-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
