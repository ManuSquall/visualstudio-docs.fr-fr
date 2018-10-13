---
title: L’accès aux données dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: eacf075a0ba8689ff0cb5ca822d5cc8ca2f7ad1e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233900"
---
# <a name="accessing-data-in-visual-studio"></a>L’accès aux données dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Dans Visual Studio, vous pouvez créer des applications qui se connectent à des données dans n’importe quel produit de base de données ou un service, dans n’importe quel format, n’importe où, sur un ordinateur local, sur un réseau local, ou dans un cloud public, privé ou hybride.  
  
 Pour les applications avec JavaScript, Python, PHP, Ruby ou C++, vous connectez aux données comme vous le faites rien d’autre, en obtenant des bibliothèques et d’écriture de code. Pour les applications .NET, Visual Studio fournit des outils que vous pouvez utiliser pour Explorer les sources de données, créer des modèles d’objet pour stocker et manipuler des données en mémoire et lier des données à l’interface utilisateur.     Microsoft Azure fournit des kits SDK pour .NET, Java, Node.js, PHP, Python, Ruby et les applications mobiles et les outils dans Visual Studio pour la connexion au stockage Azure.  
  
 Les listes suivantes présentent quelques-uns des nombreux systèmes base de données et de stockage qui peuvent être utilisés à partir de Visual Studio. Le [Microsoft Azure](https://azure.microsoft.com/en-us/) offres sont des services de données qui incluent tous les d’approvisionnement et d’administration de la banque de données sous-jacente.  [Azure Tools pour Visual Studio](https://www.visualstudio.com/en-us/features/azure-tools-vs.aspx) est un composant facultatif qui vous permet de travailler avec des banques de données Azure directement à partir de Visual Studio. La plupart des autres SQL et NoSQL de base de données produits répertoriés ici peut être hébergée sur un ordinateur local, sur un réseau local ou dans Microsoft Azure sur une machine virtuelle. Dans ce scénario, vous êtes responsable de la gestion de la base de données.  
  
 **Microsoft Azure**  
  
||||  
|-|-|-|  
|Base de données SQL|DocumentDB|Stockage (objets BLOB, tables, files d’attente, fichiers)|  
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|  
  
 Et plus encore...  
  
 **SQL**  
  
||||  
|-|-|-|  
|SQL Server 2005 – 2016, y compris Express et base de données locale|Firebird|MariaDB|  
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
  
 Plusieurs fournisseurs de base de données et les tiers en charge l’intégration de Visual Studio par les packages NuGet. Vous pouvez explorer les offres sur nuget.org ou via le Gestionnaire de Package NuGet dans Visual Studio (**outils** > **Gestionnaire de Package NuGet** > **gérer NuGet Packages de Solution**). Autres produits de base de données s’intègrent avec Visual Studio en tant qu’extension.   Vous pouvez parcourir ces offres dans la galerie Visual Studio en accédant à **outils** > **Extensions et mises à jour** , puis en sélectionnant **Online** à gauche volet de la boîte de dialogue.  Pour plus d’informations, consultez [l’installation de systèmes de base de données, des outils et des exemples](../data-tools/installing-database-systems-tools-and-samples.md).  
  
> [!NOTE]
>  Le support étendu pour SQL Server 2005 a pris fin le 12 avril 2016.   Il n’existe aucune garantie que les outils de données dans Visual Studio 2015 et versions ultérieures continueront de fonctionner avec SQL Server 2005 après cette date. Pour plus d’informations, consultez le [annonce de fin de support pour SQL Server 2005](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).  
  
### <a name="net-languages"></a>Langages .NET  
 Tous les accès aux données .NET, y compris dans .NET Core, est basé sur ADO.NET, un ensemble de classes qui définit une interface pour accéder à n’importe quel type de source de données relationnel et non relationnelles. Visual Studio dispose de plusieurs outils et concepteurs qui fonctionnent avec ADO.NET pour vous aider à vous connecter aux bases de données, manipuler les données et présenter les données à l’utilisateur. La documentation de cette section décrit comment utiliser ces outils. Vous pouvez également programmer directement les objets de commande ADO.NET. Pour plus d’informations sur l’appel de directement les APIs ADO.NET, consultez [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) dans MSDN Library.  
  
 Pour obtenir une documentation accès aux données spécifiquement liée à ASP.NET, consultez [utilisation des données](http://www.asp.net/web-forms/overview/presenting-and-managing-data) sur le site ASP.NET. Pour obtenir un didacticiel sur l’utilisation d’Entity Framework avec ASP.NET MVC, consultez [mise en route avec Entity Framework 6 Code First avec MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).  
  
 Des applications de Windows Platform (UWP) universelle en c# ou Visual Basic peuvent utiliser le Kit de développement logiciel Microsoft Azure pour .NET pour accéder à stockage Azure et autres services Azure. La classe Windows.Web.HttpClient permet la communication avec n’importe quel service RESTful. Pour plus d’informations, consultez [comment se connecter à un serveur HTTP à l’aide de Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx.)  
  
 Stockage des données sur l’ordinateur local, l’approche recommandée consiste à utiliser SQLite, qui s’exécute dans le même processus que l’application. Si une couche de mappage objet-relationnel (ORM) est requise, vous pouvez utiliser Entity Framework. Pour plus d’informations, consultez [accès aux données](https://msdn.microsoft.com/windows/uwp/data-access/index) dans le centre de développement Windows.  
  
 Si vous vous connectez aux services Azure, veillez à télécharger la dernière version [outils du SDK Azure](https://azure.microsoft.com/en-us/downloads/).  
  
#### <a name="data-providers"></a>Fournisseurs de données  
 Pour une base de données être consommable dans ADO.NET, il doit avoir un personnalisé *fournisseur de données ADO.NET* ou else doit exposer une interface ODBC ou OLE DB. Microsoft fournit un [liste des fournisseurs de données ADO.NET](https://msdn.microsoft.com/data/dd363565) pour les produits SQL Server, ainsi que des fournisseurs ODBC et OLE DB.  
  
#### <a name="data-modeling"></a>Modélisation des données  
 Dans .NET, vous avez trois possibilités pour la modélisation et la manipulation de données en mémoire une fois que vous l’avez récupéré à partir d’une source de données :  
  
 Entity Framework  
 La technologie Microsoft ORM préférée. Vous pouvez l’utiliser pour programmer par rapport aux données relationnelles comme des objets .NET. Pour les nouvelles applications, il doit être le premier choix de valeur par défaut lorsqu’un modèle est requis. Elle nécessite la prise en charge personnalisée à partir du fournisseur ADO.NET sous-jacent.  
  
 LINQ to SQL  
 Un mappeur objet-relationnel de génération antérieure. Il fonctionne bien pour les scénarios moins complexes, mais n’est plus en cours de développement.  
  
 Groupes de données  
 Le plus ancien de ces trois technologies de modélisation. Il est conçu principalement pour le développement rapide d’applications de « formulaires de données » dans lequel vous ne sont pas traiter de grandes quantités de données ou effectuer des requêtes complexes ou des transformations. Un objet DataSet comprend des objets DataTable et DataRow logiquement semblables aux objets de base de données SQL beaucoup plus que les objets .NET. Pour les applications relativement simples basées sur des sources de données SQL, les jeux de données peut toujours être un bon choix.  
  
 Il est inutile d’utiliser ces technologies. Dans certains scénarios, en particulier où les performances sont critiques, vous pouvez simplement utiliser un objet DataReader à lire à partir de la base de données et copier les valeurs dont vous avez besoin dans un objet de collection, telles que liste\<T >.  
  
### <a name="native-c"></a>C++ natif  
 Les applications C++ qui se connectent à SQL Server doivent utiliser le [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Vous pouvez accéder aux autres bases de données à l’aide de [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou pilotes OLE DB directement. ODBC est l’interface actuelle de la base de données standard, mais la plupart des systèmes de base de données fournissent des fonctionnalités personnalisées qui ne sont pas accessibles via l’interface ODBC.  OLE DB est une technologie d’accès aux données COM héritée qui est toujours pris en charge mais non recommandée pour les nouvelles applications.  Pour plus d’informations, consultez [accès aux données](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).  
  
 Les programmes C++ qui utilisent des services REST peuvent utiliser le [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).  
  
 Les programmes C++ qui fonctionnent avec Microsoft Azure Storage peuvent utiliser le [Client de stockage Microsoft Azure](http://www.nuget.org/packages/wastorage).  
  
#### <a name="data-modeling"></a>Modélisation des données  
 Visual Studio ne fournit pas d’une couche ORM pour C++.  [ODB](http://www.codesynthesis.com/products/odb/) est un ORM open source populaires pour C++.  
  
 Pour plus d’informations sur les technologies d’accès aux données héritées Visual C++, consultez [accès aux données](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)  
  
### <a name="javascript"></a>JavaScript  
 [JavaScript dans Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) est un langage de premier ordre pour la création des applications multiplateformes, les applications UWP, les services cloud, les sites Web et les applications web. Vous pouvez utiliser Bower, Grunt, Gulp, npm et NuGet à partir de Visual Studio pour installer vos bibliothèques JavaScript favorites et les produits de base de données. Se connecter au stockage Azure et services en téléchargeant les kits de développement logiciel à partir de la [site Web Azure](https://azure.microsoft.com/).  Edge.js est une bibliothèque qui se connecte côté serveur JavaScript (Node.js) à des sources de données ADO.NET.  
  
### <a name="python"></a>Python  
 Installer [Python Tools pour Visual Studio](http://microsoft.github.io/PTVS/) , ainsi que votre infrastructure Python favori pour créer des applications de CPython ou IronPython (.NET).  Les outils Python pour le site Web de Visual Studio a plusieurs didacticiels sur la connexion aux données, notamment [Django et SQL Database sur Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django et MySQL sur Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) et [Bottle et MongoDB sur Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Installation de systèmes de base de données, d’outils et d’exemples](../data-tools/installing-database-systems-tools-and-samples.md)  
 Explique comment obtenir des produits de base de données et les pilotes qui prennent en charge les extensions Visual Studio et où trouver les bases de données pour l’expérimentation et à des fins pédagogiques.  
  
 [Outils de données Visual Studio pour .NET](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)  
 Décrit comment utiliser les fenêtres Outil de Visual Studio pour vous connecter aux sources de données, créer des jeux de données ou modèles Entity Framework et lier les données aux contrôles d’interface utilisateur.  
  
## <a name="related-topics"></a>Rubriques connexes  
 [Analytique, les périphériques et les données](https://msdn.microsoft.com/data-and-devices)  
 Fournit une introduction au cloud intelligent Microsoft, y compris la prise en charge pour l’Internet des objets et la Suite d’Analytique Cortana.  
  
 [Stockage Microsoft Azure](https://azure.microCsoft.com/en-us/documentation/services/storage/)  
 Décrit le stockage Azure et comment créer des applications à l’aide de fichiers, tables, files d’attente et objets BLOB Azure.  
  
 [Azure SQL Database](https://azure.microsoft.com/en-us/documentation/services/sql-database/)  
 Décrit comment se connecter à la base de données SQL Azure, une base de données relationnelle en tant que service.  
  
 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 Décrit les outils qui simplifient la conception, exploration, de test et de déploiement de bases de données et applications de données connectées.  
  
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)  
 Décrit l’architecture ADO.NET et comment utiliser les classes ADO.NET pour gérer les données d’application et interagir avec des sources de données et XML.  
  
 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
 Décrit comment créer des applications de données qui permettent aux développeurs de programmer par rapport à un modèle conceptuel au lieu de directement par rapport à une base de données relationnelle.  
  
 [WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)  
 Décrit comment utiliser [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] pour déployer des services de données sur le web ou un intranet qui implémentent le [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).  
  
 [Données dans les solutions Office](http://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a)  
 Contient des liens vers des rubriques qui expliquent comment fonctionnent les données dans les solutions Office. Cela inclut des informations sur la programmation orientée schéma, la mise en cache des données et accès aux données côté serveur.  
  
 [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Décrit les fonctionnalités de requête intégrées dans c# et Visual Basic et le modèle commun pour interroger des bases de données relationnelles, les documents XML, les jeux de données et les collections en mémoire.  
  
 [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)  
 Décrit l’utilisation des fonctionnalités XML du .NET Framework de données, le débogage XSLT, XML et l’architecture de requête XML.  
  
 [Documents et données XML](http://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380)  
 Donne une vue d'ensemble d'un jeu de classes complet et intégré qui fonctionne avec les documents et les données XML dans le .NET Framework.

