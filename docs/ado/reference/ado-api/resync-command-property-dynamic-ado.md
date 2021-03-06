---
title: Resync Command, propriété dynamique (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e81fa9ffb28ba31f50d77cacf372bc24d09787ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917147"
---
# <a name="resync-command-property-dynamic-ado"></a>Resync Command, propriété dynamique (ADO)
Spécifie une commande fournie par l’utilisateur de chaîne qui le [Resync](../../../ado/reference/ado-api/resync-method.md) des problèmes de méthode pour actualiser les données dans la table nommée dans le [Unique Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) propriété dynamique.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur qui est une chaîne de commande.  
  
## <a name="remarks"></a>Notes  
 Le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet est le résultat d’une opération JOIN exécutée sur plusieurs tables de base. Les lignes affectées dépendent les *AffectRecords* paramètre de la [Resync](../../../ado/reference/ado-api/resync-method.md) (méthode). La norme **Resync** méthode est exécutée si la [Unique Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) et **Resync Command** propriétés ne sont pas définies.  
  
 La chaîne de commande de la **Resync Command** propriété est une commande paramétrée ou une procédure stockée qui identifie de façon unique la ligne en cours d’actualisation et retourne une seule ligne contenant le même nombre et le même ordre des colonnes en tant que la ligne soit actualisé. La chaîne de commande contient un paramètre pour chaque colonne de clé primaire dans le **Unique Table**; sinon, une erreur d’exécution est renvoyée. Les paramètres sont automatiquement renseignés avec les valeurs de clé primaire à partir de la ligne à actualiser.  
  
 Voici deux exemples basés sur SQL :  
  
 1\) le **Recordset** est défini par une commande :  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 Le **Resync Command** propriété est définie sur :  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 Le **Unique Table** est *commandes* et sa clé primaire, *OrderID*, est paramétrable. L’expression Sub-SELECT fournit un moyen simple de vous assurer par programmation que le même nombre et le même ordre des colonnes sont renvoyées par la commande d’origine.  
  
 2\) le **Recordset** est défini par une procédure stockée :  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 Le **Resync** méthode doit exécuter la procédure stockée suivante :  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 Le **Resync Command** propriété est définie sur :  
  
```  
"{call CustordersResync (?)}"  
```  
  
 Une fois encore, le **Unique Table** est *commandes* et sa clé primaire, *OrderID*, est paramétrable.  
  
 **Resync, commande** est une propriété dynamique ajoutée à la **Recordset** objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
