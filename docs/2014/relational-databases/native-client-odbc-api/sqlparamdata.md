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
author: rothja
ms.author: jroth
ms.openlocfilehash: a4e0e8b31a65f28ce83e0d114231bdedd7a35a4c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021973"
---
# <a name="sqlparamdata"></a>SQLParamData
  Lorsque SQLParamData retourne le *ValuePtrPtr* associé à un paramètre table, l’application doit appeler SQLPutData avec *StrLen_Or_Ind*. Si *StrLen_Or_Ind* a une valeur supérieure à 0, cela signifie que l'application est prête et que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client peut collecter les données de paramètre pour la prochaine ligne de paramètre table. Si *StrLen_Or_Ind* a une valeur égale à 0, cela signifie qu'il n'y a plus de lignes de données pour le paramètre table. Pour plus d’informations, consultez [liaison et transfert de données des paramètres table et des valeurs de colonne](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
