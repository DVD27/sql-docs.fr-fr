---
title: Page d’accueil pour la programmation du client SQL | Microsoft Docs
description: Page Hub avec annoté liens vers des téléchargements et documentation de nombreuses combinaisons de langues et les systèmes d’exploitation, pour la connexion à SQL Server ou à la base de données SQL Azure.
author: MightyPen
ms.date: 11/07/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: v-daveng
ms.author: genemi
ms.openlocfilehash: d773e05a3ed953e5210c0ade3226b4a32e82aeab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63182209"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Page d’accueil pour la programmation client sur Microsoft SQL Server


Bienvenue dans notre page d’accueil sur la programmation pour interagir avec Microsoft SQL Server et base de données SQL Azure dans le cloud client. Cet article fournit les informations suivantes :

- Répertorie et décrit les combinaisons de langue et des pilotes disponibles.
    - Informations sont fournies pour les systèmes d’exploitation de Linux (Ubuntu et autres), MacOS et Windows.
- Fournit des liens vers la documentation détaillée pour chaque combinaison.
- Affiche les zones et les sous-zones de la documentation hiérarchique pour certaines langues, le cas échéant.


#### <a name="azure-sql-database"></a>Azure SQL Database

Dans n’importe quel langage donné, le code qui se connecte à SQL Server est presque identique au code pour la connexion à la base de données SQL Azure.

Pour plus d’informations sur les chaînes de connexion pour la connexion à la base de données SQL Azure, consultez :

- [Utiliser .NET Core (c#) pour interroger une base de données SQL Azure](/azure/sql-database/sql-database-connect-query-dotnet-core).
- Autres Azure SQL de base de données situés à proximité de l’article précédent dans la table des matières, sur les autres langues. Par exemple, consultez [utilisation de PHP pour interroger une base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Pages Web d’une application générée

Notre *une application générée* pages Web présentent des exemples de code, ainsi que des informations de configuration, dans un autre format. Pour plus d’informations, consultez plus loin dans cet article le [section intitulée *site Web d’une application générée*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Langages et les pilotes pour les programmes clients


Dans le tableau suivant, chaque image de la langue est un lien vers des détails sur l’utilisation de la langue avec SQL Server. Chaque lien accède à une section plus loin dans cet article.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![Logo c#][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![ORM Entity Framework, du .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Logo Java][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp; [![Logo de Node.js][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [ **`ODBC for C++`** ](#an-160-odbc-cpp-docu)<br/>[![cpp-big-plus][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![Logo PHP][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Logo Python][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Logo Ruby][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Télécharge et installe

L’article suivant est consacrée au téléchargement et installer des pilotes de connexion différentes de SQL pour une utilisation par les langages de programmation :

- [Pilotes SQL Server](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![Logo c#][image-ref-320-csharp] C# à l’aide d’ADO.NET

Les langages .NET gérés, tels que c# et Visual Basic, sont les utilisateurs courants d’ADO.NET. *ADO.NET* est un nom informel pour un sous-ensemble de classes .NET Framework.

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour se connecter à SQL à l’aide d’ADO.NET](./ado-net/step-3-proof-of-concept-connecting-to-sql-using-ado-net.md) | Un exemple de code petit axé sur la connexion et l’exécution de requêtes SQL Server. |
| [Connexion résiliente à SQL avec ADO.NET](./ado-net/step-4-connect-resiliently-to-sql-with-ado-net.md) | Un exemple de code, logique de nouvelle tentative, car les connexions peuvent parfois rencontrer des moments de la perte de connectivité.<br /><br />Logique de nouvelle tentative s’applique également aux connexions gérées via internet dans une base de données cloud, comme à la base de données SQL Azure. |
| [Base de données SQL Azure : Démonstration de comment utiliser .NET Core sur Windows/Linux/macOS pour créer un programme c#, pour vous connecter et interroger](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Exemple de base de données SQL Azure. |
| [Générer une application : C#, ADO.NET, Windows](https://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentation

|||
| :-- | :-- |
| [C# à l’aide d’ADO.NET](./ado-net/index.md)| Racine de notre documentation. |
| [Namespace : System.Data](https://docs.microsoft.com/dotnet/api/system.data) | Un ensemble de classes utilisées pour ADO.NET. |
| [Namespace: System.Data.SqlClient](https://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Le jeu de classes qui sont plus directement le centre de ADO.NET. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Logo Entity Framework][image-ref-333-ef] Entity Framework (EF) avec C&#x23;

Entity Framework (EF) fournit un mappage objet-relationnel (ORM). ORM facilite votre code source de programmation orientée objet (OOP) manipuler des données qui a été récupérées à partir d’une base de données relationnelle SQL.

EF a des relations directes ou indirectes avec les technologies suivantes :

- .NET Framework
- [LINQ to SQL](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/), ou [LINQ to Entities](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Améliorations de syntaxe du langage, tel que le **=>** opérateur en c#.
- Programmes pratique qui génèrent du code source pour les classes qui mappent aux tables de votre base de données SQL. Par exemple, [EdmGen.exe](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>EF d’origine et nouveau EF

Le [page de démarrage pour Entity Framework](https://docs.microsoft.com/ef/) introduit EF avec une description semblable à ce qui suit :

- Entity Framework est un mappeur objet-relationnel (ORM) qui permet aux développeurs .NET de travailler avec une base de données à l’aide d’objets .NET. Il élimine la nécessité pour la plupart du code source d’accès aux données que les développeurs doivent généralement écrire.

*Entity Framework* est un nom partagé par deux branches de code source distinct. Une branche d’EF est antérieure, et son code source peut maintenant être géré par le public. L’autres EF est une nouveauté. Le système deux EFs sont décrites ci-après :

|     |     |
| :-- | :-- |
| [EF 6.x](https://docs.microsoft.com/ef/ef6/) | Microsoft apparus EF août 2008. En mars 2015 Microsoft a annoncé EF 6.x était la version finale Microsoft développeriez. Microsoft a publié le code source dans le domaine public.<br /><br />Initialement, EF faisait partie de .NET Framework. Mais EF 6.x a peut-être été retiré de .NET Framework.<br /><br />[Code de source EF 6.x sur Github, dans le référentiel *aspnet/EntityFramework6*](https://github.com/aspnet/EntityFramework6) |
| [EF Core](https://docs.microsoft.com/ef/core/) | Microsoft a publié le EF Core qui vient d’être développée en juin 2016. EF Core est conçu pour une meilleure flexibilité et la portabilité. EF Core peut s’exécuter sur les systèmes d’exploitation au-delà de simplement Microsoft Windows. Et EF Core peut interagir avec les bases de données au-delà de simplement Microsoft SQL Server et d’autres bases de données relationnelles.<br /><br />**C&#x23; exemples de code :**<br />[Bien démarrer avec Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Bien démarrer avec EF Core sur .NET Framework avec une base de données existante](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

Entity Framework et les technologies associées sont puissantes et sont beaucoup à apprendre pour les développeurs désireux de maîtriser la zone entière.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Logo Java][image-ref-330-java] Java et JDBC

Microsoft fournit un pilote Java Database Connectivity (JDBC) pour une utilisation avec SQL Server (ou avec Azure SQL Database, bien sûr). Il s’agit d’un pilote JDBC de type 4 offrant une connectivité de base de données par le biais des interfaces de programmation d’applications (API) JDBC standard.

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Exemples de code](./jdbc/code-samples/index.md) | Exemples de code qui renseignent sur les types de données, les jeux de résultats et les données de grande taille. |
| [Exemple d’URL de connexion](./jdbc/connection-url-sample.md) | Décrit comment utiliser une URL de connexion pour se connecter à SQL Server. Ensuite, utilisez-le pour utiliser une instruction SQL pour récupérer des données. |
| [Exemple de source de données](./jdbc/data-source-sample.md) | Décrit comment utiliser une source de données pour se connecter à SQL Server. Utilisez ensuite une procédure stockée pour récupérer des données. |
| [Utiliser Java pour interroger une base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Exemple de base de données SQL Azure. |
| [Créer des applications Java à l’aide de SQL Server sur Ubuntu](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentation

La documentation de JDBC comprend les principales zones suivantes :

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Racine de notre documentation JDBC. |
| [Référence](./jdbc/reference/index.md) | Interfaces, classes et membres. |
| [Guide de programmation pour le pilote JDBC SQL](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Logo de Node.js][image-ref-340-node] Node.js

Node.js vous pouvez vous connecter à SQL Server à partir de Windows, Linux ou Mac. Est la racine de notre documentation Node.js [ici](./node-js/index.md).

Le pilote de connexion de Node.js pour SQL Server est implémenté dans JavaScript. Le pilote utilise le protocole TDS, qui est pris en charge par toutes les versions récentes de SQL Server. Le pilote est un projet open source, [disponible sur Github](https://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour se connecter à SQL à l’aide de Node.js](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Code pour la connexion à SQL Server et l’exécution d’une requête de source de programme simple. |
| [Base de données SQL Azure : utilisez Node.js pour la requête](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Exemple de base de données SQL Azure dans le cloud. |
| [Créer des applications Node.js pour utiliser SQL Server sur macOS](https://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC pour C++ 

![Logo d’ODBC][image-ref-350-odbc] ![cpp-big-plus][image-ref-322-cpp]

Connectivité de base de données ouverte (ODBC) a été développée dans les années 1990, et elle est antérieure à .NET Framework. ODBC est conçu pour être indépendamment de n’importe quel système de base de données particulière et du système d’exploitation.

Au fil des années, nombreux pilotes ODBC ont été créés et publiés par groupes au sein et en dehors de Microsoft. La plage des pilotes impliquent plusieurs langages de programmation client. La liste des cibles de données va bien au-delà de SQL Server.

D’autres pilotes de connectivité utilisent ODBC en interne.

#### <a name="code-example"></a>Exemple de code

- [Exemple de code C++, utilisant ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Plan de documentation

Le contenu d’ODBC dans cette section se concentre sur l’accès à SQL Server ou base de données SQL Azure, à partir de C++. Le tableau suivant répertorie un plan approximatif de la documentation principale pour ODBC.


| Domaine | Sous-zone | Description |
| :--- | :------ | :---------- |
| [ODBC pour C++](./odbc/index.md) | Racine de notre documentation. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Informations sur l’utilisation d’ODBC sur les systèmes d’exploitation Linux ou MacOS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Informations sur l’utilisation d’ODBC sur le système d’exploitation Windows. |
| [Administration](../odbc/admin/index.md) | &nbsp; | L’outil d’administration pour la gestion des sources de données ODBC. |
| [Microsoft](../odbc/microsoft/index.md)  | &nbsp; | Divers pilotes ODBC qui sont créés et fournis par Microsoft. |
| [Concepts et référence](../odbc/reference/index.md) | &nbsp; | Informations conceptuelles sur l’interface ODBC, outre référence traditionnel. |
| &nbsp; " | [Annexes](../odbc/reference/appendixes/index.md)    | Tables de la transition d’état, la bibliothèque de curseurs ODBC et bien plus encore. |
| &nbsp; " | [Développement d’application](../odbc/reference/develop-app/index.md)  | Fonctions, les poignées et bien plus encore. |
| &nbsp; " | [Développer des pilotes](../odbc/reference/develop-driver/index.md) | Comment développer votre propre pilote ODBC, si vous avez une source de données spécialisées. |
| &nbsp; " | [Installer](../odbc/reference/install/index.md) | Installation de ODBC, les sous-clés et bien plus encore. |
| &nbsp; " | [Syntaxe](../odbc/reference/syntax/index.md)   | API pour le programme d’installation, programme d’installation, traduction et accès aux données. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![Logo PHP][image-ref-360-php] PHP

Vous pouvez utiliser PHP pour interagir avec SQL Server. La racine de notre documentation de PHP est [ici](./php/index.md).

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour se connecter à SQL à l’aide de PHP](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Un exemple de code petit axé sur la connexion et l’exécution de requêtes SQL Server. |
| [Connexion résiliente à SQL avec PHP](./php/step-4-connect-resiliently-to-sql-with-php.md) | Un exemple de code, logique de nouvelle tentative, car les connexions via Internet et le cloud peuvent parfois rencontrer des moments de la perte de connectivité. |
| [Base de données SQL Azure : utilisez PHP pour la requête](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Exemple de base de données SQL Azure. |
| [Créer des applications PHP pour utiliser SQL Server sur RHEL](https://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Logo Python][image-ref-370-python] Python


Vous pouvez utiliser Python pour interagir avec SQL Server.

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour la connexion à SQL avec Python à l’aide de pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Un exemple de code petit axé sur la connexion et l’exécution de requêtes SQL Server. |
| [Base de données SQL Azure : utiliser Python pour la requête](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Exemple de base de données SQL Azure. |
| [Créer des applications PHP pour utiliser SQL Server sur SLES](https://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentation

| Domaine | Description |
| :--- | :---------- |
| [Python pour SQL Server](./python/index.md) | Racine de notre documentation. |
| [pymssql driver](./python/pymssql/index.md) | Microsoft ne gère pas ni ne testez le pilote pymssql.<br /><br />Le pilote de connexion pymssql est une interface simple pour les bases de données SQL, pour une utilisation dans les programmes de Python. Pymssql s’appuie sur FreeTDS pour fournir une interface de base de données-API Python (249 du point de terminaison PRIVILÉGIÉ) à Microsoft SQL Server. |
| [pilote pyodbc](./python/pyodbc/index.md)   | Le pilote de connexion pyodbc est un module Python open source qui facilite l’accès aux bases de données ODBC. Il implémente la spécification DB API 2.0, mais il est compressé avec encore plus de commodité proche du langage Python. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Logo Ruby][image-ref-380-ruby] Ruby

Vous pouvez utiliser Ruby pour interagir avec SQL Server. Est la racine de notre documentation Ruby [ici](./ruby/index.md).

#### <a name="code-examples"></a>Exemples de code

|||
| :-- | :-- |
| [Preuve de concept pour la connexion à SQL avec Ruby](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Un exemple de code petit axé sur la connexion et l’exécution de requêtes SQL Server. |
| [Base de données SQL Azure : utilisation de Ruby pour la requête](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Exemple de base de données SQL Azure. |
| [Créer des applications Ruby pour utiliser SQL Server sur MacOS](https://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Informations de configuration, ainsi que des exemples de code. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpswwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Site Web de générer une application, pour le développement de client SQL](https://www.microsoft.com/sql-server/developer-get-started/)


Sur notre [ *une application générée* ](https://www.microsoft.com/sql-server/developer-get-started/) vous pouvez choisir parmi une longue liste de langages pour se connecter à SQL Server de programmation de pages Web. Et votre programme client peut exécuter une multitude de systèmes d’exploitation.

*Une application générée* privilégie la simplicité et conformité pour le développeur qui est uniquement prise en main. Les étapes expliquent les tâches suivantes :

1. Comment installer Microsoft SQL Server
2. Comment télécharger et installer les pilotes et outils.
3. Comment effectuer toutes les configurations requises, comme il convient pour votre système d’exploitation choisi.
4. Guide pratique pour compiler le code source fourni.
5. Comment exécuter le programme.

Sont ensuite quelques contours approximatives du détail fourni sur le site Web :

#### <a name="java-on-ubuntu"></a>Java sur Ubuntu :

1. Configurer votre environnement
    - Étape 1.1 : installer SQL Server
    - Étape 1.2 installer Java
    - Étape 1.3 installer le Kit de développement Java (JDK)
    - Étape 1.4 installer Maven
2. Créer l’application Java avec SQL Server
    - Étape 2.1 créer une application Java qui se connecte à SQL Server et exécute des requêtes
    - Étape 2.2 créer une application Java qui se connecte à SQL Server à l’aide de l’infrastructure populaire mise en veille prolongée
3. Rendre votre application Java jusqu'à 100 fois plus rapide
    - Étape 3.1 créer une application Java afin d’illustrer les index Columnstore

#### <a name="python-on-windows"></a>Python sur Windows :

1. Configurer votre environnement
    - Étape 1.1 : installer SQL Server
    - Étape 1.2 installez Python
    - Étape 1.3 installer le pilote ODBC et l’utilitaire de ligne de commande SQL pour SQL Server
2. Créer l’application Python avec SQL Server
    - Étape 2.1 installer le pilote Python pour SQL Server
    - Étape 2.2 créer une base de données pour votre application
    - Étape 2.3 créer une application Python qui se connecte à SQL Server et exécute des requêtes
3. Rendre votre application Python jusqu'à 100 fois plus rapide
    - Étape 3.1 Création d’une nouvelle table avec 5 millions à l’aide de sqlcmd
    - Étape 3.2 créer une application Python qui interroge cette table et la durée des mesures
    - Étape 3.3 mesurer le temps nécessaire pour exécuter la requête
    - Étape 3.4, ajouter un index columnstore à votre table
    - Étape 3.5 mesurer le temps nécessaire pour exécuter la requête avec un index columnstore

Les captures d’écran suivantes vous donnent une idée de quoi ressemble notre site de documentation de développement SQL.

#### <a name="choose-a-language"></a>Choisir un langage :

![Site Web de développement de SQL, prise en main][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Choisissez un système d’exploitation :

![Site Web de développement de SQL, Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Autres développement


Cette section fournit des liens sur les autres options de développement. Ceux-ci incluent en général à l’aide de ces mêmes langues pour le développement Azure. Les informations au-delà de ciblage de base de données SQL Azure et de Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Hub de développement pour Azure

- [Hub de développement pour Azure](https://docs.microsoft.com/azure/)
- [Azure pour les développeurs .NET](https://docs.microsoft.com/dotnet/azure/)
- [Azure pour les développeurs Java](https://docs.microsoft.com/java/azure/)
- [Azure pour les développeurs Node.js](https://docs.microsoft.com/nodejs/azure/)
- [Azure pour développeurs Python](https://docs.microsoft.com/python/azure/)
- [Créer une application web PHP dans Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Autres langages

- [Créer des applications d’accéder à l’aide de SQL Server sur Windows](https://www.microsoft.com/sql-server/developer-get-started/go/windows/)



<!-- Image references. -->

[image-ref-322-cpp]: ./media/homepage-sql-connection-drivers/gm-cpp-4point-p61f.png
[image-ref-320-csharp]: ./media/homepage-sql-connection-drivers/gm-csharp-c10c.png
[image-ref-333-ef]: ./media/homepage-sql-connection-drivers/gm-entity-framework-ef20d.png
[image-ref-330-java]: ./media/homepage-sql-connection-drivers/gm-java-j18c.png
[image-ref-340-node]: ./media/homepage-sql-connection-drivers/gm-node-n30.png
[image-ref-350-odbc]: ./media/homepage-sql-connection-drivers/gm-odbc-ic55826-o35.png
[image-ref-360-php]: ./media/homepage-sql-connection-drivers/gm-php-php60.png
[image-ref-370-python]: ./media/homepage-sql-connection-drivers/gm-python-py72.png
[image-ref-380-ruby]: ./media/homepage-sql-connection-drivers/gm-ruby-un-r82.png
[image-ref-390-aka-ms-sqldev-choose-language]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-400-aka-ms-sqldev-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png

