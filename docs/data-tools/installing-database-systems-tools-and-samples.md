---
title: Compatibilité de base de données
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 064e6042e734b5564c1f7270ef41a1747919b877
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880323"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Systèmes de base de données compatibles pour Visual Studio

Pour développer une application connecté aux données dans Visual Studio, votre généralement installer le système de base de données sur votre ordinateur de développement local, puis déployer l’application et la base de données dans un environnement de production lorsqu’elles sont prêtes. Visual Studio installe SQL Server Express LocalDB sur votre ordinateur dans le cadre de la **stockage de données et de traitement** charge de travail. Cette instance de base de données locale est utile pour le développement d’applications connectées avec données rapidement et facilement.

Pour un système de base de données soient accessibles à partir d’applications .NET et à être visible dans les fenêtres outils de données Visual Studio, il doit avoir un fournisseur de données ADO.NET. Un fournisseur doit prendre spécifiquement en charge Entity Framework si vous envisagez d’utiliser des modèles de données d’entité dans votre application .NET. De nombreux fournisseurs sont proposées via le Gestionnaire de Package NuGet ou via la place de marché Visual Studio.

Si vous utilisez l’API de stockage Azure, installez les émulateurs de stockage Azure sur votre ordinateur local pendant le développement afin d’éviter des frais jusqu'à ce que vous êtes prêt à déployer en production. Pour plus d’informations, consultez [utiliser l’émulateur de stockage Azure pour le développement et test](/azure/storage/common/storage-use-emulator).

La liste suivante répertorie certains des systèmes de base de données plus populaires qui peuvent être utilisés dans les projets Visual Studio. La liste n’est pas exhaustive. Pour obtenir la liste de fournisseurs tiers qui proposent des fournisseurs de données ADO.NET qui permettent l’intégration approfondie avec les outils de Visual Studio, consultez [fournisseurs de données ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server est la base de données de phare de Microsoft offre. SQL Server 2016 offre des performances fiables, de fonctions avancées de sécurité et de création de rapports riches et intégrées et analytique. Il est fourni dans les différentes éditions qui sont conçues pour différentes utilisations : à partir d’analytique métier hautement évolutive et hautes performances, à utiliser sur un seul ordinateur. SQL Server Express est une édition complète de SQL Server qui est adapté à la redistribution et l’incorporation.  LocalDB est une édition simplifiée de SQL Server Express qui ne nécessite aucune configuration et s’exécute dans le processus de votre application. Vous pouvez télécharger un ou les deux produits à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). La plupart des exemples SQL dans cette section utilisent SQL Server LocalDB. SQL Server Management Studio (SSMS) est une application de gestion de base de données autonome qui comporte davantage de fonctionnalités que celui fourni dans l’Explorateur d’objets Visual Studio SQL Server. Vous pouvez obtenir SSMS à partir du lien précédent.

## <a name="oracle"></a>Oracle

Vous pouvez télécharger une édition payante ou gratuite de la base de données Oracle à partir de la [réseau de la technologie Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) page. Pour une prise en charge au moment du design pour Entity Framework et les TableAdapters, vous devez le [outils de développement de Oracle pour Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Autres produits Oracle officielles, y compris Oracle Instant Client, sont disponibles via le Gestionnaire de Package NuGet. Vous pouvez télécharger des exemples de schémas Oracle en suivant les instructions fournies dans le [documentation en ligne Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL est un système de base de données open source populaire qui est largement utilisé dans les entreprises et les sites Web. Téléchargements pour MySQL, MySQL pour Visual Studio et les produits connexes sont à [MySQL sur Windows](http://www.mysql.com/why-mysql/windows/). Des tiers offrent différentes extensions de Visual Studio et les applications de gestion autonome pour MySQL. Vous pouvez parcourir les offres dans le Gestionnaire de Package NuGet (**outils** > **Gestionnaire de Package NuGet** > **gérer les Packages NuGet pour la Solution**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL est un système de base de données relationnelle objet gratuit, open source. Pour l’installer sur Windows, vous pouvez le télécharger à partir de la [page de téléchargement de PostgreSQL](http://www.postgresql.org/download/windows/). Vous pouvez également créer PostgreSQL à partir du code source. Le système de core PostgreSQL inclut une interface de langage C. Nombre de tiers fournissent les packages NuGet pour l’utilisation de PostgreSQL à partir d’applications .NET. Vous pouvez parcourir les offres dans le Gestionnaire de Package NuGet (**outils** > **Gestionnaire de Package NuGet** > **gérer les Packages NuGet pour la Solution**) . Par exemple, le package le plus populaire est fourni par [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite est un moteur de base de données SQL incorporé qui s’exécute dans le processus de l’application. Vous pouvez le télécharger à partir de la [page de téléchargement de SQLite](http://www.sqlite.org/download.html). Plusieurs packages NuGet tiers SQLite sont également disponibles. Vous pouvez parcourir les offres dans le Gestionnaire de Package NuGet (**outils** > **Gestionnaire de Package NuGet** > **gérer les Packages NuGet pour la Solution**) .

## <a name="firebird"></a>Firebird

Firebird est un système de base de données SQL open source. Vous pouvez le télécharger à partir de la [page de téléchargement Firebird](http://firebirdsql.org/en/downloads/). Un fournisseur de données ADO.NET est disponible via le Gestionnaire de Package NuGet.

## <a name="see-also"></a>Voir aussi

- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Guide pratique pour déterminer la version et l’édition de SQL Server et de ses composants](http://support.microsoft.com/kb/321185)