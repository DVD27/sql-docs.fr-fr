---
title: Procédures Refresh, exemple de méthode (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Refresh method [ADOX], Visual Basic example
ms.assetid: 499679bd-287b-487d-bdfb-3803abffec1c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9b5201be26bfd9df41c9cb1d8908f59499520878
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965374"
---
# <a name="procedures-refresh-method-example-vb"></a>Procedures, exemple de méthode Refresh (VB)
Le code suivant montre comment actualiser le [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md) collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md). Cela est nécessaire avant [procédure](../../../ado/reference/adox-api/procedure-object-adox.md) objets à partir de la **catalogue** sont accessibles.  
  
```  
' BeginProceduresRefreshVB  
Sub Main()  
    On Error GoTo ProcedureRefreshError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Refresh the Procedures collection  
    cat.Procedures.Refresh  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
ProcedureRefreshError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndProceduresRefreshVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Procedures, Collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
