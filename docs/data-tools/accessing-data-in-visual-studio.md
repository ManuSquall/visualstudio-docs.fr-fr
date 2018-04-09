---
title: L’accès aux données dans Visual Studio | Documents Microsoft
ms.date: 11/04/2016
ms.topic: article
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 82717e8b0eb8b4b751fc8c5ed983695ff6b6fc4a
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2018
---
# <a name="accessing-data-in-visual-studio"></a>L’accès aux données dans Visual Studio

Dans Visual Studio, vous pouvez créer des applications qui se connectent à pratiquement n’importe quel produit de base de données ou un service, dans n’importe quel format, n’importe où, sur un ordinateur local, sur un réseau local, ou dans un cloud public, privé ou hybride.

Pour les applications en JavaScript, Python, PHP, Ruby ou C++, vous vous connectez à des données comme vous le faites rien, en obtenant des bibliothèques et en écrivant du code. Pour les applications .NET, Visual Studio fournit des outils que vous pouvez utiliser pour Explorer les sources de données, créer des modèles d’objet pour stocker et manipuler les données en mémoire et lier des données à l’interface utilisateur. Microsoft Azure fournit des kits de développement logiciel pour .NET, Java, Node.js, PHP, Python, Ruby, les applications mobiles et des outils dans Visual Studio pour la connexion au stockage Azure.

Les listes suivantes présentent quelques exemples des nombreux systèmes de base de données et de stockage qui peuvent être utilisés à partir de Visual Studio. Le [Microsoft Azure](https://azure.microsoft.com/) offres sont des services de données qui incluent toutes les configuration et administration de la banque de données sous-jacente.  [Azure Tools pour Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) est un composant facultatif qui vous permet de travailler avec des banques de données Azure directement à partir de Visual Studio. La plupart des autres SQL et NoSQL de base de données produits répertoriés ici peut être hébergée sur un ordinateur local, sur un réseau local, ou dans Microsoft Azure sur un ordinateur virtuel. Dans ce scénario, vous êtes responsable de la gestion de la base de données.

**Microsoft Azure**

||||
|-|-|-|
|Base de données SQL|Azure Cosmos DB|Stockage (objets BLOB, tables, files d’attente, les fichiers)|
|SQL Data Warehouse|Base de données Stretch SQL Server|StorSimple|

Et plus encore...

**SQL**

||||
|-|-|-|
|SQL Server 2005-2016, y compris Express et la base de données locale|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

Et plus encore...

**NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

Et plus encore...

Plusieurs fournisseurs de base de données et des tiers en charge l’intégration de Visual Studio par les packages NuGet. Vous pouvez explorer les offres sur nuget.org ou via le Gestionnaire de Package NuGet dans Visual Studio (**outils** > **Gestionnaire de Package NuGet** > **gérer NuGet Packages de Solution**). Autres produits de base de données s’intégrer à Visual Studio en tant qu’extension. Vous pouvez parcourir ces offres dans Marketplace Visual Studio en accédant à **outils**, **Extensions et mises à jour** , puis en sélectionnant **Online** dans le volet gauche de la boîte de dialogue. Pour plus d’informations, consultez [systèmes de base de données Compatible pour Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Support étendu pour SQL Server 2005 a pris fin le 12 avril 2016. Il n’existe aucune garantie que les outils de données dans Visual Studio 2015 et versions ultérieures continueront de fonctionner avec SQL Server 2005 après cette date. Pour plus d’informations, consultez la [annonce de fin de prise en charge pour SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Langages .NET

Tous les accès aux données .NET, y compris dans .NET Core, est basé sur ADO.NET, un ensemble de classes qui définit une interface pour accéder à n’importe quel type de source de données relationnel et non relationnelles. Visual Studio propose plusieurs outils et concepteurs qui fonctionnent avec ADO.NET pour vous aider à vous connecter aux bases de données, de manipuler les données et de présenter les données à l’utilisateur. La documentation de cette section décrit comment utiliser ces outils. Vous pouvez également programmer directement les objets de commande ADO.NET. Pour plus d’informations sur l’appel de directement les APIs ADO.NET, consultez [ADO.NET](/dotnet/framework/data/adonet/index).

Pour obtenir la documentation accès aux données spécifiquement liée à ASP.NET, consultez [utilisation des données](http://www.asp.net/web-forms/overview/presenting-and-managing-data) sur le site ASP.NET. Pour obtenir un didacticiel sur l’utilisation d’Entity Framework avec ASP.NET MVC, consultez [mise en route avec Entity Framework 6 Code First à l’aide de MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Les applications universelles Windows Platform (UWP) en c# ou Visual Basic peuvent utiliser Microsoft Azure SDK pour .NET pour accéder au stockage Azure et autres services Azure. La classe Windows.Web.HttpClient permet la communication avec un service RESTful. Pour plus d’informations, consultez [comment se connecter à un serveur HTTP à l’aide de Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Pour le stockage de données sur l’ordinateur local, l’approche recommandée consiste à utiliser SQLite, qui s’exécute dans le même processus que l’application. Si une couche de mappage relationnel objet (ORM) est requise, vous pouvez utiliser Entity Framework. Pour plus d’informations, consultez [accès aux données](/windows/uwp/data-access/index) dans le centre de développement Windows.

Si vous vous connectez aux services Azure, veillez à télécharger la dernière version [les outils de développement logiciel Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Fournisseurs de données

Pour une base de données être utilisable dans ADO.NET, il doit avoir une personnalisée *fournisseur de données ADO.NET* ou sinon la doit exposer une interface ODBC ou OLE DB. Microsoft fournit un [la liste des fournisseurs de données ADO.NET](https://msdn.microsoft.com/data/dd363565) pour les produits SQL Server, ainsi que les fournisseurs OLE DB et ODBC.

### <a name="data-modeling"></a>Modélisation des données

Dans .NET, vous avez trois possibilités de modélisation et la manipulation de données en mémoire une fois que vous l’avez extrait à partir d’une source de données :

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) la technologie Microsoft ORM préférée. Vous pouvez l’utiliser pour programmer par rapport à des données relationnelles en tant qu’objets de première classe .NET. Pour les nouvelles applications, il doit être le premier choix de valeur par défaut lorsqu’un modèle est requis. Elle nécessite la prise en charge personnalisée à partir du fournisseur ADO.NET sous-jacent.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) un mappeur objet / relationnel de génération antérieure. Elle fonctionne bien pour les scénarios moins complexes, mais n’est plus en cours de développement.

[Jeux de données](../data-tools/dataset-tools-in-visual-studio.md) les plus anciennes de ces trois technologies de modélisation. Il est principalement destiné à développer rapidement des applications de « formulaires de données » dans lequel vous ne sont pas le traitement de grandes quantités de données ou effectuer des requêtes complexes ou des transformations. Un objet de jeu de données se compose des objets DataTable et DataRow qui logiquement ressemblent beaucoup plus que les objets .NET aux objets de base de données SQL. Pour les applications relativement simples basées sur des sources de données SQL, les jeux de données peut-être encore être un bon choix.

Il n’est pas obligatoire d’utiliser ces technologies. Dans certains scénarios, surtout lorsque les performances sont critiques, vous pouvez simplement utiliser un objet DataReader pour lire à partir de la base de données et copiez les valeurs dont vous avez besoin dans un objet de collection telles que liste\<T >.

## <a name="native-c"></a>C++ natif

Les applications C++ qui se connectent à SQL Server doivent utiliser le [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) dans la plupart des cas. Si les serveurs sont liés, OLE DB est nécessaire et que vous utilisez le [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Vous pouvez accéder à des autres bases de données à l’aide de [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou pilotes OLE DB directement. ODBC est l’interface de base de données standard en cours, mais la plupart des systèmes de base de données fournissent des fonctionnalités personnalisées qui ne sont pas accessibles via l’interface ODBC. OLE DB est une technologie d’accès aux données COM héritée qui est toujours pris en charge mais non recommandée pour les nouvelles applications. Pour plus d’informations, consultez [accès aux données dans Visual C++](/cpp/data/data-access-in-cpp).

Les programmes C++ qui utilisent des services REST peuvent utiliser le [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Les programmes C++ qui fonctionnent avec Microsoft Azure Storage peuvent utiliser le [Client de stockage Microsoft Azure](http://www.nuget.org/packages/wastorage).

Modélisation des données&mdash;Visual Studio ne fournit pas d’une couche ORM pour C++. [ODB](http://www.codesynthesis.com/products/odb/) est un ORM open source populaire pour C++.

Pour en savoir plus sur la connexion aux bases de données à partir d’applications C++, consultez [Visual Studio data tools pour C++](../data-tools/visual-studio-data-tools-for-cpp.md). Pour plus d’informations sur les technologies d’accès aux données Visual C++ hérités, consultez [accès aux données](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript dans Visual Studio](/scripting/javascript/javascript-language-reference) est un langage de premier ordre pour la création des applications multiplateformes, les applications UWP, services de cloud computing, sites Web et applications web. Pour installer les bibliothèques JavaScript favorites et des produits de base de données, vous pouvez utiliser Bower, Grunt, Gulp, npm et NuGet à partir de Visual Studio. Se connecter aux services de stockage Azure et en téléchargeant les kits de développement logiciel à partir de la [site Web Azure](https://azure.microsoft.com/). Edge.js est une bibliothèque qui se connecte côté serveur JavaScript (Node.js) à des sources de données ADO.NET.

## <a name="python"></a>Python

Installer [Python prend en charge dans Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) pour créer des applications de Python. La documentation sur Azure a plusieurs didacticiels sur la connexion aux données, notamment les suivantes :

- [Django et base de données SQL Azure](/azure/app-service/app-service-web-get-started-python)
- [Django et MySQL sur Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Travailler avec [BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [fichiers](/azure/storage/files/storage-python-how-to-use-file-storage), [les files d’attente](/azure/storage/queues/storage-python-how-to-use-queue-storage), et [tables (DB Cosmo)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Rubriques connexes

[Plateforme de Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;fournit une introduction au cloud intelligent Microsoft, y compris Cortana Analytique Suite et prise en charge de l’Internet des objets.

[Microsoft Azure Storage](/azure/storage/)&mdash;décrit le stockage Azure et comment créer des applications à l’aide d’objets BLOB Windows Azure, les tables, les files d’attente et les fichiers.

[Base de données SQL Azure](/azure/sql-database/)&mdash;décrit comment se connecter à la base de données SQL Azure, une base de données relationnelle en tant que service.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;décrit les outils qui simplifient la conception, exploration, tester et déployer des applications de données connectées et des bases de données.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;décrit l’architecture ADO.NET et comment utiliser les classes ADO.NET pour gérer les données d’application et interagir avec les sources de données et XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)&mdash;décrit comment créer des applications de données qui permettent aux développeurs de programmer par rapport à un modèle conceptuel au lieu de directement par rapport à une base de données relationnelle.

[Services de données WCF 4.5](/dotnet/framework/data/wcf/index)&mdash;explique comment utiliser [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] pour déployer des services de données sur le web ou un intranet qui implémentent la [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Les données dans les Solutions Office](../vsto/data-in-office-solutions.md)&mdash;contient des liens vers des rubriques qui expliquent comment fonctionnent les données dans les solutions Office. Cela inclut des informations sur la programmation orientée schéma, la mise en cache des données et accès aux données côté serveur.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;décrit les fonctionnalités de requête intégrées dans c# et Visual Basic et que le modèle commun pour interroger des bases de données relationnelles, les documents XML, les jeux de données et les collections en mémoire.

[Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;présente l’utilisation de fonctionnalités XML du .NET Framework de données, le débogage XSLT, XML et l’architecture de requête XML.

[Documents et données XML](/dotnet/standard/data/xml/index)&mdash;fournit une vue d’ensemble pour un ensemble complet et intégré de classes qui fonctionnent avec des documents XML et les données dans le .NET Framework.
