---
title: Accès aux données et des outils
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0a880604f14f840c3f4712e1a8d0e4d8e9cf1822
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283469"
---
# <a name="access-data-in-visual-studio"></a>Accéder aux données dans Visual Studio

Dans Visual Studio, vous pouvez créer des applications qui se connectent à des données dans n’importe quel produit de base de données ou un service, dans n’importe quel format, n’importe où, sur un ordinateur local, sur un réseau local, ou dans un cloud public, privé ou hybride.

Pour les applications avec JavaScript, Python, PHP, Ruby ou C++, vous connectez aux données comme vous le faites rien d’autre, en obtenant des bibliothèques et d’écriture de code. Pour les applications .NET, Visual Studio fournit des outils que vous pouvez utiliser pour Explorer les sources de données, créer des modèles d’objet pour stocker et manipuler des données en mémoire et lier des données à l’interface utilisateur. Microsoft Azure fournit des kits SDK pour .NET, Java, Node.js, PHP, Python, Ruby et les applications mobiles et les outils dans Visual Studio pour la connexion au stockage Azure.

Les listes suivantes présentent quelques-uns des nombreux systèmes base de données et de stockage qui peuvent être utilisés à partir de Visual Studio. Le [Microsoft Azure](https://azure.microsoft.com/) offres sont des services de données qui incluent tous les d’approvisionnement et d’administration de la banque de données sous-jacente. Le **développement Azure** charge de travail dans [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) vous permet de travailler avec des banques de données Azure directement à partir de Visual Studio.

![Charge de travail Développement Azure](media/azure-development-workload.png)

La plupart des autres SQL et NoSQL de base de données produits répertoriés ici peut être hébergée sur un ordinateur local, sur un réseau local ou dans Microsoft Azure sur une machine virtuelle. Si vous hébergez la base de données dans une machine virtuelle Microsoft Azure, vous êtes responsable de la gestion de la base de données.

**Microsoft Azure**

||||
|-|-|-|
|Base de données SQL|Azure Cosmos DB|Stockage (objets BLOB, tables, files d’attente, fichiers)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

Et plus encore...

**SQL**

||||
|-|-|-|
|SQL Server 2005-2016, y compris Express et base de données locale|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

Et plus encore...

**NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|Données|OrientDB|RavenDB|
|VelocityDB|||

Et plus encore...

Plusieurs fournisseurs de base de données et les tiers en charge l’intégration de Visual Studio par les packages NuGet. Vous pouvez explorer les offres sur nuget.org ou via le Gestionnaire de Package NuGet dans Visual Studio (**outils** > **Gestionnaire de Package NuGet** > **gérer NuGet Packages de Solution**). Autres produits de base de données s’intègrent avec Visual Studio en tant qu’extension. Vous pouvez parcourir ces offres dans la place de marché Visual Studio en accédant à **outils**, **Extensions et mises à jour** , puis en sélectionnant **Online** dans le volet gauche de la boîte de dialogue. Pour plus d’informations, consultez [des systèmes de base de données Compatible pour Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Le support étendu pour SQL Server 2005 a pris fin le 12 avril 2016. Il n’existe aucune garantie que les outils de données dans Visual Studio 2015 et versions ultérieures continueront de fonctionner avec SQL Server 2005 après cette date. Pour plus d’informations, consultez le [annonce de fin de support pour SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Langages .NET

Tous les accès aux données .NET, y compris dans .NET Core, est basé sur ADO.NET, un ensemble de classes qui définit une interface pour accéder à n’importe quel type de source de données relationnel et non relationnelles. Visual Studio dispose de plusieurs outils et concepteurs qui fonctionnent avec ADO.NET pour vous aider à vous connecter aux bases de données, manipuler les données et présenter les données à l’utilisateur. La documentation de cette section décrit comment utiliser ces outils. Vous pouvez également programmer directement les objets de commande ADO.NET. Pour plus d’informations sur l’appel de directement les APIs ADO.NET, consultez [ADO.NET](/dotnet/framework/data/adonet/index).

Pour l’accès aux données la documentation relative à ASP.NET, consultez [utilisation des données](http://www.asp.net/web-forms/overview/presenting-and-managing-data) sur le site ASP.NET. Pour obtenir un didacticiel sur l’utilisation d’Entity Framework avec ASP.NET MVC, consultez [mise en route avec Entity Framework 6 Code First avec MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Des applications de Windows Platform (UWP) universelle en c# ou Visual Basic peuvent utiliser le Kit de développement logiciel Microsoft Azure pour .NET pour accéder à stockage Azure et autres services Azure. La classe Windows.Web.HttpClient permet la communication avec n’importe quel service RESTful. Pour plus d’informations, consultez [comment se connecter à un serveur HTTP à l’aide de Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Stockage des données sur l’ordinateur local, l’approche recommandée consiste à utiliser SQLite, qui s’exécute dans le même processus que l’application. Si une couche de mappage objet-relationnel (ORM) est requise, vous pouvez utiliser Entity Framework. Pour plus d’informations, consultez [accès aux données](/windows/uwp/data-access/index) dans le centre de développement Windows.

Si vous vous connectez aux services Azure, veillez à télécharger la dernière version [outils du SDK Azure](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Fournisseurs de données

Pour une base de données être consommable dans ADO.NET, il doit avoir un personnalisé *fournisseur de données ADO.NET* ou else doit exposer une interface ODBC ou OLE DB. Microsoft fournit un [liste des fournisseurs de données ADO.NET](https://msdn.microsoft.com/data/dd363565) pour les produits SQL Server, ainsi que des fournisseurs ODBC et OLE DB.

### <a name="data-modeling"></a>Modélisation des données

Dans .NET, vous avez trois possibilités pour la modélisation et la manipulation de données en mémoire une fois que vous l’avez récupéré à partir d’une source de données :

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) la technologie Microsoft ORM préférée. Vous pouvez l’utiliser pour programmer par rapport aux données relationnelles comme des objets .NET. Pour les nouvelles applications, il doit être le premier choix de valeur par défaut lorsqu’un modèle est requis. Elle nécessite la prise en charge personnalisée à partir du fournisseur ADO.NET sous-jacent.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) un mappeur objet-relationnel de génération antérieure. Il fonctionne bien pour les scénarios moins complexes, mais n’est plus en cours de développement.

[Jeux de données](../data-tools/dataset-tools-in-visual-studio.md) le plus ancien de ces trois technologies de modélisation. Il est conçu principalement pour le développement rapide d’applications de « formulaires de données » dans lequel vous ne sont pas traiter de grandes quantités de données ou effectuer des requêtes complexes ou des transformations. Un objet DataSet comprend des objets DataTable et DataRow logiquement semblables aux objets de base de données SQL beaucoup plus que les objets .NET. Pour les applications relativement simples basées sur des sources de données SQL, les jeux de données peut toujours être un bon choix.

Il est inutile d’utiliser ces technologies. Dans certains scénarios, en particulier où les performances sont critiques, vous pouvez simplement utiliser un objet DataReader à lire à partir de la base de données et copier les valeurs dont vous avez besoin dans un objet de collection, telles que liste\<T >.

## <a name="native-c"></a>C++ natif

Les applications C++ qui se connectent à SQL Server doivent utiliser le [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) dans la plupart des cas. Si les serveurs sont liés, OLE DB est nécessaire et que vous utilisez le [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Vous pouvez accéder aux autres bases de données à l’aide de [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou pilotes OLE DB directement. ODBC est l’interface actuelle de la base de données standard, mais la plupart des systèmes de base de données fournissent des fonctionnalités personnalisées qui ne sont pas accessibles via l’interface ODBC. OLE DB est une technologie d’accès aux données COM héritée qui est toujours pris en charge mais non recommandée pour les nouvelles applications. Pour plus d’informations, consultez [accès aux données dans Visual C++](/cpp/data/data-access-in-cpp).

Les programmes C++ qui utilisent des services REST peuvent utiliser le [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Les programmes C++ qui fonctionnent avec Microsoft Azure Storage peuvent utiliser le [Client de stockage Microsoft Azure](http://www.nuget.org/packages/wastorage).

Modélisation des données&mdash;Visual Studio ne fournit pas d’une couche ORM pour C++. [ODB](http://www.codesynthesis.com/products/odb/) est un ORM open source populaires pour C++.

Pour en savoir plus sur la connexion aux bases de données à partir d’applications C++, consultez [Visual Studio data tools pour C++](../data-tools/visual-studio-data-tools-for-cpp.md). Pour plus d’informations sur les technologies d’accès aux données héritées Visual C++, consultez [accès aux données](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript dans Visual Studio](/scripting/javascript/javascript-language-reference) est un langage de premier ordre pour la création des applications multiplateformes, les applications UWP, les services cloud, les sites Web et les applications web. Vous pouvez utiliser Bower, Grunt, Gulp, npm et NuGet à partir de Visual Studio pour installer vos bibliothèques JavaScript favorites et les produits de base de données. Se connecter au stockage Azure et services en téléchargeant les kits de développement logiciel à partir de la [site Web Azure](https://azure.microsoft.com/). Edge.js est une bibliothèque qui se connecte côté serveur JavaScript (Node.js) à des sources de données ADO.NET.

## <a name="python"></a>Python

Installer [prennent en charge de Python dans Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) pour créer des applications Python. La documentation Azure comporte plusieurs didacticiels sur la connexion aux données, notamment les éléments suivants :

- [Django et SQL Database sur Azure](/azure/app-service/app-service-web-get-started-python)
- [Django et MySQL sur Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Travailler avec [blobs](/azure/storage/blobs/storage-quickstart-blobs-python), [fichiers](/azure/storage/files/storage-python-how-to-use-file-storage), [files d’attente](/azure/storage/queues/storage-python-how-to-use-queue-storage), et [tables (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Rubriques connexes

[Plateforme Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;fournit une introduction au cloud intelligent Microsoft, y compris la prise en charge pour l’Internet des objets et la Suite d’Analytique Cortana.

[Microsoft Azure Storage](/azure/storage/)&mdash;décrit le stockage Azure et comment créer des applications à l’aide des objets BLOB Azure, les tables, les files d’attente et les fichiers.

[Base de données SQL Azure](/azure/sql-database/)&mdash;décrit comment se connecter à la base de données SQL Azure, une base de données relationnelle en tant que service.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;décrit les outils qui simplifient la conception, exploration, de test et de déploiement connecté aux données des applications et bases de données.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;décrit l’architecture ADO.NET et comment utiliser les classes ADO.NET pour gérer les données d’application et interagir avec des sources de données et XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)&mdash;décrit comment créer des applications de données qui permettent aux développeurs de programmer par rapport à un modèle conceptuel au lieu de directement par rapport à une base de données relationnelle.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index)&mdash;explique comment utiliser [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] pour déployer des services de données sur le web ou un intranet qui implémentent le [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Les données dans les Solutions Office](../vsto/data-in-office-solutions.md)&mdash;contient des liens vers des rubriques qui expliquent comment fonctionnent les données dans les solutions Office. Cela inclut des informations sur la programmation orientée schéma, la mise en cache des données et accès aux données côté serveur.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;décrit les fonctionnalités de requête intégrées dans c# et Visual Basic et le modèle commun pour interroger des bases de données relationnelles, les documents XML, les jeux de données et les collections en mémoire.

[Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;aborde l’utilisation des fonctionnalités XML du .NET Framework de données, le débogage XSLT, XML et l’architecture de requête XML.

[Documents et données XML](/dotnet/standard/data/xml/index)&mdash;fournit une vue d’ensemble à un ensemble complet et intégré de classes qui fonctionnent avec des documents XML et des données dans le .NET Framework.
