---
title: Développer et déployer des bases de données SQL Server pour Linux | Microsoft Docs
description: ''
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.openlocfilehash: b98980837f6dce2ebd9f39be142b816f37f16cd8
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68077405"
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Utiliser Visual Studio pour créer des bases de données pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Data Tools (SSDT) transforme Visual Studio en environnement de développement et de gestion du cycle de vie des bases de données puissant pour SQL Server sur Linux. Vous pouvez développer, créer, tester et publier votre base de données à partir d’un projet sous contrôle de code source, comme vous le feriez pour le code de votre application.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Installer Visual Studio et SQL Server Data Tools

1. Si vous n’avez pas encore installé Visual Studio sur votre ordinateur Windows, [Télécharger et installer Visual Studio]. Si vous n’avez pas de licence Visual Studio, Visual Studio Community Edition est un environnement de développement intégré (IDE) gratuit et complet pour les étudiants ainsi que les développeurs open source et individuels.

2. Pendant l’installation de Visual Studio, sélectionnez **Personnalisé** pour l’option **Choisir le type d’installation**. Cliquez sur **Suivant**.

3. Sélectionnez **Microsoft SQL Server Data Tools**, **Git pour Windows** et **Extension GitHub pour Visual Studio** dans la liste de sélection de fonctionnalités.

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Continuez et terminez l’installation de Visual Studio. Cela peut prendre quelques minutes.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>Mettre à niveau SQL Server Data Tools vers la version SSDT 17.0 RC

SQL Server sur Linux est pris en charge par SSDT version 17.0 RC ou ultérieure.

* [Télécharger et installer SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939).

## <a name="create-a-new-database-project-in-source-control"></a>Créer un nouveau projet de base de données dans le contrôle de code source

1. Lancez Visual Studio.

2. Sélectionnez **Team Explorer** dans le menu **Affichage**. 

3. Cliquez sur **Nouveau** dans la section **Référentiel Git local** sur la page **Connexion**.

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. Cliquez sur **Créer**. Une fois le référentiel Git local créé, double-cliquez sur **SSDTRepo**.

4. Cliquez sur **Nouveau** dans la section **Solutions**. Sélectionnez **SQL Server** sous le nœud **Autres langages** dans la boîte de dialogue **Nouveau projet**.

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. Tapez le nom **TutorialDB** et cliquez sur **OK** pour créer un nouveau projet de base de données.

## <a name="create-a-new-table-in-the-database-project"></a>Créez une table dans le projet de base de données

1. Sélectionnez **Explorateur de solutions** dans le menu **Affichage**.

2. Ouvrez le menu du projet de base de données en cliquant avec le bouton droit sur **TutorialDB** dans l’Explorateur de solutions.

3. Sélectionnez **Table** sous **Ajouter**.

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. À l’aide du concepteur de tables, ajoutez deux colonnes, Nom `nvarchar(50)` et Emplacement `nvarchar(50)`, comme le montre l’illustration. SSDT génère le script `CREATE TABLE` lorsque vous ajoutez les colonnes dans le concepteur.

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Enregistrez le fichier **Table1.sql**.

## <a name="build-and-validate-the-database"></a>Créer et valider la base de données

1. Ouvrez le menu du projet de base de données sur **TutorialDB** et sélectionnez **Créer**. SSDT compile les fichiers de code source .sql dans votre projet et génère un fichier de package d’application de la couche Données (dacpac). Cela peut être utilisé pour publier une base de données sur votre instance SQL Server sur Linux. 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Vérifiez la réussite de la création dans la fenêtre **Sortie** de Visual Studio. 

## <a name="publish-the-database-to-sql-server-instance-on-linux"></a>Publier la base de données sur l’instance SQL Server sur Linux

1. Ouvrez le menu du projet de base de données sur **TutorialDB** et sélectionnez **Publier**.

2. Cliquez sur **Modifier** pour sélectionner votre instance SQL Server sur Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. Dans la boîte de dialogue de connexion, tapez l’adresse IP ou le nom d’hôte de votre instance SQL Server sur Linux, le nom d’utilisateur et le mot de passe.

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Cliquez sur le bouton **Publier** dans la boîte de dialogue de publication.

5. Vérifiez le statut de publication dans la fenêtre **Opérations des outils de données**.

6. Cliquez sur **Afficher les résultats** ou sur **Afficher le script** pour voir des détails du résultat de la publication de la base de données sur votre instance SQL Server sur Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Vous avez créé avec succès une nouvelle base de données sur l’instance SQL Server sur Linux et appris les bases du développement d’une base de données avec un projet de base de données sous contrôle de code source.

## <a name="next-steps"></a>Étapes suivantes

Si vous débutez avec T-SQL, consultez le [Tutoriel : Écriture d’instructions Transact-SQL] et [Référence Transact-SQL (moteur de base de données)].

Pour plus d’informations sur le développement d’une base de données avec SQL Data Tools, consultez les [documents MSDN SSDT]

[Télécharger et installer Visual Studio]: https://www.visualstudio.com/downloads/
[Download and Install SSDT]:https://aka.ms/ssdt-download
[Documents MSDN SSDT]: https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx
[Tutoriel : Écriture d’instructions Transact-SQL]: https://msdn.microsoft.com/library/ms365303.aspx
[Référence Transact-SQL (moteur de base de données)]: https://msdn.microsoft.com/library/bb510741.aspx
