---
title: Répliquer les modifications de schéma | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84918dd3f50d129485911fc880e67c0152fa905c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882246"
---
# <a name="replicate-schema-changes"></a>Répliquer les modifications de schéma
  Cette rubrique explique comment répliquer les modification de schéma dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Si vous apportez les modifications de schéma suivantes à un article publié, elles sont propagées, par défaut, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aux abonnés :  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour répliquer des modifications de schéma à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   La commande ALTER TABLE... L’instruction DROP COLUMN est toujours répliquée vers tous les abonnés dont l’abonnement contient les colonnes supprimées, même si vous désactivez la réplication des modifications de schéma.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Si vous ne voulez pas répliquer des modifications de schéma pour une publication, désactivez la réplication des modifications de schéma dans la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-disable-replication-of-schema-changes"></a>Pour désactiver la réplication des modifications de schéma  
  
1.  Dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**, affectez à la propriété **Répliquer les modifications de schéma** la valeur **False**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Pour propager seulement des modifications de schéma spécifiques, définissez la propriété à **True** avant une modification de schéma, puis définissez-la à **False** après avoir effectué la modification. Inversement, pour propager la plupart des modifications de schéma mais pas une modification spécifique, définissez la propriété à **False** avant la modification de schéma, puis définissez-la à **True** après avoir effectué la modification.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez utiliser les procédures stockées de réplication pour spécifier si ces modifications de schéma sont répliquées. La procédure stockée que vous utilisez dépend du type de publication.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>Pour créer une publication transactionnelle ou d'instantané qui ne réplique pas les modifications du schéma  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), en spécifiant la valeur **0** pour ** \@replicate_ddl**. Pour plus d’informations, voir [Create a Publication](create-a-publication.md).  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>Pour créer une publication de fusion qui ne réplique pas les modifications du schéma  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), en spécifiant la valeur **0** pour ** \@replicate_ddl**. Pour plus d’informations, voir [Create a Publication](create-a-publication.md).  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>Pour désactiver temporairement la réplication des modifications du schéma pour une publication transactionnelle ou d'instantané  
  
1.  Pour une publication avec réplication des modifications de schéma, exécutez [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), en affectant la ** \@** valeur **replicate_ddl** à la propriété et la valeur **0** à ** \@la valeur**.  
  
2.  Exécutez la commande DDL sur l'objet publié.  
  
3.  Facultatif Réactivez la réplication des modifications de schéma en exécutant [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), en affectant la ** \@** valeur **replicate_ddl** à la propriété et la valeur **1** à ** \@la valeur**.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>Pour désactiver temporairement la réplication des modifications du schéma pour une publication de fusion  
  
1.  Pour une publication avec réplication des modifications de schéma, exécutez [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), en affectant la ** \@** valeur **replicate_ddl** à la propriété et la valeur **0** à ** \@la valeur**.  
  
2.  Exécutez la commande DDL sur l'objet publié.  
  
3.  Facultatif Réactivez la réplication des modifications de schéma en exécutant [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), en affectant la ** \@** valeur **replicate_ddl** à la propriété et la valeur **1** à ** \@la valeur**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier le schéma dans les bases de données de publication](make-schema-changes-on-publication-databases.md)   
 [Modifier le schéma dans les bases de données de publication](make-schema-changes-on-publication-databases.md)  
  
  
