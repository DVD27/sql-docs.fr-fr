---
title: Fonctions de copie en bloc | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2888f34c1e4c4103845d07e569a0dbabeb2e4caa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63225539"
---
# <a name="bulk-copy-functions"></a>Bulk Copy Functions
  L'extension API de copie en bloc du pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet aux applications clientes d'ajouter rapidement des lignes de données à une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'en extraire.  
  
 Lorsque vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, vous pouvez faire référence aux fonctions de copie en bloc (BCP) dans SQLNCLI11.LIB et SQLNCLI.H.  
  
 Toute application qui utilise une fonction API de copie en bloc (BCP) doit être liée à la bibliothèque (.lib) fournie avec le pilote (.dll) utilisé par l'application. Une application BCP ne doit pas être liée à plus d'une bibliothèque de pilote.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [bcp_batch](bcp-batch.md)  
  
-   [bcp_bind](bcp-bind.md)  
  
-   [bcp_colfmt](bcp-colfmt.md)  
  
-   [bcp_collen](bcp-collen.md)  
  
-   [bcp_colptr](bcp-colptr.md)  
  
-   [bcp_columns](bcp-columns.md)  
  
-   [bcp_control](bcp-control.md)  
  
-   [bcp_done](bcp-done.md)  
  
-   [bcp_exec](bcp-exec.md)  
  
-   [bcp_getcolfmt](bcp-getcolfmt.md)  
  
-   [bcp_gettypename](bcp-gettypename.md)  
  
-   [bcp_init](bcp-init.md)  
  
-   [bcp_moretext](bcp-moretext.md)  
  
-   [bcp_readfmt](bcp-readfmt.md)  
  
-   [bcp_sendrow](bcp-sendrow.md)  
  
-   [bcp_setbulkmode](bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](bcp-setcolfmt.md)  
  
-   [bcp_writefmt](bcp-writefmt.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions du pilote SQL Server](../../database-engine/dev-guide/sql-server-driver-extensions.md)   
 [Exécution d’opérations de copie en bloc &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
