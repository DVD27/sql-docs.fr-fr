---
title: xp_msver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_msver_TSQL
- xp_msver
dev_langs:
- TSQL
helpviewer_keywords:
- xp_msver
ms.assetid: 9264cf8c-92ba-45ad-b2d6-15d26d805a16
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b936f00f449bd57a7a00fa825910a809a1baf225
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898366"
---
# <a name="xpmsver-transact-sql"></a>xp_msver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations de version sur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **xp_msver** retourne également des informations sur le véritable numéro de build du serveur et des informations sur l’environnement de serveur. Les informations qui **xp_msver** retourne peut être utilisé au sein de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions, lots, procédures stockées et ainsi de suite, pour optimiser la logique pour le code indépendant de la plateforme.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_msver [ optname ]  
```  
  
## <a name="arguments"></a>Arguments  
 *optname*  
 Nom d'une option ; il peut s'agir de l'une des valeurs suivantes.  
  
|Option/Nom de colonne|Description|  
|-------------------------|-----------------|  
|**ProductName**|Nom du produit ; par exemple, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProductVersion**|Version du produit.|  
|**Langage**|Version linguistique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Plateforme**|Nom du système d'exploitation, du constructeur et de la famille de micro-processeurs pour l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Commentaires**|Informations diverses sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**CompanyName**|Nom de la société qui produit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; par exemple, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**FileDescription**|Système d'exploitation.|  
|**FileVersion**|Version de l'exécutable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**InternalName**|Nom interne à [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple, SQLSERVR.|  
|**LegalCopyright**|Informations légales de copyright requises pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; par exemple, Copyright © [!INCLUDE[msCoName](../../includes/msconame-md.md)] corp. 1988-2005.|  
|**LegalTrademarks**|Informations légales relatives à la marque déposée nécessaires pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, [!INCLUDE[msCoName](../../includes/msconame-md.md)] est une marque déposée de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**OriginalFilename**|Nom du fichier exécuté au démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple Sqlservr.exe.|  
|**PrivateBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SpecialBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Versionwindows**|Version de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows installée sur l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Vitesse du processeur**|Nombre de processeurs installés dans l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProcessorActiveMask**|Indique les processeurs installés dans l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et qui sont activés et utilisables par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|  
|**ProcessorType**|Type de processeur. Semblable à **plateforme**.|  
|**PhysicalMemory**|Quantité en mégaoctets (Mo) de mémoire vive (RAM) installée sur l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ID de produit**|PID (ID de produit). Ce numéro est spécifié au cours de l'installation. Il se trouve sur l'étiquette figurant sur un autocollant placé sur la pochette du CD original de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 1 (réussite)  
  
## <a name="result-sets"></a>Jeux de résultats  
 **xp_msver**, sans aucun paramètre, retourne un jeu de résultats en quatre colonnes qui répertorie toutes les valeurs d’option. **xp_msver**, pour n’importe quel paramètre, retourne le résultat de quatre colonnes définies avec les valeurs de cette option.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées étendues générales &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [@@VERSION &#40;Transact-SQL&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)  
  
  
