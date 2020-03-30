---
title: PERCENTILE_CONT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/20/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PERCENTILE_CONT_TSQL
- PERCENTILE_CONT
dev_langs:
- TSQL
helpviewer_keywords:
- analytic functions, PERCENTILE_CONT
- PERCENTILE_CONT function
ms.assetid: d019419e-5297-4994-97d5-e9c8fc61bbf4
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c5c52b80601f7b1e8e73cffe0a6cad255d91ff82
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "72172982"
---
# <a name="percentile_cont-transact-sql"></a>PERCENTILE_CONT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Calcule un percentile basé sur une distribution continue de la valeur de colonne dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le résultat est interpolé et peut ne pas être égale aux valeurs spécifiques de la colonne.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PERCENTILE_CONT ( numeric_literal )   
    WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_literal*  
 Percentile à calculer. Il doit être compris entre 0.0 et 1.0.  
  
 WITHIN GROUP **(** ORDER BY *order_by_expression* [ **ASC** | DESC ] **)**  
 Spécifie une liste de valeurs numériques à trier et sur lesquelles calculer le percentile. Un seul argument *order_by_expression* est autorisé. L’expression doit correspondre à un type numérique exact ou approximatif, sans aucun autre type de données autorisé. Les types numériques exacts sont **int**, **bigint**, **smallint**, **tinyint**, **numeric**, **bit**, **decimal**, **smallmoney** et **money**. Les types numériques approximatifs sont **float** et **real**. L’ordre de tri par défaut est croissant.  
  
 OVER **(** \<partition_by_clause> **)**  
 Divise le jeu de résultats généré par la clause FROM en partitions auxquelles la fonction percentile est appliquée. Pour plus d’informations, consultez [Clause OVER &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md). La \<clause ORDER BY> et la \<clause ROWS ou RANGE> de la syntaxe OVER ne peuvent pas être spécifiées dans une fonction PERCENTILE_CONT.  
  
## <a name="return-types"></a>Types de retour  
 **float(53)**  
  
## <a name="compatibility-support"></a>Prise en charge de la compatibilité  
 Lorsque le niveau de compatibilité est 110 et supérieur, WITHIN GROUP est un mot clé réservé. Pour plus d’informations, consultez [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Toutes les valeurs NULL dans le jeu de données sont ignorées.  
  
 PERCENTILE_CONT n'est pas déterministe. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-basic-syntax-example"></a>R. Exemple de syntaxe de base  
 L'exemple suivant utilise PERCENTILE_CONT et PERCENTILE_DISC pour rechercher le salaire moyen d'un employé dans chaque service. Ces fonctions peuvent ne pas retourner la même valeur. PERCENTILE_CONT interpole la valeur appropriée, qui peut exister ou non dans le jeu de données, alors que PERCENTILE_DISC retourne toujours une valeur réelle à partir du jeu.  
  
```  
USE AdventureWorks2012;  
  
SELECT DISTINCT Name AS DepartmentName  
      ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianCont  
      ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianDisc  
FROM HumanResources.Department AS d  
INNER JOIN HumanResources.EmployeeDepartmentHistory AS dh   
    ON dh.DepartmentID = d.DepartmentID  
INNER JOIN HumanResources.EmployeePayHistory AS ph  
    ON ph.BusinessEntityID = dh.BusinessEntityID  
WHERE dh.EndDate IS NULL;  
```  
  
 Voici un jeu de résultats partiel.  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.8269      16.8269
Engineering            34.375       32.6923
Executive              54.32695     48.5577
Human Resources        17.427850    16.5865
```  

### <a name="b-basic-syntax-example"></a>B. Exemple de syntaxe de base  
 L'exemple suivant utilise PERCENTILE_CONT et PERCENTILE_DISC pour rechercher le salaire moyen d'un employé dans chaque service. Ces fonctions peuvent ne pas retourner la même valeur. PERCENTILE_CONT interpole la valeur appropriée, qui peut exister ou non dans le jeu de données, alors que PERCENTILE_DISC retourne toujours une valeur réelle à partir du jeu.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT DepartmentName  
,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY BaseRate)  
    OVER (PARTITION BY DepartmentName) AS MedianCont  
,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY BaseRate)  
    OVER (PARTITION BY DepartmentName) AS MedianDisc  
FROM dbo.DimEmployee;  
  
```  
  
 Voici un jeu de résultats partiel.  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.826900    16.8269
Engineering            34.375000    32.6923
Human Resources        17.427850    16.5865
Shipping and Receiving 9.250000      9.0000
```  
  
## <a name="see-also"></a>Voir aussi  
 [PERCENTILE_DISC &#40;Transact-SQL&#41;](../../t-sql/functions/percentile-disc-transact-sql.md)  
  
 