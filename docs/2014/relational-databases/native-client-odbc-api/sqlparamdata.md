---
title: SQLParamData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79285523ec83d3f10ad6f23010a7f9a6398e5980
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68890110"
---
# <a name="sqlparamdata"></a>SQLParamData
  Lorsque SQLParamData retourne le *ValuePtrPtr* associé à un paramètre table, l’application doit appeler SQLPutData avec *StrLen_Or_Ind*. Si *StrLen_Or_Ind* a une valeur supérieure à 0, cela signifie que l'application est prête et que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client peut collecter les données de paramètre pour la prochaine ligne de paramètre table. Si *StrLen_Or_Ind* a une valeur égale à 0, cela signifie qu'il n'y a plus de lignes de données pour le paramètre table. Pour plus d’informations, consultez [liaison et transfert de données des paramètres table et des valeurs de colonne](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
