---
title: Méthode getAttributes (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getAttributes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4dc784ed-4699-4197-9af5-6e03da80d14c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 29376e0c88d7563fe66b3cf2afd54db2916624f6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920086"
---
# <a name="getattributes-method-sqlserverdatabasemetadata"></a>Méthode getAttributes (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description de l'attribut donné du type donné pour un type défini par l'utilisateur disponible dans le schéma et le catalogue donnés.  
  
> [!NOTE]  
>  Actuellement, cette méthode n’est pas prise en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Si elle est appelée, elle retourne toujours un jeu de résultats vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getAttributes(java.lang.String catalog,  
                                        java.lang.String schemaPattern,  
                                        java.lang.String typeNamePattern,  
                                        java.lang.String attributeNamePattern)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 **Chaîne** contenant le nom du catalogue.  
  
 *schemaPattern*  
  
 **Chaîne** contenant le modèle de nom du schéma.  
  
 *typeNamePattern*  
  
 **String** contenant le modèle du nom de type.  
  
 *attributePattern*  
  
 **Chaîne** contenant le modèle de nom de l’attribut.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getAttributes est spécifiée par la méthode getAttributes de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
