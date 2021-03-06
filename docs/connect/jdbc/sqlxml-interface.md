---
title: Interface SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f235525e7a633bc0c49d39f8bec6bf4a79c0885d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006020"
---
# <a name="sqlxml-interface"></a>Interface SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote JDBC prend en charge l'API JDBC 4.0, ce qui permet l'introduction de l'interface java.sql.SQLXML. L’interface SQLXML définit des méthodes d’interaction et de manipulation des données XML. Le type de données **SQLXML** est mappé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]au type de données **XML** .  
  
L’interface SQLXML fournit des méthodes pour accéder à la valeur XML en tant que **chaîne**, **lecteur** ou **writer**, ou en tant que **flux**. La valeur XML est également accessible à l’aide de **Source** ou via la définition de **Result**, qui sont utilisés avec les API d’analyseurs XML tels que DOM (Document Object Model), SAX (Simple API for XML) et StAX (Streaming API for XML), ainsi que les transformations XSLT et XPath.  
  
## <a name="remarks"></a>Notes  

Le tableau suivant décrit les méthodes définies dans l'interface SQLXML :  
  
|Syntaxe de la méthode|Description de la méthode|  
|-------------------|------------------------|  
|[void free()](https://go.microsoft.com/fwlink/?LinkId=131685)|Cette méthode libère l'objet SQLXML ainsi que les ressources qu'il détient.|  
|[InputStream getBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131754)|Retourne un flux d'entrée pour la lecture des données de l'objet SQLXML.|  
|[Reader getCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131755)|Retourne les données **XML** en tant qu’objet java.io.Reader ou flux de caractères.|  
|[T étend la source t GetSource (\<classe t > sourceClass)](https://go.microsoft.com/fwlink/?LinkId=131756)|Retourne une **source** pour la lecture de la valeur **XML** spécifiée par cet objet **SQLXML** .<br /><br /> **Remarque :**  La méthode getSource prend en charge les sources suivantes : javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource et java.io.InputStream.|  
|[String getString()](https://go.microsoft.com/fwlink/?LinkId=131757)|Retourne une représentation sous forme de chaîne de la valeur **XML** désignée par cet objet SQLXML.|  
|[OutputStream setBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131758)|Récupère un flux qui permet d’écrire la valeur **XML** représentée par cet objet SQLXML.|  
|[Writer setCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131759)|Retourne un flux à utiliser pour écrire la valeur **XML** représentée par cet objet SQLXML.|  
|[T étend le résultat t SetResults (classe\<t > resultClass)](https://go.microsoft.com/fwlink/?LinkId=131760)|Retourne un **résultat** pour la définition de la valeur **XML** spécifiée par cet objet **SQLXML** .<br /><br /> **Remarque :** La méthode setResult prend en charge les sources suivantes : javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult et java.io.OutputStream.|  
|[void setString(String value)](https://go.microsoft.com/fwlink/?LinkId=131762)|Affecte la valeur XML désignée par cet objet SQLXML à la représentation **String** spécifiée.|  
  
Les applications ne peuvent lire et écrire des valeurs XML dans un objet SQLXML qu'une seule fois.  
  
Quand la méthode free() est appelée, l’objet SQLXML devient non valide et n’est plus accessible en lecture ni en écriture. Si l’application tente d’appeler sur cet objet SQLXML une autre méthode que free(), une exception est levée.  
  
L’objet SQLXML n’est ni lisible ni accessible en écriture lorsque l’application appelle l’une des méthodes getter suivantes: getSource, getCharacterStream, getBinaryStream et getString.  
  
L’objet SQLXML n’est ni accessible en écriture ni lisible lorsque l’application appelle l’une des méthodes setter suivantes: SetResult, setCharacterStream, setBinaryStream et setString.  
  
## <a name="see-also"></a>Voir aussi  

[Prise en charge des données XML](../../connect/jdbc/supporting-xml-data.md)  
