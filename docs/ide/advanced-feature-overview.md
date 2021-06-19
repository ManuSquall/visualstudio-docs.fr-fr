---
title: Fonctionnalités avancées
description: Découvrez les fonctionnalités avancées qui peuvent être plus adaptées aux développeurs expérimentés ou aux développeurs qui connaissent déjà Visual Studio.
ms.custom: vs-acquisition
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6cc6604816921b054b0c909177c8e641493920a8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386194"
---
# <a name="features-of-visual-studio"></a>Fonctionnalités de Visual Studio

L’article [Vue d’ensemble de l’IDE Visual Studio](../get-started/visual-studio-ide.md) fournit une présentation générale de Visual Studio. Cet article décrit des fonctionnalités qui peuvent être plus appropriées pour les développeurs expérimentés ou déjà familiarisés avec Visual Studio.

## <a name="modular-installation"></a>Installation modulaire

Le programme d’installation modulaire de Visual Studio vous permet de choisir et d’installer des *charges de travail*. Les charges de travail sont des groupes de fonctionnalités nécessaires au langage de programmation ou à la plateforme que vous préférez. Cette stratégie permet de réduire l’espace dédié à l’installation de Visual Studio, ce qui implique également une installation et des mises à jour plus rapides.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

Pour en savoir plus sur la configuration de Visual Studio sur votre système, consultez [Installer Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Créer des applications cloud pour Azure

Visual Studio propose une suite d’outils qui facilitent la création d’applications Cloud alimentées par Microsoft Azure. Vous pouvez configurer, générer, déboguer, packager et déployer des applications et services sur Microsoft Azure directement à partir de l’IDE. Pour obtenir les outils et modèles de projet Azure, sélectionnez la charge de travail **Développement Azure** lors de l’installation de Visual Studio.

![Charge de travail de développement Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Après avoir installé la charge de travail **développement Azure**, les modèles **cloud** suivants pour C# sont disponibles dans la boîte de dialogue **Nouveau projet** :

![Modèles de projet cloud pour Visual Studio](media/cloud-project-templates.png)

::: moniker-end

[Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) de Visual Studio vous permet d’afficher et de gérer vos ressources cloud Azure dans Visual Studio. Ces ressources peuvent inclure des machines virtuelles, des tables, des bases de données SQL, et bien plus encore. **Cloud Explorer** montre les ressources Azure dans tous les comptes gérés sous l’abonnement Azure auquel vous êtes connecté. Et si une opération particulière nécessite le portail Azure, **Cloud Explorer** fournit des liens vers l’emplacement du portail que vous devez atteindre.

![Cloud Explorer dans Visual Studio](media/cloud-explorer.png)

Vous pouvez exploiter les services Azure pour vos applications à l’aide de **services connectés**, par exemple :

- [Service connecté Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) afin que les utilisateurs puissent utiliser leurs comptes à partir d’[Azure Active Directory](/azure/active-directory/active-directory-whatis) pour se connecter à des applications web
- [Service connecté Stockage Azure](/azure/vs-azure-tools-connected-services-storage) pour le stockage d’objets blob, les files d’attente et les tables
- [Service connecté Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) pour gérer les secrets pour les applications web

Les **services connectés** disponibles dépendent du type de votre projet. Ajoutez un service en cliquant avec le bouton droit sur le projet dans **l’Explorateur de solutions**, puis en choisissant **Ajouter** > **Service connecté**.

![Services connectés de Visual Studio](media/connected-services.png)

Pour plus d’informations, consultez [Accéder au cloud avec Visual Studio et Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Créer des applications pour le web

Le web est le moteur de notre monde moderne et Visual Studio peut vous aider à écrire des applications conçues pour lui. Vous pouvez créer des applications web avec ASP.NET, Node.js, Python, JavaScript et TypeScript. Visual Studio comprend les frameworks web, telles que Angular, jQuery, Express et plus encore. ASP.NET Core et .NET Core s’exécutent sur les systèmes d’exploitation Windows, Mac et Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) est une mise à jour majeure de MVC, WebAPI et SignalR, qui s’exécute sur Windows, Mac et Linux.  ASP.NET Core a été spécialement conçu pour vous fournir une pile .NET adaptée et composable servant à générer des services et des applications web cloud modernes.

Pour plus d’informations, consultez [Outils web modernes](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Créer des applications et des jeux multiplateformes

Visual Studio vous permet de générer des applications et des jeux pour les appareils macOS, Linux et Windows, ainsi qu’Android, iOS et d’autres [appareils mobiles](https://visualstudio.microsoft.com/vs/mobile-app-development/).

- Créez des applications [.net Core](/dotnet/core/) qui s’exécutent sur Windows, MacOS et Linux.

- Générez des applications mobiles pour iOS, Android et Windows en C# et F# à l’aide de [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Générez des jeux en 2D et 3D en c# à l’aide de [Visual Studio Tools pour Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md).

- Générez des applications C++ natives pour les appareils iOS, Android et Windows. Partagez du code commun dans des bibliothèques conçues pour iOS, Android et Windows, à l’aide du [C++ pour le développement multiplateforme](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development).

## <a name="connect-to-databases"></a>Se connecter aux bases de données

**Explorateur de serveurs** vous aide à parcourir et à gérer les instances et les ressources SQL Server localement, à distance et sur Azure, Salesforce.com, Microsoft 365 et sites Web. Pour ouvrir **l’Explorateur de serveurs**, dans le menu principal, choisissez **Affichage** > **Explorateur de serveurs**. Pour plus d’informations sur l’utilisation de l’Explorateur de serveurs, consultez [Ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) est un environnement de développement puissant pour SQL Server, Azure SQL Database et Azure SQL Data Warehouse. Il vous permet de générer, déboguer, gérer et refactoriser des bases de données. Vous pouvez travailler avec un projet de base de données, ou directement avec une instance de base de données connectée, locale ou hors site.

L’**Explorateur d’objets SQL Server** de Visual Studio offre une vue des objets de base de données similaire à celle de SQL Server Management Studio. L’Explorateur d’objets SQL Server vous permet d’effectuer des travaux légers de conception et d’administration de base de données. Voici quelques exemples de travaux : modification de données de tables, comparaison de schémas, exécution de requêtes à l’aide de menus contextuels directement à partir de l’Explorateur d’objets SQL Server, etc.

![Explorateur d’objets SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Déboguer, tester et améliorer votre code

Lorsque vous écrivez du code, vous devez l’exécuter, tester ses performances et rechercher les bogues. Le système de débogage de pointe de Visual Studio vous permet de déboguer du code en cours d’exécution dans votre projet local, sur un appareil distant ou sur un [émulateur d’appareil](../cross-platform/visual-studio-emulator-for-android.md). Vous pouvez parcourir le code instruction par instruction et en examiner les variables. Vous pouvez définir des points d’arrêt qui sont atteints seulement quand une condition spécifiée a la valeur true. Vous pouvez gérer les options de débogage dans l’éditeur de code lui-même, pour ne pas avoir à quitter votre code. Pour en savoir plus sur le processus de débogage de Visual Studio, consultez [Visite guidée du débogueur](../debugger/debugger-feature-tour.md).

Pour en savoir plus sur l’amélioration des performances de vos applications, consultez les fonctionnalités de [profilage](../profiling/profiling-feature-tour.md) de Visual Studio.

À des fins de [test](../test/improve-code-quality.md), Visual Studio propose des tests unitaires, Live Unit Testing, IntelliTest, des tests de charge et de performances, et bien plus encore. Visual Studio dispose également de fonctionnalités d’[analyse du code](../code-quality/code-analysis-for-managed-code-overview.md) avancées pour intercepter les failles de conception, les failles de sécurité, ainsi que d’autres types de failles.

## <a name="deploy-your-finished-application"></a>Déployer votre application terminée

Quand votre application est prête à être déployée auprès d’utilisateurs ou de clients, Visual Studio fournit les outils pour le faire. Les options de déploiement incluent Microsoft Store ou un site SharePoint ainsi que l’utilisation des technologies InstallShield ou Windows Installer. Ils sont tous accessibles via l’IDE. Pour plus d’informations, consultez [Déployer des applications, des services et des composants](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Gérer votre code source et collaborer avec d’autres utilisateurs

Vous pouvez gérer votre code source dans des dépôts Git hébergés par tous types de fournisseurs, notamment GitHub. Vous pouvez aussi utiliser [Azure DevOps Services](/azure/devops/index) pour gérer le code, ainsi que les bogues et les éléments de travail de tout votre projet. Pour en savoir plus sur la gestion des dépôts Git dans Visual Studio avec Team Explorer, consultez la page [Bien démarrer avec Git et Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio). Visual Studio dispose également d’autres fonctionnalités de contrôle de code source intégrées. Pour plus d’informations sur ces fonctionnalités, consultez le billet de blog [New Git Features in Visual Studio](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services est un ensemble de services cloud qui permettent la planification, l’hébergement, l’automatisation et le déploiement des logiciels ainsi que la collaboration entre équipes. Azure DevOps Services prend en charge les dépôts Git (gestion de versions distribuée) et Team Foundation Version Control (gestion de versions centralisée). Il prend en charge les pipelines de build et de mise en production en continu (CI/CD) du code stocké dans les systèmes de gestion de versions. Azure DevOps Services prend également en charge les méthodologies de développement Scrum, CMMI et Agile.

Team Foundation Server (TFS) est le hub de gestion du cycle de vie des applications pour Visual Studio. Il permet à toutes personnes impliquées dans le processus de développement de participer à une même solution. TFS est également utile pour la gestion des équipes et des projets hétérogènes.

Si vous avez une organisation Azure DevOps ou Team Foundation Server sur votre réseau, utilisez la fenêtre **Team Explorer** dans Visual Studio pour vous y connecter. Depuis cette fenêtre, vous pouvez vérifier le code dans ou en dehors du contrôle de code source, gérer des éléments de travail, démarrer des builds et accéder aux salles d'équipe et aux espaces de travail. Vous pouvez ouvrir **Team Explorer** à partir de la zone de recherche, ou dans le menu principal depuis **Affichage** > **Team Explorer** ou depuis **Équipe** > **Gérer les connexions**.

L’illustration suivante montre la fenêtre **Team Explorer** pour une solution qui est hébergée dans Azure DevOps Services.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

Vous pouvez automatiser votre processus de génération pour générer le code que les développeurs de votre équipe ont archivé dans la gestion de versions. Par exemple, vous pouvez générer un ou plusieurs projets la nuit ou chaque fois le code est archivé. Pour plus d’informations, consultez [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="extend-visual-studio"></a>Étendre Visual Studio

Si Visual Studio ne dispose pas de la fonctionnalité exacte dont vous avez besoin, vous pouvez l’ajouter ! Vous pouvez personnaliser l’IDE en fonction de votre flux de travail et du style, ajouter la prise en charge des outils externes non intégrés à Visual Studio et modifier des fonctionnalités existantes pour accroître votre productivité. Pour obtenir la dernière version des outils d’extensibilité de Visual Studio (Visual Studio SDK), consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Vous pouvez utiliser « Roslyn » (.NET Compiler Platform) pour écrire vos propres analyseurs et générateurs de code. Trouvez tout ce dont vous avez besoin sur [Roslyn](https://github.com/dotnet/Roslyn).

Découvrez les [extensions existantes](https://marketplace.visualstudio.com/vs) pour Visual Studio créées par des développeurs Microsoft et notre communauté de développement.

Pour en savoir plus sur l’extension de Visual Studio, consultez [Étendre l’IDE de Visual Studio](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’IDE de Visual Studio](../get-started/visual-studio-ide.md)
- [Nouveautés de Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Nouveautés de Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)
