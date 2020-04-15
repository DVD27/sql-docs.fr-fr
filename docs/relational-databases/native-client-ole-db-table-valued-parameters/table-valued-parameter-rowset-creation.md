---
title: Création d'un ensemble de lignes de paramètre table | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
ms.assetid: ffe213ca-cc0e-465e-b31c-a8272324c4fe
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab3541f354af26f32f4071c2a6d09648cd53af6d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283084"
---
# <a name="table-valued-parameter-rowset-creation"></a>Création d'un ensemble de lignes de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bien que les consommateurs puissent fournir n'importe quel objet d'ensemble de lignes pour les paramètres table, les objets d'ensemble de lignes communs sont implémentés dans des banques de données principales, ce qui limite leurs performances. C'est pourquoi le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client permet aux consommateurs de créer un objet d'ensemble de lignes spécialisé par-dessus les données en mémoire. Cet objet encastré spécial est un nouvel objet COM appelé un paramètre de table. Il fournit des fonctionnalités similaires aux jeux de paramètres.  
  
 Les objets d'ensemble de lignes de paramètre table sont créés explicitement par le consommateur pour les paramètres d'entrée via plusieurs interfaces de niveau session. Il existe une instance d'un objet d'ensemble de lignes de paramètre table par paramètre table. Le consommateur peut créer les objets d'ensemble de lignes de paramètre table soit en fournissant des informations de métadonnées qui sont déjà connues (scénario statique), soit en révélant ces informations par le biais des interfaces du fournisseur (scénario dynamique). Les sections qui suivent décrivent ces deux scénarios :  
  
## <a name="static-scenario"></a>Scénario statique  
 Lorsque les informations de type sont connues, le consommateur utilise ITableDefinitionWithConstraints::CreateTableWithConstraints pour instancier un objet d'ensemble de lignes de paramètre table qui correspond à un paramètre table.  
  
 Le champ *guid* (paramètre *pTableID*) contient le GUID spécial (CLSID_ROWSET_TVP). Le membre *pwszName* contient le nom du type de paramètre table que le consommateur souhaite instancier. Le champ *eKind* sera défini sur DBKIND_GUID_NAME. Ce nom est requis lorsque l'instruction est une instruction SQL ad hoc ; le nom est facultatif s'il s'agit d'un appel de procédure.  
  
 Pour l'agrégation, le consommateur passe le paramètre *pUnkOuter* avec l'IUnknown de contrôle.  
  
 Les propriétés d’objets encastrement de paramètres de table sont lues seulement, de sorte que le consommateur ne devrait pas définir de propriétés dans *rgPropertySets*.  
  
 Pour le membre *rgPropertySets* de chaque structure DBCOLUMNDESC, le consommateur peut spécifier des propriétés supplémentaires pour chaque colonne. Ces propriétés appartiennent au jeu de propriétés DBPROPSET_SQLSERVERCOLUMN. Elles vous permettent de spécifier les paramètres calculés et les paramètres par défaut de chaque colonne. Elles prennent également en charge les propriétés de colonnes existantes, telles que la possibilité de valeur Null et l'identité.  
  
 Pour récupérer les informations correspondantes d’un objet d’ensemble de lignes de paramètre table, le consommateur utilise IRowsetInfo::GetProperties.  
  
 Pour récupérer des informations sur l’état nul, unique, calculé et mis à jour de chaque colonne, le consommateur utilise IColumnsRowset::GetColumnsRowset ou IColumnsInfo::GetColumnInfo. Ces méthodes fournissent des informations détaillées sur chaque colonne de l'ensemble de lignes du paramètre table.  
  
 Le consommateur spécifie le type de chaque colonne du paramètre table. Cela est identique à la spécification de colonnes lors de la création d'une table dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le consommateur obtient un objet en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de paramètres de valeur de table auprès du fournisseur de DB OLE du client autochtone par l’intermédiaire du paramètre de sortie *ppRowset.*  
  
## <a name="dynamic-scenario"></a>Scénario Dynamique  
 Lorsque le consommateur n’a pas d’informations de type, il doit utiliser IOpenRowset::OpenRowset pour instantanéiser les objets encastrés paramètres de table. Tout ce que le consommateur doit fournir au fournisseur est le nom du type.  
  
 Dans ce scénario, le fournisseur obtient les informations de type d'un objet d'ensemble de lignes de paramètre table à partir du serveur au nom du consommateur.  
  
 Les paramètres *pTableID* et *pUnkOuter* doivent être définis comme dans le scénario statique. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE du client autochtone obtient alors les informations de type (informations et contraintes de colonne) du serveur, et renvoie un objet en ligne de paramètres évalué par table par le paramètre *ppRowset.* Cette opération requiert une communication avec le serveur, et par conséquent ne fonctionne pas aussi bien que le scénario statique. Le scénario dynamique fonctionne uniquement avec des appels de procédure paramétrables.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres évalués par la table &#40;&#41;OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
