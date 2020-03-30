---
title: GetLevel (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetLevel
- GetLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetLevel [Database Engine]
ms.assetid: 81577d7e-8ff6-4e73-b7f4-94c03d4921e7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f05c80a78417a8b5153345466eadcd49fa810228
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68077991"
---
# <a name="getlevel-database-engine"></a>GetLevel (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un entier qui représente la profondeur du nœud *this* dans l’arborescence.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
node.GetLevel ( )   
```  
  
```sql
-- CLR syntax  
SqlInt16 GetLevel ( )   
```  
  
## <a name="return-types"></a>Types de retour  
**Type de retour SQL Server : smallint**
  
**Type de retour CLR : SqlInt16**
  
## <a name="remarks"></a>Notes  
Sert à déterminer le niveau d'un ou plusieurs nœuds ou à filtrer les nœuds afin d'obtenir les membres d'un niveau spécifié. La racine de la hiérarchie est le niveau 0.
  
GetLevel est utile pour les index de recherche à largeur prioritaire. Pour plus d’informations, consultez [Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-hierarchy-level-as-a-column"></a>R. Retour du niveau hiérarchique en tant que colonne  
L’exemple suivant retourne une représentation textuelle du **hierarchyid**, puis le niveau hiérarchique en tant que colonne **EmpLevel** pour toutes les lignes de la table :
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo;  
```  
  
### <a name="b-returning-all-members-of-a-hierarchy-level"></a>B. Retour de tous les membres d'un niveau hiérarchique  
L'exemple suivant retourne toutes les lignes de la table au niveau hiérarchique 2 :
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 2;  
```  
  
### <a name="c-returning-the-root-of-the-hierarchy"></a>C. Retour de la racine de la hiérarchie  
L'exemple suivant retourne la racine du niveau hiérarchique :
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 0;  
```  
  
### <a name="d-clr-example"></a>D. Exemple CLR  
L’extrait de code suivant appelle la méthode GetLevel() :
  
```sql
this.GetLevel()  
```  
  
## <a name="see-also"></a>Voir aussi
[Référence de méthodes de type de données hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  