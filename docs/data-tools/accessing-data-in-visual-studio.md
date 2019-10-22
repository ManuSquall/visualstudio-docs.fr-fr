---
title: Outils et accès aux données
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f2a33a0090be980c221ebfbe7f3116cdfef7b23b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648983"
---
# <a name="access-data-in-visual-studio"></a>Accéder aux données dans Visual Studio

Dans Visual Studio, vous pouvez créer des applications qui se connectent à des données dans pratiquement n’importe quel produit ou service de base de données, dans n’importe quel format, en tout lieu, sur un ordinateur local, sur un réseau local, ou dans un cloud public, privé ou hybride.

Pour les applications en JavaScript, Python, PHP, Ruby ou C++, vous vous connectez à des données comme vous le faites autrement, en obtenant des bibliothèques et en écrivant du code. Pour les applications .NET, Visual Studio fournit des outils que vous pouvez utiliser pour explorer des sources de données, créer des modèles objet pour stocker et manipuler des données en mémoire, et lier des données à l’interface utilisateur. Microsoft Azure fournit des kits de développement logiciel (SDK) pour .NET, Java, node. js, PHP, Python, Ruby et Mobile Apps, ainsi que des outils dans Visual Studio pour la connexion au stockage Azure.

Les listes suivantes présentent quelques-uns des nombreux systèmes de stockage et de base de données qui peuvent être utilisés à partir de Visual Studio. Les offres de [Microsoft Azure](https://azure.microsoft.com/) sont des services de données qui incluent l’approvisionnement et l’administration du magasin de données sous-jacent. La charge de travail **développement Azure** dans [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) vous permet d’utiliser des magasins de données Azure directement à partir de Visual Studio.

![Charge de travail Développement Azure](media/azure-development-workload.png)

La plupart des autres produits de base de données SQL et NoSQL répertoriés ici peuvent être hébergés sur un ordinateur local, sur un réseau local ou dans Microsoft Azure sur un ordinateur virtuel. Si vous hébergez la base de données dans une machine virtuelle Microsoft Azure, vous êtes responsable de la gestion de la base de données elle-même.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- Stockage (objets BLOB, tables, files d’attente, fichiers)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- Et plus encore...

**SQL**

- SQL Server 2005-2016 (comprend Express et la base de données locale)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- Et plus encore...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- Et plus encore...

::: moniker range="vs-2017"

De nombreux fournisseurs de bases de données et tiers prennent en charge l’intégration de Visual Studio par les packages NuGet. Vous pouvez explorer les offres sur nuget.org ou par le biais du gestionnaire de package NuGet dans Visual Studio (**outils**  > **Gestionnaire de package NuGet**  > **gérer les packages NuGet pour la solution**). D’autres produits de base de données s’intègrent à Visual Studio en tant qu’extension. Vous pouvez parcourir ces offres dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou en accédant à **Outils**  > **extensions et mises à jour** , puis en sélectionnant **en ligne** dans le volet gauche de la boîte de dialogue. Pour plus d’informations, consultez [systèmes de base de données compatibles pour Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

De nombreux fournisseurs de bases de données et tiers prennent en charge l’intégration de Visual Studio par les packages NuGet. Vous pouvez explorer les offres sur nuget.org ou par le biais du gestionnaire de package NuGet dans Visual Studio (**outils**  > **Gestionnaire de package NuGet**  > **gérer les packages NuGet pour la solution**). D’autres produits de base de données s’intègrent à Visual Studio en tant qu’extension. Vous pouvez parcourir ces offres dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou en accédant à **Extensions**  > **gérer les extensions** , puis en sélectionnant **en ligne** dans le volet gauche de la boîte de dialogue. Pour plus d’informations, consultez [systèmes de base de données compatibles pour Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> La prise en charge étendue de SQL Server 2005 a pris fin le 12 avril 2016. Il n’existe aucune garantie que les outils de données dans Visual Studio 2015 et versions ultérieures continuent de fonctionner avec SQL Server 2005. Pour plus d’informations, consultez l' [annonce de fin de support pour SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Langages .NET

Tous les accès aux données .NET, y compris dans .NET Core, sont basés sur ADO.NET, un ensemble de classes qui définit une interface pour accéder à n’importe quel type de source de données, à la fois relationnelles et non relationnelles. Visual Studio propose plusieurs outils et concepteurs qui fonctionnent avec ADO.NET pour vous aider à vous connecter aux bases de données, à manipuler les données et à présenter les données à l’utilisateur. La documentation de cette section décrit comment utiliser ces outils. Vous pouvez également programmer directement par rapport aux objets de commande ADO.NET. Pour plus d’informations sur l’appel direct des API ADO.NET, consultez [ADO.net](/dotnet/framework/data/adonet/index).

Pour obtenir une documentation d’accès aux données relative à ASP.NET, consultez [utilisation des données](https://www.asp.net/web-forms/overview/presenting-and-managing-data) sur le site ASP.net. Pour obtenir un didacticiel sur l’utilisation de Entity Framework avec ASP.NET MVC, consultez [prise en main avec Entity Framework 6 Code First à l’aide de MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Les applications de plateforme Windows universelle (UWP C# ) dans ou Visual Basic peuvent utiliser le kit de développement logiciel Microsoft Azure SDK pour .net pour accéder à stockage Azure et à d’autres services Azure. La classe Windows. Web. HttpClient permet la communication avec n’importe quel service RESTful. Pour plus d’informations, consultez [Comment se connecter à un serveur http à l’aide de Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Pour le stockage de données sur l’ordinateur local, l’approche recommandée consiste à utiliser SQLite, qui s’exécute dans le même processus que l’application. Si une couche de mappage objet-relationnel (ORM) est requise, vous pouvez utiliser Entity Framework. Pour plus d’informations, consultez [accès aux données](/windows/uwp/data-access/index) dans le centre de développement Windows.

Si vous vous connectez aux services Azure, veillez à télécharger les derniers [outils du kit de développement logiciel (SDK) Azure](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Fournisseurs de données

Pour qu’une base de données soit consommable dans ADO.NET, elle doit avoir un *fournisseur de données ADO.net* personnalisé ou doit exposer une interface ODBC ou OLE DB. Microsoft fournit une [liste de fournisseurs de données ADO.net](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) pour les produits SQL Server, ainsi que les fournisseurs ODBC et OLE DB.

### <a name="data-modeling"></a>Modélisation des données

Dans .NET, vous avez trois possibilités de modélisation et de manipulation des données en mémoire après les avoir récupérées d’une source de données :

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) La technologie Microsoft ORM préférée. Vous pouvez l’utiliser pour programmer des données relationnelles en tant qu’objets .NET de première classe. Pour les nouvelles applications, il doit s’agir du premier choix par défaut lorsqu’un modèle est requis. Elle nécessite une prise en charge personnalisée du fournisseur ADO.NET sous-jacent.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Un mappeur relationnel objet de génération antérieure. Elle fonctionne bien pour les scénarios moins complexes, mais n’est plus en cours de développement.

[Jeux de données](../data-tools/dataset-tools-in-visual-studio.md) La plus ancienne des trois technologies de modélisation. Il est principalement conçu pour le développement rapide d’applications de « formulaires de données » dans lesquelles vous ne traitez pas d’énormes quantités de données ou effectuez des requêtes ou des transformations complexes. Un objet DataSet se compose d’objets DataTable et DataRow qui ressemblent logiquement à des objets de base de données SQL, bien plus que des objets .NET. Pour les applications relativement simples basées sur les sources de données SQL, les jeux de données peuvent toujours être un bon choix.

Il n’est pas nécessaire d’utiliser ces technologies. Dans certains scénarios, en particulier lorsque les performances sont critiques, vous pouvez simplement utiliser un objet DataReader pour lire la base de données et copier les valeurs dont vous avez besoin dans un objet de collection, tel que List \<T >.

## <a name="native-c"></a>C++ natif

C++dans la plupart des cas, les applications qui se connectent à SQL Server doivent utiliser [Microsoft® ODBC Driver 13,1 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) . Si les serveurs sont liés, OLE DB est nécessaire et pour que vous utilisiez le [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Vous pouvez accéder à d’autres bases de données à l’aide de pilotes [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) ou OLE DB directement. ODBC est l’interface de base de données standard actuelle, mais la plupart des systèmes de base de données fournissent des fonctionnalités personnalisées qui ne sont pas accessibles par le biais de l’interface ODBC. OLE DB est une technologie héritée d’accès aux données COM qui est toujours prise en charge mais non recommandée pour les nouvelles applications. Pour plus d’informations, consultez [accès aux données C++dans Visual ](/cpp/data/data-access-in-cpp).

C++les programmes qui utilisent des services REST peuvent utiliser le [ C++ Kit de développement logiciel Rest](https://github.com/Microsoft/cpprestsdk).

C++les programmes qui fonctionnent avec Stockage Microsoft Azure peuvent utiliser le [Client stockage Microsoft Azure](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

La modélisation des données &mdash;Visual Studio ne fournit pas de couche C++ORM pour. [ODB](https://www.codesynthesis.com/products/odb/) est un ORM Open source populaire pour C++.

Pour en savoir plus sur la connexion à des C++ bases de données à partir d’applications, consultez [Visual Studio Data Tools pour C++ ](../data-tools/visual-studio-data-tools-for-cpp.md). Pour plus d’informations sur les C++ technologies d’accès aux données visuelles héritées, consultez [accès aux données](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript dans Visual Studio](/scripting/javascript/javascript-language-reference) est un langage de premier ordre pour la création d’applications multiplateformes, d’applications UWP, de services Cloud, de sites Web et d’applications Web. Vous pouvez utiliser Bower, Grunt, Gulp, NPM et NuGet à partir de Visual Studio pour installer vos bibliothèques et vos produits de base de données JavaScript préférés. Connectez-vous à Azure Storage et aux services en téléchargeant les kits de développement logiciel à partir du [site Web Azure](https://azure.microsoft.com/). Edge. js est une bibliothèque qui connecte le JavaScript côté serveur (node. js) à des sources de données ADO.NET.

## <a name="python"></a>Python

Installez la [prise en charge de Python dans Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) pour créer des applications python. La documentation Azure comporte plusieurs didacticiels sur la connexion aux données, notamment les suivantes :

- [Django et SQL Database sur Azure](/azure/app-service/app-service-web-get-started-python)
- [Django et MySQL sur Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Utiliser des [objets BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), des [fichiers](/azure/storage/files/storage-python-how-to-use-file-storage), des [files d’attente](/azure/storage/queues/storage-python-how-to-use-queue-storage)et des [tables (Cosmo dB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Rubriques connexes

La [plateforme Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash;Provides une présentation du Cloud intelligent Microsoft, y compris Cortana Analytics suite et la prise en charge de Internet des objets.

[Stockage Microsoft Azure](/azure/storage/) &mdash;Describes le stockage Azure et comment créer des applications à l’aide d’objets BLOB, de tables, de files d’attente et de fichiers Azure.

[Azure SQL Database](/azure/sql-database/) &mdash;Describes la connexion à Azure SQL Database, une base de données relationnelle en tant que service.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash;Describes les outils qui simplifient la conception, l’exploration, le test et le déploiement d’applications et de bases de données connectées aux données.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash;Describes l’architecture ADO.net et comment utiliser les classes ADO.net pour gérer les données d’application et interagir avec les sources de données et XML.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/) &mdash;Describes la création d’applications de données qui permettent aux développeurs de programmer par rapport à un modèle conceptuel plutôt que directement sur une base de données relationnelle.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index) &mdash;Describes comment utiliser [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] pour déployer des services de données sur le Web ou sur un intranet qui implémente le [Open Data Protocol (OData)](https://www.odata.org/).

Les [données des solutions office](../vsto/data-in-office-solutions.md) &mdash;Contains des liens vers des rubriques qui expliquent le fonctionnement des données dans les solutions Office. Cela comprend des informations sur la programmation orientée schéma, la mise en cache des données et l’accès aux données côté serveur.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) &mdash;Describes les fonctionnalités de requête intégrées C# à et Visual Basic, ainsi que le modèle commun pour interroger des bases de données relationnelles, des documents XML, des DataSets et des collections en mémoire.

Les [outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash;Discusses l’utilisation des données XML, le débogage de XSLT, les fonctionnalités XML .net et l’architecture de la requête XML.

[Les documents et les données xml](/dotnet/standard/data/xml/index) &mdash;Provides une vue d’ensemble d’un ensemble complet et intégré de classes qui fonctionnent avec des documents et des données XML dans .net.
