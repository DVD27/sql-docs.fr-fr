---
title: LTRIM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LTRIM
- LTRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- leading blanks
- deleting blank spaces
- characters [SQL Server], blanks
- removing blank spaces
- LTRIM function
- blank characters [SQL Server]
ms.assetid: 369ed340-1a09-4597-a9eb-6720156cd39a
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0f3e52b291c9a91e1135d41ab6843ef97f53d17d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68130375"
---
# <a name="ltrim-transact-sql"></a>LTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une expression de caractères après la suppression de tous les espaces à gauche.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
LTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de données binaires ou caractères. *character_expression* peut être une constante, une variable ou une colonne. *character_expression* doit être d’un type de données, à l’exception de **text**, **ntext** et **image**, pouvant être implicitement converti en **varchar**. Sinon, utilisez la fonction [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) pour convertir explicitement *character_expression*.  
  
## <a name="return-type"></a>Type de retour  
 **varchar** ou **nvarchar**  
  
## <a name="examples"></a>Exemples  

### <a name="a-simple-example"></a>R. Exemple simple   

 L’exemple suivant utilise LTRIM pour supprimer les espaces de début d’une expression de caractères.  
  
```sql  
SELECT LTRIM('     Five spaces are at the beginning of this string.') FROM sys.databases;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ---------------------------------------------------------------  
  Five spaces are at the beginning of this string.
  ```  

### <a name="b-example-using-a-variable"></a>B. Exemple utilisant une variable   
  
 L'exemple suivant utilise `LTRIM` pour supprimer les espaces à droite d'une variable caractère.  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = '     5 spaces are at the beginning of this string.';  
SELECT 
    @string_to_trim AS 'Original string',
    LTRIM(@string_to_trim) AS 'Without spaces';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Original string Without spaces
--------------------------------------------------- ---------------------------------------------
     5 spaces are at the beginning of this string.  5 spaces are at the beginning of this string.
```  
  
## <a name="see-also"></a>Voir aussi  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


