---
title: Ajouter et supprimer des articles dans une publication | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 1b713b0615ae13fc898567307f945176db8908d7
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769907"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication"></a>Ajouter et supprimer des articles dans une publication
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Ajoutez initialement des articles à une publication quand vous la créez dans l'Assistant Nouvelle Publication. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Créer une publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 Après la création d’une publication, vous pouvez ajouter et supprimer des articles sur la page **Articles** de la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Pour plus d’informations sur l’ajout et la suppression d’articles, consultez [Ajouter et supprimer des articles de publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a>Pour ajouter un article après la création d'une publication  
  
1.  Sur la page **Articles** de la boîte de dialogue **Propriétés de publication - \<Publication>** , décochez la case **Afficher uniquement les objets activés dans la liste**. Ceci vous permet de voir les objets non publiés de la base de données de publication.  
  
2.  Activez la case à cocher en regard des articles que vous voulez ajouter.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a>Pour supprimer un article  
  
1.  Sur la page **Articles** de la boîte de dialogue **Propriétés de publication - \<Publication>** , décochez la case en regard des articles à supprimer.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
