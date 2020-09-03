---
title: Accès aux données
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 78d950b777d866835ef516c4910180b21de295e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545000"
---
# <a name="accessing-data-in-visual-studio"></a>Accès aux données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez créer des applications qui se connectent à des données dans pratiquement n’importe quel produit ou service de base de données, dans n’importe quel format, en tout lieu, sur un ordinateur local, sur un réseau local, ou dans un cloud public, privé ou hybride.

 Pour les applications en JavaScript, Python, PHP, Ruby ou C++, vous vous connectez à des données comme vous le feriez autre chose, en obtenant des bibliothèques et en écrivant du code. Pour les applications .NET, Visual Studio fournit des outils que vous pouvez utiliser pour explorer des sources de données, créer des modèles objet pour stocker et manipuler des données en mémoire, et lier des données à l’interface utilisateur.     Microsoft Azure fournit des kits de développement logiciel (SDK) pour .NET, Java, Node.js, PHP, Python, Ruby et Mobile Apps, ainsi que des outils dans Visual Studio pour la connexion au stockage Azure.

 Les listes suivantes présentent quelques-uns des nombreux systèmes de stockage et de base de données qui peuvent être utilisés à partir de Visual Studio. Les offres de [Microsoft Azure](https://azure.microsoft.com/) sont des services de données qui incluent l’approvisionnement et l’administration du magasin de données sous-jacent.  [Azure Tools pour Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) est un composant facultatif qui vous permet d’utiliser des magasins de données Azure directement à partir de Visual Studio. La plupart des autres produits de base de données SQL et NoSQL répertoriés ici peuvent être hébergés sur un ordinateur local, sur un réseau local ou dans Microsoft Azure sur un ordinateur virtuel. Dans ce scénario, vous êtes responsable de la gestion de la base de données elle-même.

 **Microsoft Azure**

- SQL Database

- Base de données de documents

-Stockage (objets BLOB, tables, files d’attente, fichiers)

- SQL Data Warehouse

- SQL Server Stretch Database

- StorSimple

 Et bien plus...

 **SQL**

- SQL Server 2005 – 2016, y compris Express et la base de données locale
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite

 Et bien plus...

 **NoSQL**

- Apache cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB
- RavenDB
- VelocityDB

 Et bien plus...

 De nombreux fournisseurs de bases de données et tiers prennent en charge l’intégration de Visual Studio par les packages NuGet. Vous pouvez explorer les offres sur NuGet.org ou par le biais du gestionnaire de package NuGet dans Visual Studio (**Outils**  >  **Gestionnaire de package NuGet**  >  **gérer les packages NuGet pour la solution**). D’autres produits de base de données s’intègrent à Visual Studio en tant qu’extension.   Vous pouvez parcourir ces offres dans la Galerie Visual Studio en accédant à **Outils**  >  **extensions et mises à jour** , puis en sélectionnant **en ligne** dans le volet gauche de la boîte de dialogue.  Pour plus d’informations, consultez [installation de systèmes de base de données, d’outils et d’exemples](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Le support étendu pour SQL Server 2005 a pris fin le 12 avril 2016.   Il n’existe aucune garantie que les outils de données dans Visual Studio 2015 et versions ultérieures continuent de fonctionner avec SQL Server 2005 après cette date. Pour plus d’informations, consultez l' [annonce de fin de support pour SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Langages .NET
 Tous les accès aux données .NET, y compris dans .NET Core, sont basés sur ADO.NET, un ensemble de classes qui définit une interface pour accéder à n’importe quel type de source de données, à la fois relationnelles et non relationnelles. Visual Studio propose plusieurs outils et concepteurs qui fonctionnent avec ADO.NET pour vous aider à vous connecter aux bases de données, à manipuler les données et à présenter les données à l’utilisateur. La documentation de cette section décrit comment utiliser ces outils. Vous pouvez également programmer directement par rapport aux objets de commande ADO.NET. Pour plus d’informations sur l’appel direct des API ADO.NET, consultez [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) dans MSDN Library.

 Pour obtenir une documentation sur l’accès aux données spécifiquement liée à ASP.NET, consultez  [utilisation des données](/aspnet/web-forms/overview/presenting-and-managing-data/) sur le site ASP.net. Pour obtenir un didacticiel sur l’utilisation de Entity Framework avec ASP.NET MVC, consultez [prise en main avec Entity Framework 6 Code First à l’aide de MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Les applications plateforme Windows universelle (UWP) en C# ou Visual Basic peuvent utiliser le kit de développement logiciel Microsoft Azure SDK pour .NET pour accéder à Azure Storage et à d’autres services Azure. La classe Windows. Web. HttpClient permet la communication avec n’importe quel service RESTful. Pour plus d’informations, consultez [Comment se connecter à un serveur http à l’aide de Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Pour le stockage de données sur l’ordinateur local, l’approche recommandée consiste à utiliser SQLite, qui s’exécute dans le même processus que l’application. Si une couche de mappage objet-relationnel (ORM) est requise, vous pouvez utiliser Entity Framework. Pour plus d’informations, consultez [accès aux données](https://msdn.microsoft.com/windows/uwp/data-access/index) dans le centre de développement Windows.

 Si vous vous connectez aux services Azure, veillez à télécharger les derniers [outils du kit de développement logiciel (SDK) Azure](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Fournisseurs de données
 Pour qu’une base de données soit consommable dans ADO.NET, elle doit avoir un *fournisseur de données ADO.net* personnalisé ou doit exposer une interface ODBC ou OLE DB. Microsoft fournit une [liste de fournisseurs de données ADO.net](https://msdn.microsoft.com/data/dd363565) pour les produits SQL Server, ainsi que les fournisseurs ODBC et OLE DB.

#### <a name="data-modeling"></a>Modélisation de données
 Dans .NET, vous avez trois possibilités de modélisation et de manipulation des données en mémoire après les avoir récupérées d’une source de données :

 Entity Framework la technologie Microsoft ORM préférée. Vous pouvez l’utiliser pour programmer des données relationnelles en tant qu’objets .NET de première classe. Pour les nouvelles applications, il doit s’agir du premier choix par défaut lorsqu’un modèle est requis. Elle nécessite une prise en charge personnalisée du fournisseur ADO.NET sous-jacent.

 LINQ to SQL un mappeur relationnel objet d’une génération antérieure. Elle fonctionne bien pour les scénarios moins complexes, mais n’est plus en cours de développement.

 Datasets est le plus ancien des trois technologies de modélisation. Il est principalement conçu pour le développement rapide d’applications de « formulaires de données » dans lesquelles vous ne traitez pas d’énormes quantités de données ou effectuez des requêtes ou des transformations complexes. Un objet DataSet se compose d’objets DataTable et DataRow qui ressemblent logiquement à des objets de base de données SQL, bien plus que des objets .NET. Pour les applications relativement simples basées sur les sources de données SQL, les jeux de données peuvent toujours être un bon choix.

 Il n’est pas nécessaire d’utiliser ces technologies. Dans certains scénarios, en particulier lorsque les performances sont critiques, vous pouvez simplement utiliser un objet DataReader pour lire la base de données et copier les valeurs dont vous avez besoin dans un objet de collection tel que List \<T> .

### <a name="native-c"></a>C++ natif
 Les applications C++ qui se connectent à SQL Server doivent utiliser l' [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Vous pouvez accéder à d’autres bases de données à l’aide de pilotes [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou OLE DB directement. ODBC est l’interface de base de données standard actuelle, mais la plupart des systèmes de base de données fournissent des fonctionnalités personnalisées qui ne sont pas accessibles par le biais de l’interface ODBC.  OLE DB est une technologie héritée d’accès aux données COM qui est toujours prise en charge mais non recommandée pour les nouvelles applications.  Pour plus d’informations, consultez [accès aux données](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 Les programmes c++ qui utilisent les services REST peuvent utiliser le [Kit de développement logiciel (SDK) Rest c++](https://github.com/Microsoft/cpprestsdk).

 Les programmes C++ qui fonctionnent avec Stockage Microsoft Azure peuvent utiliser le [Client stockage Microsoft Azure](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modélisation de données
 Visual Studio ne fournit pas de couche ORM pour C++.  [ODB](https://www.codesynthesis.com/products/odb/) est un ORM Open source populaire pour C++.

 Pour plus d’informations sur les technologies d’accès aux données héritées Visual C++, consultez  [accès aux données](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript dans Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) est un langage de premier ordre pour la création d’applications multiplateformes, d’applications UWP, de services Cloud, de sites Web et d’applications Web. Vous pouvez utiliser Bower, Grunt, Gulp, NPM et NuGet à partir de Visual Studio pour installer vos bibliothèques et vos produits de base de données JavaScript préférés. Connectez-vous à Azure Storage et aux services en téléchargeant les kits de développement logiciel à partir du [site Web Azure](https://azure.microsoft.com/).  Edge.js est une bibliothèque qui connecte le JavaScript côté serveur (Node.js) à des sources de données ADO.NET.

### <a name="python"></a>Python
 Installez  [python Tools pour Visual Studio](http://microsoft.github.io/PTVS/) avec votre infrastructure python favorite pour créer des applications CPython ou IronPython (.net).  Le site Web Python Tools pour Visual Studio propose plusieurs didacticiels sur la connexion aux données, notamment [Django et SQL Database sur Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django et MySQL sur Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) et [bouteille et MongoDB sur Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>Contenu de cette section
 [Installation des systèmes de base de données, des outils et des exemples](../data-tools/installing-database-systems-tools-and-samples.md) Explique comment obtenir des produits de base de données et les extensions ou pilotes Visual Studio qui les prennent en charge, et où trouver des exemples de bases de données à des fins d’expérimentation et d’apprentissage.

 [Outils de données Visual Studio pour .net](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Décrit comment utiliser les fenêtres Outil Visual Studio pour se connecter à des sources de données, créer des jeux de données ou des modèles de Entity Framework, et lier les données aux contrôles d’interface utilisateur.

## <a name="related-topics"></a>Rubriques connexes
 [Données, appareils et analytiques](https://msdn.microsoft.com/data-and-devices) Fournit une présentation du Cloud intelligent Microsoft, y compris Cortana Analytics suite et la prise en charge de Internet des objets.

 [Stockage Microsoft Azure](/azure/storage/) Décrit le stockage Azure et comment créer des applications à l’aide d’objets BLOB, de tables, de files d’attente et de fichiers Azure.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) Décrit comment se connecter à Azure SQL Database, une base de données relationnelle en tant que service.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Décrit les outils qui simplifient la conception, l’exploration, le test et le déploiement d’applications et de bases de données connectées aux données.

 [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Décrit l’architecture ADO.NET et comment utiliser les classes ADO.NET pour gérer les données d’application et interagir avec les sources de données et XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) Décrit comment créer des applications de données qui permettent aux développeurs de programmer par rapport à un modèle conceptuel plutôt que directement sur une base de données relationnelle.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Décrit comment utiliser [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] pour déployer des services de données sur le Web ou sur un intranet qui implémente le [Open Data Protocol (OData)](https://www.odata.org/).

 [Données dans les solutions Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Contient des liens vers des rubriques qui expliquent le fonctionnement des données dans les solutions Office. Cela comprend des informations sur la programmation orientée schéma, la mise en cache des données et l’accès aux données côté serveur.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Décrit les fonctionnalités de requête intégrées à C# et Visual Basic, ainsi que le modèle commun pour interroger des bases de données relationnelles, des documents XML, des DataSets et des collections en mémoire.

 [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Traite de l’utilisation des données XML, du débogage XSLT, des fonctionnalités XML .NET Framework et de l’architecture de la requête XML.

 [Documents et données XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Fournit une vue d’ensemble d’un ensemble complet et intégré de classes qui fonctionnent avec les documents et les données XML dans le .NET Framework.
