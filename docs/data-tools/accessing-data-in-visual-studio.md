---
title: "L’accès aux données dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 585f021bf88dd6005a82643c5d182bd1fcbf8e91
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="accessing-data-in-visual-studio"></a>L’accès aux données dans Visual Studio
Dans Visual Studio, vous pouvez créer des applications qui se connectent à pratiquement n’importe quel produit de base de données ou un service, dans n’importe quel format, n’importe où, sur un ordinateur local, sur un réseau local, ou dans un cloud public, privé ou hybride.  
  
Pour les applications en JavaScript, Python, PHP, Ruby ou C++, vous vous connectez à des données comme vous le faites rien, en obtenant des bibliothèques et en écrivant du code. Pour les applications .NET, Visual Studio fournit des outils que vous pouvez utiliser pour Explorer les sources de données, créer des modèles d’objet pour stocker et manipuler les données en mémoire et lier des données à l’interface utilisateur. Microsoft Azure fournit des kits de développement logiciel pour .NET, Java, Node.js, PHP, Python, Ruby, les applications mobiles et des outils dans Visual Studio pour la connexion au stockage Azure.  
  
Les listes suivantes présentent quelques exemples des nombreux systèmes de base de données et de stockage qui peuvent être utilisés à partir de Visual Studio. Le [Microsoft Azure](https://azure.microsoft.com/) offres sont des services de données qui incluent toutes les configuration et administration de la banque de données sous-jacente.  [Azure Tools pour Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) est un composant facultatif qui vous permet de travailler avec des banques de données Azure directement à partir de Visual Studio. La plupart des autres SQL et NoSQL de base de données produits répertoriés ici peut être hébergée sur un ordinateur local, sur un réseau local, ou dans Microsoft Azure sur un ordinateur virtuel. Dans ce scénario, vous êtes responsable de la gestion de la base de données.  
  
**Microsoft Azure**  
  
||||  
|-|-|-|  
|Base de données SQL|DocumentDB|Stockage (objets BLOB, tables, files d’attente, les fichiers)|  
|Entrepôt de données SQL|Base de données Stretch SQL Server|StorSimple|  
  
et bien plus encore...  
  
**SQL**  
  
||||  
|-|-|-|  
|SQL Server 2005-2016, y compris Express et la base de données locale|Toute|MariaDB|  
|MySQL|Oracle|PostgreSQL|  
|SQLite|||  
  
et bien plus encore...  
  
**NoSQL**  
  
||||  
|-|-|-|  
|Apache Cassandra|CouchDB|MongoDB|  
|Données|OrientDB|RavenDB|  
|VelocityDB|||  
  
et bien plus encore...  
  
Plusieurs fournisseurs de base de données et des tiers en charge l’intégration de Visual Studio par les packages NuGet. Vous pouvez explorer les offres sur nuget.org ou via le Gestionnaire de Package NuGet dans Visual Studio (**outils** > **Gestionnaire de Package NuGet** > **gérer NuGet Packages de Solution**). Autres produits de base de données s’intégrer à Visual Studio en tant qu’extension. Vous pouvez parcourir ces offres dans la galerie Visual Studio en accédant à **outils** > **Extensions et mises à jour** , puis en sélectionnant **Online** dans la partie gauche volet de la boîte de dialogue. Pour plus d’informations, consultez [l’installation de systèmes de base de données, des outils et des exemples](../data-tools/installing-database-systems-tools-and-samples.md).  
  
> [!NOTE]
> Support étendu pour SQL Server 2005 a pris fin le 12 avril 2016. Il n’existe aucune garantie que les outils de données dans Visual Studio 2015 et versions ultérieures continueront de fonctionner avec SQL Server 2005 après cette date. Pour plus d’informations, consultez la [annonce de fin de prise en charge pour SQL Server 2005](https://www.microsoft.com/server-cloud/products/sql-server-2005/).  
  
### <a name="net-languages"></a>Langages .NET  
Tous les accès aux données .NET, y compris dans .NET Core, est basé sur ADO.NET, un ensemble de classes qui définit une interface pour accéder à n’importe quel type de source de données relationnel et non relationnelles. Visual Studio propose plusieurs outils et concepteurs qui fonctionnent avec ADO.NET pour vous aider à vous connecter aux bases de données, de manipuler les données et de présenter les données à l’utilisateur. La documentation de cette section décrit comment utiliser ces outils. Vous pouvez également programmer directement les objets de commande ADO.NET. Pour plus d’informations sur l’appel de directement les APIs ADO.NET, consultez [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) dans MSDN Library.  
  
Pour obtenir la documentation accès aux données spécifiquement liée à ASP.NET, consultez [utilisation des données](http://www.asp.net/web-forms/overview/presenting-and-managing-data) sur le site ASP.NET. Pour obtenir un didacticiel sur l’utilisation d’Entity Framework avec ASP.NET MVC, consultez [mise en route avec Entity Framework 6 Code First à l’aide de MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).  
  
Les applications universelles Windows Platform (UWP) en c# ou Visual Basic peuvent utiliser Microsoft Azure SDK pour .NET pour accéder au stockage Azure et autres services Azure. La classe Windows.Web.HttpClient permet la communication avec un service RESTful. Pour plus d’informations, consultez [comment se connecter à un serveur HTTP à l’aide de Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).  
  
Pour le stockage de données sur l’ordinateur local, l’approche recommandée consiste à utiliser SQLite, qui s’exécute dans le même processus que l’application. Si une couche de mappage relationnel objet (ORM) est requise, vous pouvez utiliser Entity Framework. Pour plus d’informations, consultez [accès aux données](https://msdn.microsoft.com/windows/uwp/data-access/index) dans le centre de développement Windows.  
  
Si vous vous connectez aux services Azure, veillez à télécharger la dernière version [les outils de développement logiciel Azure SDK](https://azure.microsoft.com/downloads/).  
  
#### <a name="data-providers"></a>Fournisseurs de données  
Pour une base de données être utilisable dans ADO.NET, il doit avoir une personnalisée *fournisseur de données ADO.NET* ou sinon la doit exposer une interface ODBC ou OLE DB. Microsoft fournit un [la liste des fournisseurs de données ADO.NET](https://msdn.microsoft.com/data/dd363565) pour les produits SQL Server, ainsi que les fournisseurs OLE DB et ODBC.  
  
#### <a name="data-modeling"></a>Modélisation des données  
Dans .NET, vous avez trois possibilités de modélisation et la manipulation de données en mémoire une fois que vous l’avez extrait à partir d’une source de données :  
  
[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)  
La technologie Microsoft ORM préférée. Vous pouvez l’utiliser pour programmer par rapport à des données relationnelles en tant qu’objets de première classe .NET. Pour les nouvelles applications, il doit être le premier choix de valeur par défaut lorsqu’un modèle est requis. Elle nécessite la prise en charge personnalisée à partir du fournisseur ADO.NET sous-jacent.  
  
[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
Un mappeur objet / relationnel générations antérieures. Elle fonctionne bien pour les scénarios moins complexes, mais n’est plus en cours de développement.  
  
[Jeux de données](../data-tools/dataset-tools-in-visual-studio.md)  
La plus ancienne de ces trois technologies de modélisation. Il est principalement destiné à développer rapidement des applications de « formulaires de données » dans lequel vous ne sont pas le traitement de grandes quantités de données ou effectuer des requêtes complexes ou des transformations. Un objet de jeu de données se compose des objets DataTable et DataRow qui logiquement ressemblent beaucoup plus que les objets .NET aux objets de base de données SQL. Pour les applications relativement simples basées sur des sources de données SQL, les jeux de données peut-être encore être un bon choix.  
  
Il n’est pas obligatoire d’utiliser ces technologies. Dans certains scénarios, surtout lorsque les performances sont critiques, vous pouvez simplement utiliser un objet DataReader pour lire à partir de la base de données et copiez les valeurs dont vous avez besoin dans un objet de collection telles que liste\<T >.  
  
### <a name="native-c"></a>C++ natif  
Les applications C++ qui se connectent à SQL Server doivent utiliser le [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) dans la plupart des cas. Si les serveurs sont liés, OLE DB est nécessaire et que vous utilisez le [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Vous pouvez accéder à des autres bases de données à l’aide de [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou pilotes OLE DB directement. ODBC est l’interface de base de données standard en cours, mais la plupart des systèmes de base de données fournissent des fonctionnalités personnalisées qui ne sont pas accessibles via l’interface ODBC. OLE DB est une technologie d’accès aux données COM héritée qui est toujours pris en charge mais non recommandée pour les nouvelles applications. Pour plus d’informations, consultez [accès aux données dans Visual C++](https://docs.microsoft.com/cpp/data/).  
  
Les programmes C++ qui utilisent des services REST peuvent utiliser le [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).  
  
Les programmes C++ qui fonctionnent avec Microsoft Azure Storage peuvent utiliser le [Client de stockage Microsoft Azure](http://www.nuget.org/packages/wastorage).
  
Modélisation des données &mdash; Visual Studio ne fournit pas d’une couche ORM pour C++. [ODB](http://www.codesynthesis.com/products/odb/) est un ORM open source populaire pour C++.  

Pour en savoir plus sur la connexion aux bases de données à partir d’applications C++, consultez [Visual Studio data tools pour C++](../data-tools/visual-studio-data-tools-for-cpp.md). Pour plus d’informations sur les technologies d’accès aux données Visual C++ hérités, consultez [accès aux données](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b).
  
### <a name="javascript"></a>JavaScript  
[JavaScript dans Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) est un langage de premier ordre pour la création des applications multiplateformes, les applications UWP, services de cloud computing, sites Web et applications web. Pour installer les bibliothèques JavaScript favorites et des produits de base de données, vous pouvez utiliser Bower, Grunt, Gulp, npm et NuGet à partir de Visual Studio. Se connecter aux services de stockage Azure et en téléchargeant les kits de développement logiciel à partir de la [site Web Azure](https://azure.microsoft.com/). Edge.js est une bibliothèque qui se connecte côté serveur JavaScript (Node.js) à des sources de données ADO.NET.  
  
### <a name="python"></a>Python  
Installer [outils Python pour Visual Studio](http://microsoft.github.io/PTVS/) en même temps que votre infrastructure de Python favoris pour créer des applications de CPython ou IronPython (.NET). Les outils Python pour le site Web de Visual Studio possède plusieurs didacticiels sur la connexion aux données, y compris [Django et la base de données SQL Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django et MySQL sur Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) et [d’eau et MongoDB sur Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).
  
## <a name="related-topics"></a>Rubriques connexes  
 [Analytique, les périphériques et les données](https://msdn.microsoft.com/data-and-devices)  
 Fournit une introduction au cloud intelligent Microsoft, y compris Cortana Analytique Suite et prise en charge de l’Internet des objets.  
  
 [Microsoft Azure Storage](https://azure.microCsoft.com/documentation/services/storage/)  
 Décrit le stockage Azure et comment créer des applications à l’aide de fichiers, les tables, les files d’attente et les objets BLOB Windows Azure.  
  
 [Base de données SQL Azure](https://azure.microsoft.com/documentation/services/sql-database/)  
 Décrit comment se connecter à la base de données SQL Azure, une base de données relationnelle en tant que service.  
  
 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 Décrit les outils qui simplifient la conception, exploration, tester et déployer des bases de données et des applications de données connectées.  
  
 [ADO.NET](/dotnet/framework/data/adonet/index)  
 Décrit l’architecture ADO.NET et comment utiliser les classes ADO.NET pour gérer les données d’application et interagir avec les sources de données et XML.  
  
 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
 Décrit comment créer des applications de données qui permettent aux développeurs de programmer par rapport à un modèle conceptuel au lieu de directement par rapport à une base de données relationnelle.  
  
 [WCF Data Services 4.5](/dotnet/framework/data/wcf/index)  
 Décrit comment utiliser [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] pour déployer des services de données sur le web ou un intranet qui implémentent la [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).  
  
 [Données dans les solutions Office](/office-dev/office-dev/data-in-office-solutions)  
 Contient des liens vers des rubriques qui expliquent comment fonctionnent les données dans les solutions Office. Cela inclut des informations sur la programmation orientée schéma, la mise en cache des données et accès aux données côté serveur.  
  
 [LINQ (Language Integrated Query)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Décrit les fonctionnalités de requête intégrées dans c# et Visual Basic et que le modèle commun pour interroger des bases de données relationnelles, les documents XML, les jeux de données et les collections en mémoire.
  
 [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)  
 Décrit l’utilisation de fonctionnalités XML du .NET Framework de données, le débogage XSLT, XML et l’architecture de requête XML.  
  
 [Documents et données XML](/dotnet/standard/data/xml/index)  
 Donne une vue d'ensemble d'un jeu de classes complet et intégré qui fonctionne avec les documents et les données XML dans le .NET Framework.