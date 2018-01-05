---
title: "Compatibilité de base de données Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: af76fad7d6288aff08de22b076d27cafbb5c3cff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="compatible-database-systems-for-visual-studio"></a>Systèmes de base de données compatible pour Visual Studio

Pour développer une application de connexion de données dans Visual Studio, votre généralement installer le système de base de données sur votre ordinateur de développement local, puis déployer l’application et la base de données dans un environnement de production lorsqu’elles sont prêtes. Visual Studio installe SQL Server Express LocalDB sur votre ordinateur dans le cadre de la **stockage de données et de traitement** la charge de travail. Cette instance de base de données locale est utile pour le développement d’applications de données connectées rapidement et facilement.

Pour un système de base de données doit être accessible à partir d’applications .NET et pour être visible dans les fenêtres outils de données Visual Studio, il doit avoir un fournisseur de données ADO.NET. Un fournisseur doit prendre spécifiquement en charge Entity Framework si vous envisagez d’utiliser des modèles de données d’entité dans votre application .NET. De nombreux fournisseurs sont proposées par le biais du Gestionnaire de Package NuGet ou via le Marketplace Visual Studio.

Si vous utilisez l’API de stockage Azure, installez les émulateurs de stockage Azure sur votre ordinateur local pendant le développement afin d’éviter des frais jusqu'à ce que vous êtes prêt à déployer en production. Pour plus d’informations, consultez [utiliser l’émulateur de stockage Azure pour le développement et le test](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).

La liste suivante inclut certains des systèmes de base de données plus populaires qui peuvent être utilisés dans les projets Visual Studio. La liste n’est pas exhaustive. Pour obtenir la liste des fournisseurs tiers qui offrent des fournisseurs de données ADO.NET qui permettent l’intégration en profondeur avec les outils de Visual Studio, consultez [fournisseurs de données ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server est la base de données Microsoft phare de l’offre. SQL Server 2016 offre des performances élevées, de fonctions avancées de sécurité et d’intégré complet, le rapport et de l’analytique. Il est fourni dans les différentes éditions qui sont conçues pour différentes utilisations : à partir de l’analytique d’entreprise hautement évolutive et hautes performances, à utiliser sur un seul ordinateur. SQL Server Express est une version complète de SQL Server qui est adaptée pour la redistribution et l’incorporation.  LocalDB est une version simplifiée de SQL Server Express qui ne nécessite aucune configuration et s’exécute dans le processus de votre application. Vous pouvez télécharger un ou les deux produits à partir de [la page de téléchargement de SQL Server Express](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx). La plupart des exemples SQL dans cette section utilisent SQL Server LocalDB. SQL Server Management Studio (SSMS) est une application de gestion de base de données autonome qui possède plus de fonctionnalités que celui fourni dans l’Explorateur d’objets Visual Studio SQL Server. Vous pouvez obtenir SSMS à partir du lien précédent.

## <a name="oracle"></a>Oracle

Vous pouvez télécharger une version payante ou gratuite de la base de données Oracle à partir de la [Oracle Technology Network](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) page. Pour une prise en charge au moment du design pour Entity Framework et les TableAdapters, vous devez le [Oracle Developer Tools pour Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Autres produits Oracle officiels, y compris le Client instantané Oracle, sont disponibles via le Gestionnaire de Package NuGet.  Vous pouvez télécharger des exemples de schémas Oracle en suivant les instructions de la [Documentation en ligne d’Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL est un système de base de données open source populaire qui est largement utilisé dans les entreprises et les sites Web. Téléchargements pour MySQL, MySQL pour Visual Studio et les produits associés sont à [MySQL sur Windows](http://www.mysql.com/why-mysql/windows/).  Des tiers offrent des différentes extensions Visual Studio et les applications de gestion autonome pour MySQL. Vous pouvez parcourir les offres dans le Gestionnaire de Package NuGet (**outils** > **Gestionnaire de Package NuGet** > **gérer les Packages NuGet pour la Solution**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL est un système de base de données relationnelle objet libre et open source. Pour l’installer sur Windows, vous pouvez le télécharger à partir de la [page de téléchargement PostgreSQL](http://www.postgresql.org/download/windows/).  Vous pouvez également générer PostgreSQL à partir du code source.  Le système principal PostgreSQL inclut une interface en langage C. Nombre de tiers fournissent les packages NuGet pour l’utilisation de PostgreSQL à partir d’applications .NET.  Vous pouvez parcourir les offres dans le Gestionnaire de Package NuGet (**outils** > **Gestionnaire de Package NuGet** > **gérer les Packages NuGet pour la Solution**) . Par exemple, le package les plus populaires est fourni par [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite est un moteur de base de données SQL incorporé qui s’exécute dans le processus de l’application. Vous pouvez le télécharger à partir de la [page de téléchargement de SQLite](http://www.sqlite.org/download.html). Plusieurs packages NuGet tiers SQLite sont également disponibles. Vous pouvez parcourir les offres dans le Gestionnaire de Package NuGet (**outils** > **Gestionnaire de Package NuGet** > **gérer les Packages NuGet pour la Solution**) .

## <a name="firebird"></a>Toute

Toute est un système de base de données SQL open source. Vous pouvez le télécharger à partir de la [page de téléchargement de toute](http://firebirdsql.org/en/downloads/). Un fournisseur de données ADO.NET est disponible via le Gestionnaire de Package NuGet.

## <a name="see-also"></a>Voir aussi

[Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Comment déterminer la version et l’édition de SQL Server et ses composants](http://support.microsoft.com/kb/321185)