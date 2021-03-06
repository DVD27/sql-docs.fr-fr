---
title: catalog.create_execution_dump | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 91319b0b-5536-4ab4-a403-9559ed9dd177
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 72b833d5e11e5a034001eca4cac698b5ef392930
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023509"
---
# <a name="catalogcreateexecutiondump"></a>catalog.create_execution_dump 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Provoque la suspension d'un package en cours d'exécution et la création d'un fichier de vidage par ce dernier. Le fichier est stocké dans le dossier *\<lecteur>* :\Program Files\Microsoft SQL Server\130\Shared\ErrorDumps.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.create_execution_dump [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id = ] *execution_id*  
 ID d'exécution du package en cours d'exécution. *execution_id* est de type **bigint**.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, le package en cours d'exécution dont l'ID d'exécution est 88 est invité à créer un fichier de vidage.  
  
```sql
EXEC create_execution_dump @execution_id = 88  
```  
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert que les utilisateurs soient membres du rôle de base de données **ssis_admin**.  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L'ID d'exécution spécifié n'est pas valide.  
  
-   Le package a déjà été exécuté.  
  
-   Le package crée actuellement un fichier de vidage.  
  
## <a name="see-also"></a>Voir aussi  
 [Générer de fichiers de vidage pour l’exécution des packages](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
