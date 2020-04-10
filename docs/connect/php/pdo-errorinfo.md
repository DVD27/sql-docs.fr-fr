---
title: PDO::errorInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9d5481d5-13bc-4388-b3aa-78676c0fc709
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab46786bf62f7bd582aa09be562cc3db4183e5c2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919366"
---
# <a name="pdoerrorinfo"></a>PDO::ErrorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Récupère les informations d’erreur étendues de la dernière opération effectuée sur le handle de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array PDO::errorInfo();  
```  
  
## <a name="return-value"></a>Valeur de retour  
Tableau d’informations d’erreur sur la dernière opération effectuée sur le handle de base de données. Le tableau comprend les champs suivants :  
  
-   Le code d’erreur SQLSTATE  
  
-   Le code d’erreur propre au pilote  
  
-   Le message d’erreur propre au pilote  
  
En l’absence d’erreur, ou si la valeur SQLSTATE n’est pas définie, les champs propres au pilote ont la valeur Null.  
  
## <a name="remarks"></a>Notes  
PDO::ErrorInfo récupère uniquement les informations d’erreur pour les opérations exécutées directement sur la base de données. Utilisez PDOStatement::errorInfo quand vous créez une instance de PDOStatement à l’aide de PDO::prepare ou PDO::query.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
Dans cet exemple, le nom de la colonne est mal orthographié (`Cityx` au lieu de `City`), ce qui provoque une erreur qui est ensuite signalée.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
echo "\n";  
print_r ($conn->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDO, classe](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
