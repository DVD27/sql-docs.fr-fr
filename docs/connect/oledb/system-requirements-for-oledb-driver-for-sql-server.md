---
title: Configuration requise pour OLE DB Driver pour SQL Server | Microsoft Docs
description: Configuration requise pour OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- system requirements [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], system requirements
- OLE DB Driver for SQL Server, system requirements
- MSOLEDBSQL, system requirements
author: pmasl
ms.author: pelopes
ms.openlocfilehash: cec8b2aca53f64e7a3883dbccddce1a330c8a6e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993779"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Configuration requise pour OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Pour utiliser les fonctionnalités d'accès aux données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple MARS, les logiciels suivants doivent être installés :  

-   OLE DB pilote pour SQL Server sur votre client.  

-   Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur votre serveur.   

> [!NOTE]  
>  Assurez-vous que vous vous connectez avec les privilèges d'administrateur avant d'installer ce logiciel.  

## <a name="operating-system-requirements"></a>Système d'exploitation requis  
 Pour obtenir la liste des systèmes d’exploitation qui prennent en charge OLE DB pilote pour SQL Server, consultez [stratégies de support pour OLE DB pilote pour SQL Server](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md).  

 ## <a name="azure-active-directory-authentication-requirements"></a>Conditions d’authentification d’Azure Active Directory  
 Lorsque vous utilisez des méthodes d’authentification Azure Active Directory avec le pilote OLE DB, assurez-vous que le [bibliothèque d’Authentification Active Directory pour SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) a été installé. ADAL n’est pas requis pour les autres méthodes d’authentification ou les opérations de OLE DB.
Pour plus d’informations, consultez : [Utilisation d’Azure Active Directory](features/using-azure-active-directory.md).

## <a name="sql-server-requirements"></a>impératifs SQL Server  
 Pour utiliser OLE DB pilote pour SQL Server pour accéder aux données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les bases de données, vous devez disposer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’une instance de installée.  

 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] prend en charge les connexions à partir de toutes les versions de MDAC, de Windows Data Access Components, et de toutes les versions d’OLE DB Driver for SQL Server. Lorsqu'une version cliente plus ancienne se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les types de données de serveur inconnus du client sont mappés à des types compatibles avec la version du client. Pour plus d'informations, consultez [Compatibilité des types de données pour les versions du client](#data-type-compatibility-for-client-versions).  

## <a name="cross-language-requirements"></a>Configuration multilingue  
 La version anglaise du pilote OLE DB pour SQL Server est prise en charge sur toutes les versions localisées des systèmes d’exploitation pris en charge. Les versions localisées du pilote OLE DB pour les SQL Server sont prises en charge sur les systèmes d’exploitation localisés qui sont dans la même langue que le pilote OLE DB localisé pour SQL Server version. Les versions localisées d’OLE DB Driver for SQL Server sont également prises en charge sur les versions en anglais des systèmes d’exploitation pris en charge, sous réserve que les paramètres de langue correspondants soient installés.  

 Pour les mises à niveau :  

-   Les versions en anglais du pilote OLE DB pour SQL Server peuvent être mises à niveau vers n’importe quelle version localisée du pilote OLE DB pour SQL Server.  

-   Les versions localisées du pilote OLE DB pour SQL Server peuvent être mises à niveau vers des versions localisées de OLE DB pilote pour SQL Server de la même langue.  

-   La version localisée du pilote de OLE DB pour SQL Server peut être mise à niveau vers la version anglaise du pilote OLE DB pour SQL Server.  

-   Impossible de mettre à niveau les versions localisées du pilote OLE DB pour SQL Server vers le pilote OLE DB localisé pour les versions SQL Server d’une langue localisée différente.  

## <a name="data-type-compatibility-for-client-versions"></a>Compatibilité des types de données pour les versions du client  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et OLE DB Driver for SQL Server mappent les nouveaux types de données aux types de données plus anciens qui sont compatibles avec les clients de bas niveau, comme indiqué dans le tableau ci-dessous.  

 Les applications OLE DB et ADO peuvent utiliser le mot clé de chaîne de connexion **DataTypeCompatibility** avec OLE DB pilote pour SQL Server pour fonctionner avec des types de données plus anciens. Quand **DataTypeCompatibility=80**, les clients OLE DB se connectent à l’aide de la version TDS (Tabular Data Stream) de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] plutôt que de la version TDS. Cela signifie que pour [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les types de données ultérieurs, la conversion de bas niveau sera effectuée par le serveur et non par OLE DB Driver for SQL Server. Cela signifie également que les fonctionnalités disponibles sur la connexion seront limitées à l'ensemble de fonctionnalités de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Plutôt que d'essayer de transmettre des requêtes non valides au serveur, une détection des tentatives d'utilisation de nouveaux types de données ou fonctionnalités intervient dès que possible sur les appels d'API et les erreurs sont retournées à l'application appelante.   


 IDBInfo:: GetKeywords retourne toujours une liste de mots clés qui correspond à la version du serveur sur la connexion et n’est pas affectée par **DataTypeCompatibility**.  

|Type de données|SQL Server Native Client<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|OLE DB Driver pour SQL Server|Windows Data Access Components, MDAC et<br /><br /> Pilote OLE DB pour les applications SQL Server OLE DB avec DataTypeCompatibility = 80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8 Ko)|udt|udt|udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|varchar|Texte|  
|nvarchar(max)|NVARCHAR|NVARCHAR|NVARCHAR|Ntext|  
|xml|xml|xml|xml|Ntext|  
|CLR UDT (> 8 Ko)|varbinary|udt|udt|image|  
|Date|varchar|Date|Date|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>Voir aussi  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)   
 [Installation d’OLE DB Driver pour SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
