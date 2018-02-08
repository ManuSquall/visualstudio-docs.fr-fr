---
title: "Vue d’ensemble de Visual Studio| Microsoft Docs"
ms.custom: 
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5bde32fc86610fa451aa01659401362fe4207f5c
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-ide-overview"></a>Vue d’ensemble de l’IDE de Visual Studio

L’environnement de développement interactif de Visual Studio (l’IDE) est une plateforme de lancement créative avec laquelle vous pouvez afficher et modifier quasiment tous les types de code, et déboguer, générer et publier des applications Android, iOS, Windows, web et cloud. Des versions sont disponibles pour Mac et Windows. Cette rubrique vous présente les fonctionnalités de l’IDE de Visual Studio. Nous allons vous présenter ce que vous pouvez faire avec Visual Studio, vous expliquer comment installer et utiliser l’IDE et comment créer des projets simples, vous donner des conseils sur le débogage et le déploiement de code, et vous faire découvrir les diverses fenêtres Outil.

## <a name="what-can-you-do-with-the-visual-studio-ide"></a>Que pouvez-vous faire avec l’IDE Visual Studio ?

Vous souhaitez créer une application pour un téléphone Android ? C’est possible. Et qu’en est-il de la création de jeux de pointe à l’aide de C++ ? Cela fait également partie des innombrables possibilités proposées. Visual Studio fournit des modèles qui vous permettent de créer des sites web, des jeux, des applications de bureau, des applications mobiles, des applications pour Office et plus encore.

![Projets Visual Studio](../ide/media/VSIDE_Tour_Projects_List.png)

Vous pouvez aussi tout simplement ouvrir du code que vous avez obtenu d’une source et commencer à travailler. Vous voyez sur GitHub un projet qui vous plaît ? Il vous suffit de cloner le dépôt, de l’ouvrir dans Visual Studio et de commencer à rédiger le code !

### <a name="create-mobile-apps"></a>Créer des applications mobiles

Vous pouvez créer des applications mobiles natives pour différentes plateformes à l’aide de C# et Xamarin ou Visual C++, ou des applications hybrides à l’aide de JavaScript avec Apache Cordova. Vous pouvez créer des jeux mobiles pour Unity, Unreal, DirectX, Cocos, et plus encore. Visual Studio inclut un émulateur Android pour vous aider à exécuter et déboguer des applications Android.

Vous pouvez exploiter la puissance du Cloud pour vos applications mobiles en créant des services d’applications Azure. Les services d’applications Azure permettent à vos applications de stocker des données sur le Cloud, d’authentifier les utilisateurs de manière sécurisée et de faire évoluer automatiquement leurs ressources pour répondre aux besoins de votre application et de votre entreprise. Pour plus d’informations, consultez [Développement d’applications mobiles](https://www.visualstudio.com/vs/mobile-app-development/).

### <a name="create-cloud-apps-for-azure"></a>Créer des applications Cloud pour Azure

Visual Studio propose une suite d’outils qui facilitent la création d’applications Cloud alimentées par Microsoft Azure. Vous pouvez configurer, générer, déboguer, packager et déployer des applications et services sur Microsoft Azure directement à partir de l’IDE. Pour obtenir les outils Azure pour .NET, sélectionnez la charge de travail de **développement Azure** lors de l’installation de Visual Studio. Pour plus d’informations, consultez [Visual Studio Tools pour Azure](https://www.visualstudio.com/vs/azure-tools/).

Vous pouvez exploiter les services Azure pour vos applications à l’aide de services connectés tels que :

- [Azure Mobile Services](http://azure.microsoft.com/documentation/services/mobile-services/)

- [Azure Storage](http://azure.microsoft.com/documentation/services/storage/)

[HockeyApp](https://www.visualstudio.com/hockey-app/) vous aide à distribuer des versions bêta, collecter des rapports d’incidents en direct et obtenir des commentaires de vos utilisateurs. De plus, vous pouvez intégrer les API REST Office 365 à votre propre application pour vous connecter aux données stockées dans le cloud. Pour plus d’informations, consultez [ces exemples GitHub](https://github.com/OfficeDev/?utf8=%E2%9C%93&query=o365).

[Application Insights](https://marketplace.visualstudio.com/items?itemName=VisualStudioOnlineApplicationInsights.application-insights) vous permet de détecter et de diagnostiquer les problèmes de qualité dans vos applications et services web. Application Insights vous aide aussi à comprendre ce que vos utilisateurs font réellement avec votre application, afin d’optimiser l’expérience utilisateur.

### <a name="create-apps-for-the-web"></a>Créer des applications pour le web

Le web est le moteur de notre monde moderne et Visual Studio peut vous aider à écrire des applications conçues pour lui. Vous pouvez créer des applications web à l’aide de ASP.NET, Node.js, Python, JavaScript et TypeScript. Visual Studio comprend les frameworks web, telles que Angular, jQuery, Express et plus encore. ASP.NET Core et .NET Core s’exécutent sur les systèmes d’exploitation Windows, Mac et Linux. [ASP.NET Core](http://www.asp.net/core/overview) est une mise à jour majeure de MVC, WebAPI et SignalR, qui s’exécute sur Windows, Mac et Linux.  ASP.NET Core a été spécialement conçu pour vous fournir une pile .NET adaptée et composable servant à générer des services et des applications web cloud modernes.

Pour plus d’informations, consultez [Outils web modernes](https://www.visualstudio.com/vs/modern-web-tooling/).

### <a name="build-cross-platform-apps-and-games"></a>Créer des applications et des jeux multiplateformes

À l’aide de Visual Studio, créez des applications et des jeux pour les appareils Android, iOS, Linux, Windows, etc. Découvrez-en plus dans [Développement mobile multiplateforme](../cross-platform/cross-platform-mobile-development-in-visual-studio.md). Les applications de la plateforme Windows universelle vous permettent de tirer parti de votre code entre plusieurs plateformes. Consultez la page sur les [applications de la plateforme Windows universelle](https://dev.windows.com/windows-apps) pour plus d’informations.

Choisissez les outils dont vous avez besoin en fonction des exigences de votre application et du langage utilisé :

- [Xamarin pour Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md) : base de code commune en C# pour tous les appareils.

- [Visual Studio Tools pour Apache Cordova](../cross-platform/visual-studio-tools-for-apache-cordova.md) : base de code commune pour HTML, CSS et JavaScript ou Typescript.

- [Visual Studio Tools pour Unity](../cross-platform/visual-studio-tools-for-unity.md) : développement de jeux en 2D/3D en C#.

- [C++ pour développement multiplateforme](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md) : applications et bibliothèques de code partagées en C++.

- [Émulateur Visual Studio pour Android](../cross-platform/visual-studio-emulator-for-android.md) : déboguez et testez vos applications Android, quel que soit l’IDE.

[Créez des jeux à l’aide de Visual Studio](https://www.visualstudio.com/vs/game-development/) avec les outils de développement de jeux tels que DirectX, Unity, Unreal, Cocos et bien d’autres.

Visual Studio peut vous permettre d’effectuer bien d’autres choses. Pour une liste plus complète, consultez [IDE de Visual Studio](https://www.visualstudio.com/vs/).

## <a name="install-the-visual-studio-ide"></a>Installer l’IDE de Visual Studio

Pour commencer, téléchargez Visual Studio et installez-le sur votre système. Vous pouvez le télécharger depuis le site [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).

Visual Studio n’a jamais été si léger ! Le programme d’installation modulaire vous permet de choisir et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités requises pour la plateforme ou le langage de programmation de votre choix. Cette stratégie permet de réduire encore l’espace dédié à l’installation de Visual Studio. Ce qui implique également une plus grande rapidité de l’installation et des mises à jour.

Pour effectuer les étapes de création d’un programme ci-dessous, vous devez sélectionner et installer la charge de travail **Développement pour la plateforme Windows universelle**.

![Programme d’installation de Visual Studio](../ide/media/vside_tour_install_dialog.png)

Visual Studio 2017 offre des performances d’installation améliorées, et des processus de démarrage de l’IDE et de chargement des solutions plus rapides.

Pour en savoir plus sur la configuration de Visual Studio sur votre système, consultez [Installer Visual Studio 2017](../install/install-visual-studio.md).

## <a name="sign-in"></a>Se connecter

Quand vous démarrez Visual Studio pour la première fois, vous pouvez vous connecter avec votre compte Microsoft, ou avec votre compte professionnel ou celui de votre établissement scolaire. Le fait d’être connecté vous permet de synchroniser les paramètres de Visual Studio, tels que les dispositions de fenêtres sur plusieurs appareils. Cela vous permet également de vous connecter aux services dont vous pouvez avoir besoin, tels que les abonnements Azure et Visual Studio Team Services.

## <a name="create-a-program"></a>Créer un programme

Un bon moyen d’en savoir plus sur quelque chose est de l’utiliser ! Nous allons aller plus loin en créant un nouveau programme simple.

1. Ouvrez Visual Studio. Dans le menu, choisissez **Fichier** > **Nouveau** > **Projet**.

  ![capture d’écran](../ide/media/VSIDE_Tour_NewProject1.png)

  Vous pouvez également créer un projet à l’aide de la page de démarrage. Pour plus d’informations, consultez le blog [Harness the Power of the Redesigned Start Page](https://blogs.msdn.microsoft.com/visualstudio/2016/11/29/harness-the-power-of-the-redesigned-start-page/).

1. La boîte de dialogue **Nouveau projet** affiche plusieurs modèles de projet. Choisissez la catégorie **Windows universel** sous **Visual C#**, le modèle **Applications vide (Windows Universel)**, puis cliquez sur le bouton **OK**.

  > [!NOTE]
  > Si vous ne voyez pas la catégorie **Windows universel**, vous devez installer la charge de travail **Développement de la plateforme universelle Windows**. Pour cela, cliquez sur le lien **Ouvrir Visual Studio Installer** en bas à gauche de la boîte de dialogue **Nouveau projet**. Une fois **Visual Studio Installer** lancé, sélectionnez la charge de travail **Développement Universal Windows Platform**, puis choisissez **Modifier**.

  ![Modèle d’application vide UWP](../ide/media/new-uwp-blank-app-template.png)

  Cela crée un nouveau projet d’application Windows universel vide utilisant C# et XAML comme langages de programmation. Patientez jusqu’à ce que Visual Studio configure le projet pour vous. Si vous êtes invité à saisir de nouvelles informations, acceptez simplement les valeurs par défaut pour le moment.

1. Dans la boîte de dialogue **Nouveau projet de plateforme Windows universelle**, acceptez les valeurs par défaut en choisissant **OK**.

1. Quelque chose qui ressemble à la capture d’écran suivante doit bientôt s’afficher. Vos fichiers de projet sont répertoriés sur le côté droit dans une fenêtre appelée Explorateur de solutions.

  ![capture d’écran](../ide/media/VSIDE_Tour_NewProject3.png)

1. Dans l’Explorateur de solutions, cliquez sur le petit triangle noir en regard du fichier MainPage.xaml pour le développer. Un fichier MainPage.xaml.cs doit s’afficher en dessous. Cliquez sur ce fichier (qui contient du code C#) pour l’ouvrir.

  Le code C# du fichier MainPage.xaml.cs apparaît dans l’éditeur de code sur le côté gauche de l’écran. Notez que la syntaxe du code est automatiquement colorisée pour indiquer les différents types de code, tels que les instructions ou les commentaires. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer le code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran.

  ![](../ide/media/VSIDE_Tour_NewProject3a.png)

  Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

1. Ajoutez un bouton au formulaire XAML pour permettre aux utilisateurs d’interagir avec votre application. Pour ce faire, ouvrez le fichier MainPage.xaml. Cet exemple montre un affichage fractionné : un concepteur dans la partie supérieure pour distinguer visuellement les contrôles et un affichage de code dans la partie inférieure, qui affiche le code XAML derrière le concepteur. Quand vous exécutez le programme ultérieurement, ce que vous voyez dans le concepteur devient une fenêtre (un formulaire) visible aux utilisateurs, et le code XAML sous-jacent détermine ce qui apparaît sur ce formulaire.

1. À gauche de l’écran, cliquez sur l’onglet **Boîte à outils** pour ouvrir la boîte à outils. La boîte à outils contient un certain nombre de contrôles visuels que vous pouvez ajouter aux formulaires. Pour l’instant, nous allons nous contenter d’ajouter un bouton de contrôle.

1. Développez la section **Contrôles XAML communs**, puis faites glisser le contrôle du bouton vers le centre du formulaire. L’emplacement exact importe peu.

  ![capture d’écran](../ide/media/VSIDE_Tour_Toolbox.png)

  Lorsque vous avez terminé, l’affichage doit ressembler à ce qui suit.

  ![capture d’écran](../ide/media/VSIDE_Tour_XAMLButton.png)

  Le bouton est dans le concepteur et son code sous-jacent (en surbrillance) est automatiquement ajouté au code XAML du concepteur.

1. Modifions le code XAML. Renommez `Button` en `Hello!` dans le texte du code du bouton.

  ![capture d’écran](../ide/media/VSIDE_Tour_XAMLButton2.png)

1. Maintenant, démarrez l’application. Pour ce faire, cliquez sur le bouton **Démarrer** (![bouton Démarrer](../ide/media/VSIDE_StartButton.png)) de la barre d’outils, appuyez sur la touche **F5** ou choisissez **Déboguer** > **Démarrer le débogage**.

  ![capture d’écran](../ide/media/VSIDE_Tour_RunButton.png)

  L’application commence son processus de génération et les messages d’état apparaissent dans la fenêtre Sortie. Vous ne tarderez pas à voir le formulaire, sur lequel apparaît vote bouton, s’afficher. Maintenant, votre application fonctionne !

  ![capture d’écran](../ide/media/VSIDE_Tour_RunProject.png)

  Bien sûr, ses fonctionnalités restent limitées pour le moment, mais vous pourrez l’améliorer ultérieurement si vous le souhaitez.

1. Lorsque vous avez fini d’exécuter le programme, cliquez sur le bouton![Arrêter](../ide/media/VSIDE_StopButton.png)de la barre d’outils pour l’arrêter.

Récapitulons ce que vous avez fait jusqu’à présent. Vous avez créé un projet Windows universel C# dans Visual Studio, affiché son code, ajouté un contrôle au concepteur, modifié le code XAML et exécuté le projet. Bien que le processus ait été simplifié pour cet exemple, il vous montre certaines parties de l’IDE de Visual Studio, que vous utiliserez lors du développement de vos propres applications courantes. Si vous souhaitez en savoir plus sur cet exemple, consultez [Créer une application « Hello World » (XAML)](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).

## <a name="debug-test-and-improve-your-code"></a>Déboguer, tester et améliorer votre code

Des erreurs peuvent survenir lors de l’exécution. Lorsque vous écrivez du code, vous devez l’exécuter, tester ses performances et rechercher les bogues. Le système de débogage de pointe de Visual Studio vous permet de déboguer du code en cours d’exécution dans votre projet local, sur un appareil distant ou sur un émulateur comme ceux destinés aux appareils Android ou Windows Phone. Vous pouvez parcourir le code instruction par instruction et examiner les variables au fil de la progression, vous pouvez avancer pas à pas dans des applications multithread, et vous pouvez définir des points d'arrêt qui sont atteints seulement quand une condition spécifiée est vraie. Vous pouvez surveiller les valeurs des variables à mesure que le code s’exécute. Tout ceci peut être géré dans l’éditeur de code lui-même, ce qui vous permet de ne pas quitter votre code.

![Débogage](../ide/media/VSIDE_Tour_Debugging.png)

À des fins de test, Visual Studio propose des tests unitaires, IntelliTest, des tests de charge et de performances et bien plus encore. Pour en savoir plus sur le processus de débogage de Visual Studio, consultez [Debugger Feature Tour](../debugger/debugger-feature-tour.md) (Présentation des fonctionnalités de débogage). Pour plus d’informations sur les tests, consultez [Outils et scénarios de test](../test/developer-testing-scenarios.md). Pour en savoir plus sur l’amélioration des performances de vos applications, consultez [Visite guidée des fonctionnalités de profilage](../profiling/profiling-feature-tour.md).

## <a name="deploy-your-finished-application"></a>Déployer votre application terminée

Quand vous êtes prêt à déployer votre application terminée auprès d’utilisateurs ou de clients, Visual Studio vous fournit les outils nécessaires pour effectuer son déploiement dans le Microsoft Store, sur un site SharePoint ou à l’aide des technologies InstallShield ou Windows Installer. Ils sont tous accessibles via l’IDE. Pour plus d’informations, consultez [Déploiement d’applications, de services et de composants](../deployment/deploying-applications-services-and-components.md).

## <a name="quick-tour-of-the-ide"></a>Visite guidée de l’IDE

Pour vous donner une représentation générale de Visual Studio, l’image suivante montre un projet ouvert dans Visual Studio et les fenêtres Outil principales dont vous aurez probablement besoin :

- L’[Explorateur de solutions](../ide/solutions-and-projects-in-visual-studio.md) vous permet d’afficher, de parcourir et de gérer vos fichiers de code. L’Explorateur de solutions peut vous aider à organiser votre code en regroupant les fichiers dans des projets et des solutions.

- La fenêtre [Éditeur](../ide/writing-code-in-the-code-and-text-editor.md) est la fenêtre où vous passerez sans doute le plus de temps. Utilisez cette fenêtre pour afficher votre code, modifier le code source et concevoir une interface utilisateur.

- La fenêtre [Sortie](../ide/reference/output-window.md) est l’emplacement où Visual Studio envoie ses notifications, telles que les messages d’erreur et de débogage, les avertissements du compilateur, les messages d’état de publication, et ainsi de suite. Chaque source de message a son propre onglet.

- [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) vous permet de suivre des éléments de travail et de partager du code avec d’autres utilisateurs à l’aide des technologies de gestion de versions comme [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](/vsts/tfvc/overview).

- [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) vous permet d’afficher et de gérer vos ressources Azure, telles que les machines virtuelles, les tables, les bases de données SQL et bien plus encore. Si une opération particulière nécessite le portail Azure, Cloud Explorer fournit des liens vers l’emplacement du portail Azure auquel vous devez accéder.

![IDE de Visual Studio](../ide/media/visualstudioide.png)

Voici d’autres fonctionnalités de productivité courantes de Visual Studio :

- La zone de recherche [Lancement rapide](../ide/reference/quick-launch-environment-options-dialog-box.md) est un excellent moyen de trouver rapidement ce dont vous avez besoin dans Visual Studio. Entrez simplement le nom de l’élément que vous recherchez, et Visual Studio affiche les résultats de la recherche à partir desquels vous pouvez accéder à l’élément précis recherché. Le lancement rapide affiche également des liens permettant de démarrer Visual Studio Installer pour une charge de travail ou un composant.

  ![Zone de recherche de lancement rapide](../ide/media/VSIDE_Tour_QuickLaunch.png)

- La [refactorisation](../ide/refactoring-in-visual-studio.md) inclut des opérations comme le renommage intelligent des variables, le déplacement de lignes de code sélectionnées dans une fonction distincte, le déplacement de code à d’autres endroits, la réorganisation des paramètres des fonctions, et ainsi de suite.

 ![Refactorisation](../ide/media/VSIDE_refactor.png)

- **IntelliSense** est un terme couvrant un ensemble de fonctionnalités appréciées qui affichent des informations sur les types concernant votre code directement dans l’éditeur et qui, dans certains cas, écrivent de petits extraits de code pour vous. Cela revient à avoir de la documentation de base incluse dans l’éditeur, ce qui vous évite d’avoir à rechercher des informations sur les types dans une fenêtre d’aide distincte. Les fonctionnalités d'IntelliSense varient selon le langage. Pour plus d’informations, consultez [C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ Intellisense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md) et [Options IntelliSense spécifiques à Visual Basic](../ide/visual-basic-specific-intellisense.md). L’illustration suivante montre certaines fonctionnalités IntelliSense à l'œuvre :

  ![Liste des membres Visual Studio](../ide/media/vs2017_Intellisense.png)

- Les **tildes** sont des soulignements rouges ondulés indiquant des erreurs ou des problèmes potentiels dans votre code en temps réel en cours de frappe. Cela vous permet de les corriger immédiatement sans attendre la détection de l’erreur lors de la compilation ou de l’exécution. Si vous pointez sur le tilde, vous voyez des informations supplémentaires sur l'erreur. Une icône d'ampoule peut également apparaître dans la marge gauche, avec des suggestions pour corriger l'erreur. Pour plus d’informations, consultez [Actions rapides](../ide/quick-actions.md).

 ![Tildes](../ide/media/vs2017_squiggle.png)

- Vous pouvez ouvrir la fenêtre [Hiérarchie d’appels](../ide/reference/call-hierarchy.md) dans le menu contextuel de l’éditeur de texte pour afficher les méthodes qui appellent la méthode sous le signe insertion (point d’insertion) et qui sont appelées par cette méthode.

 ![Fenêtre Hiérarchie d'appels](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) vous permet de rechercher les références et les modifications apportées à votre code, les bogues liés, les éléments de travail, les révisions de code et les tests unitaires, tout cela sans quitter l'éditeur.

 ![CodeLens](../ide/media/codelensoverview.png)

- La fenêtre [Aperçu de la définition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) montre une définition de méthode ou de type inline, sans vous obliger à quitter votre contexte actuel.

 ![Aperçu de définition](../ide/media/VSIDE_peek_definition.png)

- L'option de menu contextuel **Atteindre la définition** vous amène directement à l'endroit où la fonction ou l'objet est défini. D'autres commandes de navigation sont également disponibles en cliquant avec le bouton droit dans l'éditeur.

 ![Atteindre la définition](../ide/media/VSIDE_go_to_definition.png)

- L’outil connexe [Explorateur d’objets](http://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470) vous permet d’inspecter les assemblys .NET ou Windows Runtime sur votre système pour voir les types qu’ils contiennent ainsi que les membres de ces types (propriétés, méthodes, événements, etc.).

  ![Explorateur d’objets montrant le composant System.Timer](../ide/media/objectbrowser.png)

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Gérer votre code source et collaborer avec d’autres utilisateurs

Vous pouvez gérer votre code source dans des dépôts Git hébergés par tous types de fournisseurs, notamment GitHub. Ou utilisez [Visual Studio Team Services (VSTS)](/vsts/index) pour gérer le code en même temps que les bogues et les éléments de travail de votre projet entier. Pour en savoir plus sur la gestion des dépôts Git dans Visual Studio à l’aide de Team Explorer, consultez [Bien démarrer avec Git et Team Services (VSTS)](/vsts/git/gitquickstart?tabs=visual-studio). Visual Studio dispose également d’autres fonctionnalités de contrôle de code source intégrées. Pour en savoir plus à ce sujet, consultez le blog [New Git Features in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/).

Visual Studio Team Services est un service basé sur le cloud destiné à héberger des projets de logiciels et à permettre la collaboration dans des équipes. VSTS prend en charge les systèmes de contrôle de code source Git et Team Foundation, ainsi que les méthodologies de développement Scrum, CMMI et Agile. La gestion de version Team Foundation (TFVC) utilise un dépôt de serveur unique et centralisé pour effectuer le suivi et la gestion des versions des fichiers. Les modifications locales sont toujours archivées sur le serveur central, où les autres développeurs peuvent obtenir les dernières modifications.

Team Foundation Server (TFS) est le hub de gestion du cycle de vie des applications pour Visual Studio. Il permet à toutes personnes impliquées dans le processus de développement de participer à une même solution. TFS est également utile pour la gestion des équipes et des projets hétérogènes.

Si vous avez un compte Visual Studio Team Services ou Team Foundation Server sur votre réseau, vous vous y connectez via la fenêtre Team Explorer. Depuis cette fenêtre, vous pouvez vérifier le code dans ou en dehors du contrôle de code source, gérer des éléments de travail, démarrer des builds et accéder aux salles d'équipe et aux espaces de travail. Vous pouvez ouvrir Team Explorer à partir de la zone **Lancement rapide** ou du menu principal, à partir d’**Affichage, Team Explorer** ou d’**Équipe, Gérer les connexions**.

L’illustration suivante montre la fenêtre Team Explorer pour une solution qui est hébergée dans VSTS.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer.png)

Vous pouvez automatiser votre processus de génération pour générer le code que les développeurs de votre équipe ont archivé dans la gestion de versions. Par exemple, vous pouvez générer un ou plusieurs projets la nuit ou chaque fois le code est archivé. Pour plus d’informations, consultez [Build et Release (VSTS et TFS)](/vsts/build-release/index).

## <a name="connect-to-services-databases-and-cloud-based-resources"></a>Se connecter aux services, bases de données et ressources de Cloud

Le Cloud est essentiel dans le monde connecté actuel, et Visual Studio vous permet de l’exploiter. Par exemple, la fonctionnalité Services connectés facilite la connexion de votre application aux services. Vos applications peuvent l’utiliser pour stocker leurs données sur le stockage Azure, notamment.

![Services connectés](../ide/media/VSIDE_Tour_Connected_Services.png)

Sélectionnez un service sur la page **Services connectés** pour appeler l’Assistant Services connectés, qui configure votre projet et télécharge les packages NuGet nécessaires pour vous permettre de démarrer le codage par rapport au service.

Vous pouvez afficher et gérer vos ressources de Cloud basées sur Azure dans Visual Studio à l’aide de [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer). Cloud Explorer montre les ressources Azure dans tous les comptes gérés sous l’abonnement Azure auquel vous êtes connecté. Vous pouvez obtenir Cloud Explorer en sélectionnant la charge de travail **Développement Azure** dans Visual Studio Installer.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

L’**Explorateur de serveurs** vous aide à parcourir et à gérer les instances et ressources SQL Server en local et à distance, et sur Azure, Salesforce.com, Office 365 et les sites web. Pour ouvrir l’Explorateur de serveurs, dans le menu principal, choisissez **Affichage** > **Explorateur de serveurs**. Consultez la page [Ajouter de nouvelles connexions](../data-tools/add-new-connections.md) pour plus d’informations sur l’Explorateur de serveurs.

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) est un environnement de développement puissant pour SQL Server, Azure SQL Database et Azure SQL Data Warehouse. Il vous permet de générer, déboguer, gérer et refactoriser des bases de données. Vous pouvez travailler avec un projet de base de données, ou directement avec une instance de base de données connectée, locale ou hors site.

L’**Explorateur d’objets SQL Server** de Visual Studio offre une vue des objets de base de données similaire à celle de SQL Server Management Studio. L’Explorateur d’objets SQL Server vous permet d’effectuer des tâches simples d’administration et de conception de base de données, y compris la modification des données des tables, la comparaison de schémas et l’exécution de requêtes à l’aide de menus contextuels directement depuis l’Explorateur d’objets SQL Server, et plus encore.

![Explorateur d'objets SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="extend-visual-studio"></a>Extension de Visual Studio

Si Visual Studio ne dispose pas de la fonctionnalité exacte dont vous avez besoin, vous pouvez l’ajouter ! Vous pouvez personnaliser l’IDE en fonction de votre flux de travail et du style, ajouter la prise en charge des outils externes non intégrés à Visual Studio et modifier des fonctionnalités existantes pour accroître votre productivité. Pour obtenir la dernière version des outils d’extensibilité de Visual Studio (Visual Studio SDK), consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Vous pouvez écrire vos propres analyseurs et générateurs de code à l’aide de la plateforme de compilateurs .NET (Roslyn). Trouvez tout ce dont vous avez besoin sur [Roslyn](https://github.com/dotnet/Roslyn).

Découvrez les [extensions existantes](https://marketplace.visualstudio.com/vs) pour Visual Studio créées par des développeurs Microsoft et notre communauté de développement.

Pour en savoir plus sur l’extension de Visual Studio, consultez [Étendre l’IDE de Visual Studio](https://www.visualstudio.com/vs/extend/).

## <a name="learn-more-and-find-out-whats-new"></a>En savoir plus et découvrir les nouveautés

Si vous n’avez encore jamais utilisé Visual Studio, consultez [Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md) ou recherchez les cours Visual Studio gratuits disponibles sur [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033). Si vous voulez découvrir les nouvelles fonctionnalités de Visual Studio 2017, consultez [Nouveautés dans Visual Studio 2017](../ide/whats-new-in-visual-studio.md).

Félicitations, vous avez terminé la visite guidée de l’IDE de Visual Studio ! Nous espérons qu’elle vous aura permis de découvrir ses fonctionnalités principales.

## <a name="see-also"></a>Voir aussi

* [IDE Visual Studio](https://www.visualstudio.com/vs/)
* [Téléchargements Visual Studio](https://www.visualstudio.com/downloads/)
* [Le blog Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Forums Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?category=visualstudio%2Cvsarch%2Cvsdbg%2Cvstest%2Cvstfs%2Cvsdata%2Cvsappdev%2Cvisualbasic%2Cvisualcsharp%2Cvisualc)
* [Microsoft Virtual Academy](https://mva.microsoft.com/)
* [Channel 9](https://channel9.msdn.com/)