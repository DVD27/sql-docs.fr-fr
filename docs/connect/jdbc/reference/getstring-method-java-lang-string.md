---
title: Méthode getString (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f67371e0-e879-4188-85fc-ecb85f0be2a9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4ff58d1a2f58e044b49767f8fb2982b669a7b78
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979434"
---
# <a name="getstring-method-javalangstring"></a>Méthode getString (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que **chaîne** dans le langage de programmation Java en fonction du nom du paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getString(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur de **chaîne**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getString est spécifiée par la méthode getString de l’interface java.sql.CallableStatement.  
  
 Toutes les colonnes dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent être retournées en tant que chaîne. Cela signifie qu'une représentation de chaîne de tous les types à base de nombres et de caractères, et une représentation de chaîne hexadécimale des colonnes binaires telles que binary, varbinary, varbinary(max), image, timestamp et uniqueidentifier, peuvent être retournées.  
  
 Les types sensibles à l'emplacement tels que money, smallmoney, datetime, smalldatetime, float, real, decimal et numeric retourneront le format toString() canonique pour la valeur sous-jacente du type.  
  
 Les types définis par l'utilisateur sont retournés en tant que valeurs de chaînes hexadécimales.  
  
## <a name="see-also"></a>Voir aussi  
 [getString, méthode (SQLServerCallableStatement)](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
