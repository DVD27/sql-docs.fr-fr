---
title: Refresh, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a676bf5eb3d8d98f1b2eb9367aa8ad56f0da209d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931251"
---
# <a name="refresh-method-ado"></a>Refresh, méthode (ADO)
Met à jour les objets dans une collection afin de refléter les objets disponibles à partir d’et spécifiques au fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Notes  
 Le **Actualiser** méthode exécute différentes tâches en fonction de la collection à partir de laquelle vous l’appelez.  
  
### <a name="parameters"></a>Paramètres  
 À l’aide de la **Actualiser** méthode sur le [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet récupère les informations de paramètres côté fournisseur pour la procédure stockée ou requête paramétrable spécifié dans le **commande** objet. La collection sera vide pour les fournisseurs qui ne prennent pas en charge les appels de procédures stockées ou des requêtes paramétrables.  
  
 Vous devez définir le [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) propriété de la **commande** objet valide [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet, le [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété pour une commande valide et le [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) propriété **valeur adCmdStoredProc** avant d’appeler le **Actualiser** (méthode).  
  
 Si vous accédez à la **paramètres** collection avant d’appeler le **Actualiser** méthode, ADO automatiquement appelle la méthode et remplir la collection pour vous.  
  
> [!NOTE]
>  Si vous utilisez le **Actualiser** méthode pour obtenir des informations sur les paramètres du fournisseur d’et il retourne un ou plusieurs types de données de longueur variable [paramètre](../../../ado/reference/ado-api/parameter-object.md) ADO peut allouer de mémoire pour les paramètres en fonction des objets de leur taille maximale potentielle, ce qui provoque une erreur lors de l’exécution. Vous devez définir explicitement la [taille](../../../ado/reference/ado-api/size-property-ado-parameter.md) propriété de ces paramètres avant d’appeler le [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) méthode pour éviter les erreurs.  
  
### <a name="fields"></a>Champs  
 À l’aide de la **Actualiser** méthode sur le [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection n’a aucun effet visible. Pour récupérer les modifications de la structure de base de données sous-jacente, vous devez utiliser soit le [Requery](../../../ado/reference/ado-api/requery-method.md) méthode ou, si le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet ne prend pas en charge les signets, le [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)(méthode).  
  
### <a name="properties"></a>Properties  
 À l’aide de la **Actualiser** méthode sur un **propriétés** collection de certains objets remplit la collection avec les propriétés dynamiques exposées par le fournisseur. Ces propriétés fournissent des informations sur les fonctionnalités spécifiques au fournisseur, au-delà de la prend en charge ADO de propriétés intégrées.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Axes, Collection](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Collection de colonnes](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs, Collection](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Collection de dimensions](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Collection d’erreurs](../../../ado/reference/ado-api/errors-collection-ado.md)|[Collection de champs](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Collection de groupes](../../../ado/reference/adox-api/groups-collection-adox.md)|[Collection de hiérarchies](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes, Collection](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys, Collection](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels, Collection](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Collection de membres](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Collection de paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Collection de positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures, Collection](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Collection de propriétés](../../../ado/reference/ado-api/properties-collection-ado.md)|[Collection de tables](../../../ado/reference/adox-api/tables-collection-adox.md)|[Collection d’utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views, Collection](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Voir aussi  
 [Refresh, exemple de méthode (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Refresh, exemple de méthode (VC ++)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Refresh, méthode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
