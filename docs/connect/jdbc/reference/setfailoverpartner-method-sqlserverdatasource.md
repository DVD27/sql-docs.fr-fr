---
title: Méthode setFailoverPartner (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1d152001d1b0eb4ad47936d04ba6c74b8ae7f6e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974283"
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>Méthode setFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom du serveur de basculement utilisé dans une configuration de mise en miroir de bases de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *serverName*  
  
 **Chaîne** qui contient le nom du serveur de basculement.  
  
## <a name="remarks"></a>Notes  
 La valeur définie par cette méthode est utilisée en cas d'échec de connexion initiale avec le serveur principal ; une fois la connexion initiale établie, cette valeur est ignorée. La méthode [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) doit également être utilisée conjointement avec cette méthode ; sinon, une exception est levée.  
  
 Le pilote ne prend pas en charge la spécification du numéro de port du serveur de basculement lorsque le nom de ce serveur est défini. Cependant, l’appel des méthodes [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) et [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) avec la méthode [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) est pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
