---
title: Méthode getConnection () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f520e96-5313-468f-b987-535ddaea027e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 714ba26610aa27fbc05cb27156b293c13e58130d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923329"
---
# <a name="getconnection-method-"></a>Méthode getConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tente d’établir une connexion avec la source de données représentée par cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getConnection est spécifiée par la méthode getConnection de l’interface javax.sql.DataSource.  
  
## <a name="see-also"></a>Voir aussi  
 [getConnection, méthode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
