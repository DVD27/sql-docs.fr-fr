---
title: Méthode setNCharacterStream pour un objet Reader – long | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: af9a1ba8-7980-43fa-88e5-14f6cc5e897c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 73bd7fe7d3da0745f66e0a6d883d7024a318c95f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67973888"
---
# <a name="setncharacterstream-method-javalangstring-javaioreader-long"></a>Méthode setNCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Reader spécifié, qui correspond au nombre de caractères spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNCharacterStream(java.lang.String parameterName,  
                     java.io.Reader value,  
                     long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui indique le nom du paramètre.  
  
 *value*  
  
 Objet Reader.  
  
 *length*  
  
 **long** indiquant le nombre de caractères dans le flux.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setNCharacterStream est spécifiée par la méthode setNCharacterStream de l’interface java.sql.CallableStatement.  
  
 Cette méthode doit être utilisée pour les types de données **NCHAR**, **NVARCHAR**, **NTEXT** et **XML**.  
  
 Si la longueur du flux diffère de ce qui est spécifié dans le paramètre *length*, le pilote JDBC lève une exception lors de la mise à jour ou de l’insertion de la ligne.  
  
 Si la longueur du flux est inconnue, le paramètre *length* peut être défini sur -1 pour indiquer que le pilote doit accepter le flux, quelle que soit sa longueur. Avec sqljdbc4.jar, nous recommandons d’utiliser la méthode JDBC 4.0 [setNCharacterStream, méthode &#40;java.lang.String, java.io.Reader&#41;](../../../connect/jdbc/reference/setncharacterstream-method-java-lang-string-java-io-reader.md) quand l’application veut mettre à jour la colonne à partir d’un flux de longueur inconnue.  
  
## <a name="see-also"></a>Voir aussi  
 [setNCharacterStream, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
