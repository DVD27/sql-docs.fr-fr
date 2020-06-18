---
title: Éditeur de tâche de transfert de procédures stockées de Master (page procédures stockées) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 09a9ad4645f430418c39f76178bfe7a6757018dd
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972779"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>Éditeur de tâche de transfert de procédures stockées de master (page Procédures stockées)
  La page **Procédures stockées** de la boîte de dialogue **Éditeur de tâche de transfert de procédures stockées de master** permet de spécifier les propriétés de copie d’une ou plusieurs procédures stockées définies par l’utilisateur de la base de données **MASTER** d’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers une base de données **MASTER** d’une autre instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d'informations sur cette tâche, consultez [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Cette tâche transfère seulement les procédures stockées définies par l’utilisateur appartenant à **dbo** d’une base de données **MASTER** sur le serveur source vers une base de données **MASTER** sur le serveur de destination. Les utilisateurs doivent disposer de l’autorisation Créer une procédure dans la base de données **MASTER** du serveur de destination ou être membres du rôle serveur fixe **sysadmin** sur le serveur de destination pour y créer des procédures stockées.  
  
## <a name="options"></a>Options  
 **Abord SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<New connection...>** pour créer une nouvelle connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<New connection...>** pour créer une connexion au serveur de destination.  
  
 **IfObjectExists**  
 Sélectionnez la façon dont la tâche doit traiter les procédures stockées définies par l’utilisateur qui existent déjà sous le même nom dans la base de données **MASTER** du serveur de destination.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**FailTask**|La tâche échoue si des procédures stockées du même nom existent déjà dans la base de données **MASTER** du serveur de destination.|  
|**Remplacer**|La tâche remplace les procédures stockées du même nom dans la base de données **MASTER** du serveur de destination.|  
|**Ignorer**|La tâche ignore les procédures stockées qui existent sous le même nom dans la base de données **MASTER** du serveur de destination.|  
  
 **TransferAllStoredProcedures**  
 Indiquez si toutes les procédures stockées définies par l’utilisateur dans la base de données **MASTER** sur le serveur source doivent être copiées sur le serveur de destination.  
  
|Value|Description|  
|-----------|-----------------|  
|**:**|Copie toutes les procédures stockées définies par l’utilisateur dans la base de données **MASTER** .|  
|**Fausses**|Copie uniquement les procédures stockées spécifiées.|  
  
 **StoredProceduresList**  
 Sélectionnez les procédures stockées définies par l’utilisateur dans la base de données **MASTER** du serveur source qui doivent être copiées dans la base de données **MASTER** de destination. Cette option est disponible uniquement lorsque **TransferAllStoredProcedures** a la valeur **False**.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de procédures stockées de Master &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page expressions](expressions/expressions-page.md)   
 [Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)  
  
  
