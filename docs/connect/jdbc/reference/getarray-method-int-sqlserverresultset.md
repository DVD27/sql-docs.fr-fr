---
title: Méthode getArray (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getArray (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 377746c7-8c9c-41f5-8490-ca0dd56fd57a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff7355a5d63d5f6335612d2bf5de5131f23cab96
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954386"
---
# <a name="getarray-method-int-sqlserverresultset"></a>getArray, méthode (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de l’index de colonne désigné dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) sous forme d’objet Array.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Array getArray(int i)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *i*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 Un objet Array.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getArray est spécifiée par la méthode getArray de l’interfacejava.sql.ResultSet.  
  
## <a name="see-also"></a> Voir aussi  
 [Méthode getArray &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
