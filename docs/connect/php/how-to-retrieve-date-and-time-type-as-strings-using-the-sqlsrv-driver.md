---
title: Récupérer des types date et heure sous forme de chaînes avec le pilote SQLSRV | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as strings
ms.assetid: 58a974ea-4daf-4e3b-98ed-9731b9c9250f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8c3fbd475d5f7038d36ba17a9578713c3ed1b53
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993531"
---
# <a name="how-to-retrieve-date-and-time-types-as-strings-using-the-sqlsrv-driver"></a>Procédure : récupérer des types date et heure sous forme de chaînes à l’aide du pilote SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Quand vous utilisez le pilote sqlsrv pour [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], vous pouvez récupérer des types de date et d’heure (**smalldatetime**, **DateTime**, **Date**, **Time**, **datetime2**et **DateTimeOffset**) sous forme de chaînes en spécifiant les éléments suivants: dans la chaîne de connexion ou au niveau de l’instruction:

```
'ReturnDatesAsStrings'=>true
```

La valeur par défaut est **false**, ce qui signifie que les types **smalldatetime**, **datetime**, **date**, **time**, **datetime2** et **datetimeoffset** sont retournés en tant qu’objets [PHP DateTime](http://php.net/manual/en/class.datetime.php). Si cette option est définie au niveau de l’instruction, elle remplace le paramètre de niveau de connexion.

Le pilote PDO_SQLSRV retourne des types de date et d’heure sous forme de chaînes par défaut. Pour les récupérer en tant qu’objets DateTime PHP, consultez [Comment: récupérer des types de date et d’heure en tant qu’objets php DateTime à l’aide de PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)

## <a name="example"></a>Exemple
L’exemple suivant montre la syntaxe permettant de récupérer des types de date et heure sous forme de chaînes.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks", 'ReturnDatesAsStrings '=> true);
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_close($conn);
?>
```

## <a name="example"></a>Exemple
L’exemple suivant montre que vous pouvez récupérer des dates sous forme de chaînes en spécifiant UTF-8 lors de la récupération de la chaîne, même quand la connexion a été établie avec `"ReturnDatesAsStrings" => false`.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks", "ReturnDatesAsStrings" => false);
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tsql = "SELECT VersionDate FROM AWBuildVersion";

$stmt = sqlsrv_query($conn, $tsql);

if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_fetch($stmt);

// retrieve date as string
$date = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STRING("UTF-8"));

if ($date === false) {
   die(print_r(sqlsrv_errors(), true));
}

echo $date;

sqlsrv_close($conn);
?>
```

## <a name="example"></a>Exemple
L’exemple suivant montre comment récupérer des dates sous forme de chaînes en spécifiant UTF-8 et `"ReturnDatesAsStrings" => true` dans la chaîne de connexion.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks", 'ReturnDatesAsStrings'=> true, "CharacterSet" => 'utf-8');
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tsql = "SELECT VersionDate FROM AWBuildVersion";

$stmt = sqlsrv_query($conn, $tsql);

if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_fetch($stmt);

// retrieve date as string
$date = sqlsrv_get_field($stmt, 0);

if ($date === false) {
   die(print_r(sqlsrv_errors(), true));
}

echo $date;
sqlsrv_close($conn);
?>
```

## <a name="example"></a>Exemple
L’exemple suivant montre comment récupérer la date sous la forme d’un type PHP. `'ReturnDatesAsStrings'=> false` est activé par défaut.

```php
<?php
$serverName = "MyServer";
$connectionInfo = array("Database"=>"AdventureWorks");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tsql = "SELECT VersionDate FROM AWBuildVersion";

$stmt = sqlsrv_query($conn, $tsql);

if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}

sqlsrv_fetch($stmt);

// retrieve date as a DateTime object, then convert to string using PHP's date_format function
$date = sqlsrv_get_field($stmt, 0);

if ($date === false) {
   die(print_r(sqlsrv_errors(), true));
}

$date_string = date_format($date, 'jS, F Y');
echo "Date = $date_string\n";

sqlsrv_close($conn);
?>
```

## <a name="example"></a>Exemple
L’option ReturnDatesAsStrings au niveau de l’instruction remplace l’option de connexion correspondante.

```php
<?php
$serverName = 'MyServer';
$connectionInfo = array('Database' => 'MyDatabase', 'ReturnDatesAsStrings' => false);
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
   echo "Could not connect.\n";
   die(print_r(sqlsrv_errors(), true));
}

$tableName = 'MyTable';
$options = array('ReturnDatesAsStrings' => true);
$query = "SELECT DateTimeCol FROM $tableName";
$stmt = sqlsrv_prepare($conn, $query, array(), $options);
if ($stmt === false) {
   echo "Error in statement preparation/execution.\n";
   die(print_r(sqlsrv_errors(), true));
}
sqlsrv_execute($stmt);

// Expect the fetched value to be a string
$field = sqlsrv_get_field($stmt, 0);
echo $field . PHP_EOL;

sqlsrv_close($conn);
?>
```

## <a name="see-also"></a>Voir aussi
[Récupération de données](../../connect/php/retrieving-data.md)

[Procédure : récupérer des types date et heure sous forme d’objets à l’aide de PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)
