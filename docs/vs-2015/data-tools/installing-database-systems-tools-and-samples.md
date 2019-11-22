---
title: Installation des systèmes de base de données, des outils et des exemples | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299605"
---
# <a name="installing-database-systems-tools-and-samples"></a>Installation de systèmes de base de données, outils et exemples
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio n’inclut pas les systèmes de base de données autres que ceux qu’il utilise en interne. Pour développer une application connectée aux données dans Visual Studio, vous installez généralement le système de base de données sur votre ordinateur de développement local, puis vous déployez l’application et la base de données dans un environnement de production lorsqu’ils sont prêts. Pour que le système de base de données soit accessible à partir des applications .NET et soit visible dans les fenêtres Visual Studio Data Tools, il doit avoir un fournisseur de données ADO.NET. Un fournisseur doit prendre en charge spécifiquement Entity Framework si vous envisagez d’utiliser Entity Data Models dans votre application .NET.     De nombreux fournisseurs sont proposés par le biais du gestionnaire de package NuGet ou de la Galerie Visual Studio.

 Pour le développement SQL, assurez-vous que SQL Server Data Tools est installé dans Visual Studio. Cliquez sur le menu **affichage** . Si vous ne voyez pas Explorateur d’objets SQL Server, accédez au panneau de configuration et modifiez Visual Studio. Dans le programme d’installation, sélectionnez **Microsoft SQL Server Data Tools**.

 Si vous utilisez des API de stockage Azure, installez les émulateurs de stockage Azure sur votre ordinateur local pendant le développement afin d’éviter des frais jusqu’à ce que vous soyez prêt à effectuer le déploiement en production. Pour plus d’informations, consultez [utiliser l’émulateur de stockage Azure pour le développement et le test](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 La liste suivante répertorie certains des systèmes de base de données les plus populaires qui peuvent être utilisés dans les projets Visual Studio. La liste n’est pas exhaustive. Pour obtenir la liste des fournisseurs tiers qui proposent des fournisseurs de données ADO.NET qui permettent une intégration profonde avec les outils Visual Studio, consultez [fournisseurs de données ADO.net](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server est l’offre de base de données phare de Microsoft. SQL Server 2016 offre des performances exceptionnelles, une sécurité avancée et des fonctionnalités de génération de rapports et d’analytique riches et intégrées. Il est fourni dans différentes éditions conçues pour différentes utilisations : de l’analyse commerciale hautement évolutive et hautes performances, à utiliser sur un seul ordinateur. SQL Server Express est une édition complète de SQL Server adaptée pour la redistribution et l’incorporation.  La base de données locale est une édition simplifiée de SQL Server Express qui ne requiert aucune configuration et s’exécute dans le processus de votre application. Vous pouvez télécharger l’un ou l’autre ou les deux produits à partir de [la page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). La plupart des exemples SQL de cette section utilisent SQL Server base de données locale. SQL Server Management Studio (SSMS) est une application de gestion de base de données autonome qui offre plus de fonctionnalités que celles fournies dans Visual Studio Explorateur d’objets SQL Server. Vous pouvez accéder à SSMS à partir du lien précédent.

### <a name="oracle"></a>Oracle
 Vous pouvez télécharger une version payante ou gratuite de la base de données Oracle à partir de la page [réseau de technologie Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Pour la prise en charge au moment du design des Entity Framework et des TableAdapters, vous aurez besoin des [outils de développement Oracle pour Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). D’autres produits officiels d’Oracle, y compris le client instantané Oracle, sont disponibles via le gestionnaire de package NuGet.  Vous pouvez télécharger des exemples de schémas Oracle en suivant les instructions de la [documentation en ligne d’Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

### <a name="mysql"></a>MySQL
 MySQL est un système de base de données Open source populaire qui est largement utilisé dans les entreprises et les sites Web. Les téléchargements pour MySQL, MySQL pour Visual Studio et les produits connexes se trouvent dans [MySQL sur Windows](https://www.mysql.com/why-mysql/windows/).  Les tiers proposent différentes extensions Visual Studio et des applications de gestion autonomes pour MySQL. Vous pouvez parcourir les offres dans le gestionnaire de package NuGet (**outils** > **Gestionnaire de package NuGet** > **gérer les packages NuGet pour la solution**).

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL est un système de base de données relationnel objet Open source gratuit. Pour l’installer sur Windows, vous pouvez le télécharger à partir de la [page de téléchargement de PostgreSQL](http://www.postgresql.org/download/windows/).  Vous pouvez également générer PostgreSQL à partir du code source.  Le système PostgreSQL Core comprend une interface en langage C. De nombreux tiers fournissent des packages NuGet pour l’utilisation de PostgreSQL à partir des applications .NET.  Vous pouvez parcourir les offres dans le gestionnaire de package NuGet (**outils** > **Gestionnaire de package NuGet** > **gérer les packages NuGet pour la solution**). Le package le plus populaire est peut-être fourni par [npgsql.org](http://www.npgsql.org/).

### <a name="sqlite"></a>SQLite
 SQLite est un moteur de base de données SQL incorporé qui s’exécute dans le processus propre à l’application. Vous pouvez le télécharger à partir de la [page de téléchargement de SQLite](http://www.sqlite.org/download.html). De nombreux packages NuGet tiers pour SQLite sont également disponibles. Vous pouvez parcourir les offres dans le gestionnaire de package NuGet (**outils** > **Gestionnaire de package NuGet** > **gérer les packages NuGet pour la solution**).

### <a name="firebird"></a>Firebird
 Firebird est un système de base de données SQL Open source. Vous pouvez le télécharger à partir de la [page de téléchargement de Firebird](http://firebirdsql.org/en/downloads/). Un fournisseur de données ADO.NET est disponible via le gestionnaire de package NuGet.

## <a name="see-also"></a>Voir aussi
 [Guide pratique pour déterminer la version et l’édition de SQL Server et de ses composants](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
