---
title: Compatibilité de la base de données
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfc3b6c3adc5c51cbbc4bc7d91338fd3595ec372
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586404"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Systèmes de base de données compatibles pour Visual Studio

Pour développer une application connectée aux données dans Visual Studio, vous installez généralement le système de base de données sur votre ordinateur de développement local, puis vous déployez l’application et la base de données dans un environnement de production lorsqu’ils sont prêts. Visual Studio installe SQL Server Express base de données locale sur votre ordinateur dans le cadre de la charge de travail de **stockage et de traitement des données** . Cette instance de base de données locale est utile pour développer des applications connectées rapidement et facilement.

Pour qu’un système de base de données soit accessible à partir des applications .NET et apparaisse dans les fenêtres Visual Studio Data Tools, il doit avoir un fournisseur de données ADO.NET. Un fournisseur doit prendre en charge spécifiquement Entity Framework si vous envisagez d’utiliser Entity Data Models dans votre application .NET. De nombreux fournisseurs sont proposés par le biais du gestionnaire de package NuGet ou de l’Visual Studio Marketplace.

Si vous utilisez des API de stockage Azure, installez les émulateurs de stockage Azure sur votre ordinateur local pendant le développement afin d’éviter des frais jusqu’à ce que vous soyez prêt à effectuer le déploiement en production. Pour plus d’informations, consultez [utiliser l’émulateur de stockage Azure pour le développement et le test](/azure/storage/common/storage-use-emulator).

La liste suivante répertorie certains des systèmes de base de données les plus populaires qui peuvent être utilisés dans les projets Visual Studio. La liste n’est pas exhaustive. Pour obtenir la liste des fournisseurs tiers qui proposent des fournisseurs de données ADO.NET qui permettent une intégration profonde avec les outils Visual Studio, consultez [fournisseurs de données ADO.net](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server est l’offre de base de données phare de Microsoft. SQL Server 2016 offre des performances exceptionnelles, une sécurité avancée et des fonctionnalités de génération de rapports et d’analytique riches et intégrées. Il est fourni dans différentes éditions conçues pour différentes utilisations : de l’analyse commerciale hautement évolutive et hautes performances, à utiliser sur un seul ordinateur. SQL Server Express est une édition complète de SQL Server adaptée pour la redistribution et l’incorporation.  La base de données locale est une édition simplifiée de SQL Server Express qui ne requiert aucune configuration et s’exécute dans le processus de votre application. Vous pouvez télécharger l’un ou l’autre ou les deux produits à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). La plupart des exemples SQL de cette section utilisent SQL Server base de données locale. SQL Server Management Studio (SSMS) est une application de gestion de base de données autonome qui offre plus de fonctionnalités que celles fournies dans Visual Studio Explorateur d’objets SQL Server. Vous pouvez accéder à SSMS à partir du lien précédent.

## <a name="oracle"></a>Oracle

Vous pouvez télécharger une version payante ou gratuite de la base de données Oracle à partir de la page [réseau de technologie Oracle](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) . Pour la prise en charge au moment du design des Entity Framework et des TableAdapters, vous aurez besoin des [outils de développement Oracle pour Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). D’autres produits officiels d’Oracle, y compris le client instantané Oracle, sont disponibles via le gestionnaire de package NuGet. Vous pouvez télécharger des exemples de schémas Oracle en suivant les instructions de la [documentation en ligne d’Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL est un système de base de données Open source populaire qui est largement utilisé dans les entreprises et les sites Web. Les téléchargements pour MySQL, MySQL pour Visual Studio et les produits connexes se trouvent dans [MySQL sur Windows](https://www.mysql.com/why-mysql/windows/). Les tiers proposent différentes extensions Visual Studio et des applications de gestion autonomes pour MySQL. Vous pouvez parcourir les offres dans le gestionnaire de package NuGet (**outils** > **Gestionnaire de package NuGet** > **gérer les packages NuGet pour la solution**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL est un système de base de données relationnel objet Open source gratuit. Pour l’installer sur Windows, vous pouvez le télécharger à partir de la [page de téléchargement de PostgreSQL](https://www.postgresql.org/download/windows/). Vous pouvez également générer PostgreSQL à partir du code source. Le système PostgreSQL Core comprend une interface en langage C. De nombreux tiers fournissent des packages NuGet pour l’utilisation de PostgreSQL à partir des applications .NET. Vous pouvez parcourir les offres dans le gestionnaire de package NuGet (**outils** > **Gestionnaire de package NuGet** > **gérer les packages NuGet pour la solution**). Par exemple, le package le plus populaire est fourni par [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite est un moteur de base de données SQL incorporé qui s’exécute dans le processus propre à l’application. Vous pouvez le télécharger à partir de la [page de téléchargement de SQLite](https://www.sqlite.org/download.html). De nombreux packages NuGet tiers pour SQLite sont également disponibles. Vous pouvez parcourir les offres dans le gestionnaire de package NuGet (**outils** > **Gestionnaire de package NuGet** > **gérer les packages NuGet pour la solution**).

## <a name="firebird"></a>Firebird

Firebird est un système de base de données SQL Open source. Vous pouvez le télécharger à partir de la [page de téléchargement de Firebird](http://firebirdsql.org/en/downloads/). Un fournisseur de données ADO.NET est disponible via le gestionnaire de package NuGet.

## <a name="see-also"></a>Voir aussi

- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Guide pratique pour déterminer la version et l’édition de SQL Server et de ses composants](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
