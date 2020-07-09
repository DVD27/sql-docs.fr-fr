---
title: GetRoot (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetRoot
- GetRoot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetRoot [Database Engine]
ms.assetid: 240b70f1-eeda-44ab-b4bb-9e4af80fa7c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbc5bd95c10c89da4fb6fc6cbd1400f2e310927b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738201"
---
# <a name="getroot-database-engine"></a>GetRoot (moteur de base de données)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Retourne la racine de la structure hiérarchique. GetRoot() est une méthode statique.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
hierarchyid::GetRoot ( )   
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId GetRoot ( )   
```  
  
## <a name="return-types"></a>Types de retour  
**Type de retour SQL Server : hierarchyid**
  
**Type de retour CLR : SqlHierarchyId**
  
## <a name="remarks"></a>Notes  
Sert à déterminer le nœud racine dans une arborescence hiérarchique.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-transact-sql-example"></a>R. Exemple Transact-SQL  
L'exemple suivant retourne la racine de l'arborescence hiérarchique :
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = hierarchyid::GetRoot()  
```  
  
### <a name="b-clr-example"></a>B. Exemple CLR  
L’extrait de code suivant appelle la méthode GetRoot() :
  
```sql
SqlHierarchyId.GetRoot()  
```  
  
## <a name="see-also"></a>Voir aussi
[Référence de méthodes de type de données hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
