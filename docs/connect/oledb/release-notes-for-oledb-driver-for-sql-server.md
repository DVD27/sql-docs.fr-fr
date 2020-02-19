---
title: Notes de publication (OLE DB Driver pour SQL Server) | Microsoft Docs
ms.date: 10/11/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 23c730ce0bba9003b47b777108907763d981c551
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "74401532"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Notes de publication de Microsoft OLE DB Driver pour SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Cette page décrit ce qui a été ajouté dans chaque version de Microsoft OLE DB Driver pour SQL Server.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1830"></a>18.3.0

2 octobre 2019

### <a name="features-added"></a>Ajout de fonctionnalités

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge de l’authentification Azure Active Directory (`ActiveDirectoryInteractive`, `ActiveDirectoryMSI`). | [Utilisation d’Azure Active Directory](features/using-azure-active-directory.md). |
| Inclure la bibliothèque d’authentification Azure Active Directory (adal.dll) dans le programme d’installation | Maintenant incluse dans l’installation du pilote de base, cette opération met à niveau les installations existantes de la Bibliothèque d’authentification Microsoft Active Directory pour SQL Server, en les supprimant de la liste des applications installées dans Windows. |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Bogues corrigés

| Bogue corrigé | Détails |
| :-------- | :------ |
| Correction de la logique de suppression d’index dans [IIndexDefinition::DropIndex](https://go.microsoft.com/fwlink/?linkid=2106448). | Les versions précédentes du pilote OLE DB ne peuvent pas supprimer un index de clé primaire lorsque l’ID de schéma et l’ID d’utilisateur du propriétaire de l’index ne sont pas égaux. |
| &nbsp; | &nbsp; |

## <a name="1823"></a>18.2.3

Juin 2019

### <a name="features-added"></a>Ajout de fonctionnalités

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge des mises à niveau du pilote à partir du média amovible SQL Server. | Cette amélioration permet de mettre à niveau les pilotes directement à partir du média amovible SQL Server. |
| &nbsp; | &nbsp; |

## <a name="1822"></a>18.2.2

Mai 2019

### <a name="bugs-fixed"></a>Bogues corrigés

| Bogue corrigé | Détails |
| :-------- | :------ |
| Correction de l’authentification Azure Active Directory non interactive dans le multithread cloisonné (MTA). | OLE DB Driver 18.2.1 essaie de manière inappropriée de changer le modèle de concurrence COM sur un cloisonnement précédemment initialisé comme multithread (MTA). Par conséquent, dans une application qui effectue plusieurs appels à la suite à [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) ou [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) avant d’appeler l’interface [IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522), le pilote ne parvient pas à se connecter à l’aide des modes d’authentification Azure Active Directory. |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

Février 2019

### <a name="features-added"></a>Ajout de fonctionnalités

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge de l’encodage serveur UTF-8. | [Prise en charge d’UTF-8 dans OLE DB Driver pour SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Prise en charge de l’authentification Azure Active Directory. | [Utilisation d’Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

Juillet 2018

### <a name="features-added"></a>Ajout de fonctionnalités

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge du mot clé de chaîne de connexion `UseFMTONLY` et de la propriété d’initialisation `SSPROP_INIT_USEFMTONLY`. | `UseFMTONLY` contrôle la façon dont les métadonnées sont récupérées pendant la connexion à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions ultérieures.<br/><br/>Pour plus d'informations, consultez les pages suivantes : [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Bogues corrigés

| Bogue corrigé | Détails |
| :-------- | :------ |
| Correction d’une version incorrecte du fichier de format BCP. | OLE DB Driver 18.0 définit de manière inappropriée la version du fichier de format BCP sur 18.0 au lieu de 11.0.<br/>Les fichiers de format générés par OLE DB Driver 18.0 ne peuvent pas être lus par OLE DB Driver 18.1.<br/>Si vous devez utiliser des fichiers de format générés par la version précédente du pilote avec le nouveau pilote, vous pouvez modifier manuellement les fichiers pour remplacer la version par 11.0. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>Ajout de fonctionnalités

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge du mot clé de chaîne de connexion `MultiSubnetFailover` et de la propriété d’initialisation `SSPROP_INIT_MULTISUBNETFAILOVER`. | Pour plus d'informations, consultez les pages suivantes :<br/>&bull; &nbsp; [Prise en charge de la reprise d’activité et de la haute disponibilité par OLE DB Driver pour SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md),<br/>&bull; &nbsp; [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi

[Microsoft OLE DB Driver pour SQL Server](oledb-driver-for-sql-server.md)
