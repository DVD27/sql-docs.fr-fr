---
title: Méthode getColumnTypeName (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getColumnTypeName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a444da82-c1af-40a5-9774-02476416c92c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ff7fbebe710b9d52394b12bbd1524ff9785ba7e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952807"
---
# <a name="getcolumntypename-method-sqlserverresultsetmetadata"></a>Méthode getColumnTypeName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nom de type spécifique pour la base de données de la colonne désignée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getColumnTypeName(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **Entier** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 **Chaîne** contenant le nom du serveur pour la colonne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnTypeName est spécifiée par la méthode getColumnTypeName dans l’interface java. Sql. ResultSetMetaData.  
  
 Le comportement de [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 a changé pour la colonne TYPE_NAME. Pour plus d’informations, consultez [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
