---
title: catalog.set_worker_agent_property (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 986807ab07a563fef1ae8a9231db194a4a5943e7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038668"
---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>catalog.set_worker_agent_property (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Définit la propriété d’un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker.

## <a name="syntax"></a>Syntaxe

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>Arguments
[@WorkerAgentId =] *WorkerAgentId*  
ID d’agent de Worker de Scale Out Worker. *WorkerAgentId* est de type **uniqueidentifier**.

[@PropertyName =] *PropertyName*  
Nom de la propriété. *PropertyName* est de type **nvarchar(256)** .

[@PropertyValue =] *PropertyValue*  
Valeur de la propriété. *PropertyValue* est de type **nvarchar(max)** .

## <a name="remarks"></a>Notes
Les noms de propriété valides sont **DisplayName**, **Description** et **Tags**.

## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  

## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**

## <a name="errors-and-warnings"></a>Erreurs et avertissements
  La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur n’a pas les autorisations appropriées 

-   L’ID d’agent de Worker n’est pas valide.

-   Le nom de la propriété n’est pas valide.

-   La valeur de propriété n’est pas valide.  
