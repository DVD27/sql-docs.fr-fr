---
title: Propriétés d’informations sur la Source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1a272a93d0148524da2def06fb8b4bbc121a9b0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128692"
---
# <a name="data-source-information-properties"></a>Propriétés des informations de la source de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Dans le jeu de propriétés DBPROPSET_SQLSERVERDATASOURCEINFO spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit les propriétés des informations de la source de données.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Tapez : VT_BOOL<br /><br /> R/W : Lecture<br /><br /> Par défaut : VARIANT_TRUE<br /><br /> Description : Utilisé pour déterminer si le classement de colonne est pris en charge.<br /><br /> VARIANT_TRUE : Classement au niveau des colonnes est pris en charge.<br /><br /> VARIANT_FALSE : Classement au niveau des colonnes n’est pas pris en charge.|  
|SSPROP_UNICODELCID|Tapez : VT_I4 R/W : Lecture<br /><br /> Description : ID de paramètres régionaux Unicode.<br /><br /> Il s'agit des paramètres régionaux utilisés pour le tri des données Unicode.|  
|SSPROP_UNICODECOMPARISONSTYLE|Tapez : VT_I4 R/W : Lecture<br /><br /> Description : Style de comparaison Unicode.<br /><br /> Options de tri utilisés pour le tri des données Unicode.|  
  
 Dans le jeu de propriétés DBPROPSET_SQLSERVERSTREAM spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit la propriété supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Tapez : VT_BSTR R/W : En lecture/écriture<br /><br /> Description : Le résultat d’une requête FOR XML ne peut pas être un document bien formé. Lorsque cette propriété est spécifiée, le résultat d'une requête 'select... for XML' est encapsulée dans la balise racine fournie par la propriété pour retourner un document XML bien formé. Si la requête est exécutée dans le navigateur, il se peut que le navigateur affiche les erreurs de l'analyseur lors du chargement du résultat. Pour éviter l'erreur, SQL ISAPI prend en charge le mot clé ROOT. Ce mot clé est mappé avec la propriété SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets Source de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
