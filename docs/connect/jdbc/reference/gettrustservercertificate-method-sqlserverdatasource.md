---
title: Méthode getTrustServerCertificate (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 81d07743dfefe0b0305b1a094a9ae4632d4effd9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978579"
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>Méthode getTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur **booléenne** qui indique si la propriété trustServerCertificate est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si trustServerCertificate est activé. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété trustServerCertificate est définie sur **true**, le certificat SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est automatiquement approuvé quand la couche de communication est chiffrée avec SSL. En d’autres termes, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne validera pas le certificat SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur par défaut est **false**.  
  
 Si la propriété trustServerCertificate est définie sur **false**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] validera le certificat SSL du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
