---
title: "Visite guidée des fonctionnalités de l’IDE Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 06/28/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 35
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 669bc5894727c207691a7e37937f432d98fee8b1
ms.openlocfilehash: 8d2c20b32201b3df85e5150828565eee84d66375
ms.contentlocale: fr-fr
ms.lasthandoff: 06/30/2017

---
# <a name="visual-studio-ide-feature-tour"></a>Visite guidée des fonctionnalités de l’IDE Visual Studio
Cette rubrique vous présente les fonctionnalités de l’IDE de Visual Studio. L’IDE de Visual Studio est un environnement de développement interactif (IDE) ; une plate-forme de lancement créative que vous pouvez utiliser pour afficher et modifier presque n’importe quel type de code et déboguer, générer et publier des applications pour Android, iOS, Windows, le web et le Cloud. Des versions sont disponibles pour Mac et Windows. Nous allons voir ce que vous pouvez faire avec Visual Studio, aborder son installation, son utilisation, la création de projets simples, l’obtention de pointeurs lors du débogage et du déploiement de code et découvrir les divers outils Windows.

## <a name="what-can-you-do-with-the-visual-studio-ide"></a>Que pouvez-vous faire avec l’IDE Visual Studio ?
Vous souhaitez créer une application pour un téléphone Android ? C’est possible. Et qu’en est-il de la création de jeux de pointe à l’aide de C++ ? Cela fait également partie des innombrables possibilités proposées. Visual Studio fournit des modèles qui vous permettent de créer des sites web, des jeux, des applications de bureau, des applications mobiles, des applications pour Office et plus encore.

![Projets Visual Studio](../ide/media/VSIDE_Tour_Projects_List.png)

Vous pouvez aussi ouvrir tout simplement presque n’importe quel code obtenu où que vous soyez et commencer à travailler. Vous voyez sur GitHub un projet qui vous plaît ? Il vous suffit de cloner le dépôt, de l’ouvrir dans Visual Studio et de commencer à rédiger le code !

### <a name="create-mobile-apps"></a>Créer des applications mobiles
Vous pouvez créer des applications mobiles natives pour différentes plateformes à l’aide de Visual C# et Xamarin ou Visual C++ natives ou des applications hybrides à l’aide de JavaScript avec Apache Cordova. Vous pouvez créer des jeux mobiles pour Unity, Unreal, DirectX, Cocos, et plus encore. Visual Studio inclut un émulateur Android pour vous aider à exécuter et déboguer des applications Android.

Vous pouvez exploiter la puissance du Cloud pour vos applications mobiles en créant des services d’applications Azure. Les services d’applications Azure permettent à vos applications de stocker des données sur le Cloud, d’authentifier les utilisateurs de manière sécurisée et de faire évoluer automatiquement leurs ressources pour répondre aux besoins de votre application et de votre entreprise. Pour plus d’informations, consultez [Développement d’applications mobiles](https://www.visualstudio.com/vs/mobile-app-development/).

### <a name="create-cloud-apps-for-azure"></a>Créer des applications Cloud pour Azure
Visual Studio propose une suite d’outils qui facilitent la création d’applications Cloud alimentées par Microsoft Azure. Vous pouvez configurer, générer, déboguer, packager et déployer des applications et services sur Microsoft Azure directement à partir de l’IDE. Exploiter les services Azure pour vos applications à l’aide des services connectés. Pour obtenir les outils Azure pour .NET, sélectionnez la charge de travail de **développement Azure** lors de l’installation de Visual Studio. Pour plus d’informations, consultez [Visual Studio Tools pour Azure](https://www.visualstudio.com/vs/azure-tools/).

### <a name="create-apps-for-the-web"></a>Créer des applications pour le web
Le web est le moteur de notre monde moderne et Visual Studio peut vous aider à écrire des applications conçues pour lui. Vous pouvez créer des applications web à l’aide de ASP.NET, Node.js, Python, JavaScript et TypeScript. Visual Studio comprend les frameworks web, telles que Angular, jQuery, Express et plus encore. ASP.NET Core et .NET Core s’exécutent sur les systèmes d’exploitation Windows, Mac et Linux. Pour plus d’informations, consultez [Outils web modernes](https://www.visualstudio.com/vs/modern-web-tooling/).

### <a name="write-code-in-a-world-class-editing-environment"></a>Écrire du code dans un environnement d’édition international
Visual Studio vous permet d’écrire du code rapidement et facilement grâce à des fonctionnalités, telles que la colorisation de syntaxe, la saisie semi-automatique, IntelliSense (descriptions contextuelles de l’élément de code sélectionné), le surlignage de code, la définition de points d’arrêt pour le débogage et bien plus encore.

![Exemple de code JavaScript](../ide/media/vside_tour_javascript_example.gif)

Pour en savoir plus, consultez [Écriture de code dans l’éditeur de code et de texte](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor).

Visual Studio peut vous permettre d’effectuer bien d’autres choses. Pour une liste plus complète, consultez [IDE de Visual Studio](https://www.visualstudio.com/vs/).


## <a name="install-the-visual-studio-ide"></a>Installer l’IDE de Visual Studio
Pour commencer, téléchargez Visual Studio et installez-le sur votre système. Vous pouvez le télécharger depuis le site [Visual Studio 2017](https://www.visualstudio.com/vs/visual-studio-2017/).

Visual Studio n’a jamais été si léger ! Le nouveau programme d’installation modulaire vous permet de choisir et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités requises pour la plate-forme ou le langage de programmation que vous préférez. Cette stratégie permet de réduire encore l’espace dédié à l’installation de Visual Studio. Ce qui implique également une plus grande rapidité de l’installation et des mises à jour.

![Programme d’installation de Visual Studio](../ide/media/vside_tour_install_dialog.png)

Outre les meilleures performances d’installation, de nombreuses améliorations ont été effectuées dans Visual Studio 2017 afin de réduire les durées globales de chargement des solutions et de démarrage de l’IDE. Par exemple, sélectionnez la nouvelle fonctionnalité de chargement de solution allégé, située dans le menu principal sous **Outils**, **Options**, **Projets et solutions** pour accélérer le chargement des solutions. Pour en savoir plus sur la configuration de Visual Studio sur votre système, consultez [Installer Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio).

## <a name="sign-in"></a>Se connecter
Quand vous démarrez Visual Studio pour la première fois, vous pouvez vous connecter avec votre compte Microsoft, ou avec votre compte professionnel ou celui de votre établissement scolaire. Le fait d’être connecté vous permet de synchroniser les paramètres de Visual Studio, tels que les dispositions de fenêtres sur plusieurs appareils. Cela vous permet également de vous connecter aux services dont vous pouvez avoir besoin, tels que les abonnements Azure et Visual Studio Team Services.


## <a name="create-a-program"></a>Créer un programme

Un bon moyen d’en savoir plus sur quelque chose est de l’utiliser ! Nous allons aller plus loin en créant un nouveau programme simple.

1. Ouvrez Visual Studio. Dans le menu, sélectionnez **Fichier**, **Nouveau**, **Projet**. Utilisez les valeurs de projet par défaut.

  ![capture d’écran](../ide/media/VSIDE_Tour_NewProject1.png)

  Vous pouvez également créer un projet à l’aide de la page de démarrage. Pour plus d’informations, consultez le blog [Harness the Power of the Redesigned Start Page](https://blogs.msdn.microsoft.com/visualstudio/2016/11/29/harness-the-power-of-the-redesigned-start-page/).

1. La boîte de dialogue **Nouveau projet** affiche plusieurs modèles de projet. Choisissez la catégorie **Windows universel** sous **Visual C#**, le modèle **Applications vide (Windows Universel)**, puis cliquez sur le bouton **OK**.

  ![capture d’écran](../ide/media/VSIDE_Tour_NewProject2.png)

  Cela crée un nouveau projet d’application Windows universel vide utilisant Visual C# et XAML comme langages de programmation. Patientez jusqu’à ce que Visual Studio configure le projet pour vous. Si vous êtes invité à saisir de nouvelles informations, acceptez simplement les valeurs par défaut pour le moment.

1. Quelque chose qui ressemble à la capture d’écran suivante doit bientôt s’afficher. Vos fichiers de projet sont répertoriés sur le côté droit dans une fenêtre appelée Explorateur de solutions.

  ![capture d’écran](../ide/media/VSIDE_Tour_NewProject3.png)

1. Dans l’Explorateur de solutions, cliquez sur le petit triangle noir en regard du fichier MainPage.xaml pour le développer. Un fichier MainPage.xaml.cs doit s’afficher en dessous. Cliquez sur ce fichier (qui contient du code C#) pour l’ouvrir.

  Le code C# du fichier MainPage.xaml.cs apparaît dans l’éditeur de code sur le côté gauche de l’écran. Notez que la syntaxe du code est automatiquement colorisée pour indiquer les différents types de code, tels que les instructions ou les commentaires. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer le code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran.

  ![](../ide/media/VSIDE_Tour_NewProject3a.png)

  Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

1. Ajoutez un bouton au formulaire XAML pour permettre aux utilisateurs d’interagir avec votre application. Pour ce faire, ouvrez le fichier MainPage.xaml. Cet exemple montre un affichage fractionné : un concepteur dans la partie supérieure pour distinguer visuellement les contrôles et un affichage de code dans la partie inférieure, qui affiche le code XAML derrière le concepteur. Lorsque vous exécutez le programme ultérieurement, ce que vous voyez dans le concepteur devient une fenêtre (un formulaire) visible aux utilisateurs, et le code XAML sous-jacent détermine ce qui apparaît sur ce formulaire.

1. À gauche de l’écran, cliquez sur l’onglet **Boîte à outils** pour ouvrir la boîte à outils. La boîte à outils contient un certain nombre de contrôles visuels que vous pouvez ajouter aux formulaires. Pour l’instant, nous allons nous contenter d’ajouter un bouton de contrôle.

1. Développez la section **Contrôles XAML communs**, puis faites glisser le contrôle du bouton vers le centre du formulaire. L’emplacement exact importe peu.

  ![capture d’écran](../ide/media/VSIDE_Tour_Toolbox.png)

  Lorsque vous avez terminé, l’affichage doit ressembler à ce qui suit.

  ![capture d’écran](../ide/media/VSIDE_Tour_XAMLButton.png)

  Le bouton est dans le concepteur et son code sous-jacent (en surbrillance) est automatiquement ajouté au code XAML du concepteur.

1. Modifions le code XAML. Renommez `Button` en `Hello!` dans le texte du code du bouton.

  ![capture d’écran](../ide/media/VSIDE_Tour_XAMLButton2.png)

1. Maintenant, démarrez l’application. Pour ce faire, cliquez sur le bouton **Démarrer** (![bouton Démarrer](../ide/media/VSIDE_StartButton.png)) de la barre d’outils, appuyez sur la touche F5 ou choisissez **Déboguer**, **Démarrer le débogage**.

  ![capture d’écran](../ide/media/VSIDE_Tour_RunButton.png)

  L’application commence son processus de génération et les messages d’état apparaissent dans la fenêtre Sortie. Vous ne tarderez pas à voir le formulaire, sur lequel apparaît vote bouton, s’afficher. Maintenant, votre application fonctionne !

  ![capture d’écran](../ide/media/VSIDE_Tour_RunProject.png)

  Bien sûr, ses fonctionnalités restent limitées pour le moment, mais vous pourrez l’améliorer ultérieurement si vous le souhaitez.

1. Lorsque vous avez fini d’exécuter le programme, cliquez sur le bouton![Arrêter](../ide/media/VSIDE_StopButton.png)de la barre d’outils pour l’arrêter.

Récapitulons ce que vous avez fait jusqu’à présent. Vous avez créé un projet Windows universel C# dans Visual Studio, affiché son code, ajouté un contrôle au concepteur, modifié le code XAML et exécuté le projet. Bien que le processus ait été simplifié pour cet exemple, il vous montre certaines parties de l’IDE de Visual Studio, que vous utiliserez lors du développement de vos propres applications courantes. Si vous souhaitez en savoir plus sur cet exemple, consultez [Créer une application « Hello World » (XAML)](https://docs.microsoft.com/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).


## <a name="debug-test-and-improve-your-code"></a>Déboguer, tester et améliorer votre code
Des erreurs peuvent survenir lors de l’exécution. Lorsque vous écrivez du code, vous devez l’exécuter, tester ses performances et rechercher les bogues. Le système de débogage de pointe de Visual Studio vous permet de déboguer du code en cours d’exécution dans votre projet local, sur un appareil distant ou sur un émulateur comme ceux destinés aux appareils Android ou Windows Phone. Vous pouvez parcourir le code instruction par instruction et examiner les variables au fil de la progression, vous pouvez avancer pas à pas dans des applications multithread, et vous pouvez définir des points d'arrêt qui sont atteints seulement quand une condition spécifiée est vraie. Vous pouvez surveiller les valeurs des variables à mesure que le code s’exécute. Tout ceci peut être géré dans l’éditeur de code lui-même, ce qui vous permet de ne pas quitter votre code.

![Débogage](../ide/media/VSIDE_Tour_Debugging.png)

À des fins de test, Visual Studio propose des tests unitaires, IntelliTest, des tests de charge et de performances et bien plus encore. Pour en savoir plus sur le processus de débogage de Visual Studio, consultez [Debugger Feature Tour](../debugger/debugger-feature-tour.md) (Présentation des fonctionnalités de débogage). Pour plus d’informations sur le test, consultez [Outils de test](https://www.visualstudio.com/vs/testing-tools/). Pour en savoir plus sur l’amélioration des performances de vos applications, consultez [Visite guidée des fonctionnalités de profilage](../profiling/profiling-feature-tour.md).

## <a name="deploy-your-finished-application"></a>Déployer votre application terminée  
Quand votre application est prête à être déployée auprès des utilisateurs ou des clients, Visual Studio fournit les outils nécessaires, qu’elle soit déployée dans le Windows Store, sur un site SharePoint ou à l’aide des technologies InstallShield ou Windows Installer. Ils sont tous accessibles via l’IDE. Pour plus d’informations, consultez [Déploiement d’applications, de services et de composants](../deployment/deploying-applications-services-and-components.md).

## <a name="quick-tour-of-the-ide"></a>Visite guidée de l’IDE
Pour vous donner une vue d’ensemble détaillée de Visual Studio, l’image suivante montre un projet est ouvert dans Visual Studio et plusieurs fenêtres d’outils clés que vous utiliserez très probablement.
 - L’[Explorateur de solutions](../ide/solutions-and-projects-in-visual-studio.md) vous permet d’afficher, de parcourir et de gérer vos fichiers de code.
 - La fenêtre [Éditeur](../ide/writing-code-in-the-code-and-text-editor.md) vous permet d’afficher votre code et de modifier les données de concepteur et le code source.
 - La fenêtre [Sortie](../ide/reference/output-window.md) affiche les messages de résultat de la compilation, de l’exécution, du débogage et bien plus encore.
 - [Team Explorer](https://www.visualstudio.com/docs/connect/work-team-explorer) vous permet de suivre des éléments de travail et de partager du code avec d’autres utilisateurs à l’aide des technologies de gestion de version comme [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](https://www.visualstudio.com/docs/tfvc/overview).
 - [Cloud Explorer](https://azure.microsoft.com/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/) vous permet d’afficher et de gérer vos ressources Azure, telles que les machines virtuelles, les tables, les bases de données SQL et bien plus encore.

![IDE de Visual Studio](../ide/media/visualstudioide.png)  

Voici d’autres fonctionnalités de productivité courantes de Visual Studio.  

- La zone de recherche [Lancement rapide](https://docs.microsoft.com/en-us/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) est un excellent moyen de trouver rapidement ce dont vous avez besoin dans Visual Studio. Il vous suffit d’entrer le nom de ce que vous cherchez et Visual Studio proposent des options qui vous emmènent exactement là où vous souhaitez aller. Le Lancement rapide propose également des liens permettant de démarrer le programme d’installation de Visual Studio pour n’importe quelle charge de travail ou composant.

  ![Zone de recherche de lancement rapide](../ide/media/VSIDE_Tour_QuickLaunch.png)

-  La [refactorisation](../ide/refactoring-in-visual-studio.md) inclut des opérations comme le renommage intelligent des variables, le déplacement de lignes de code sélectionnées dans une fonction distincte, le déplacement de code à d’autres endroits, la réorganisation des paramètres des fonctions, et ainsi de suite.

 ![Refactorisation](../ide/media/VSIDE_refactor.png)  

-  **IntelliSense** est un terme couvrant un ensemble de fonctionnalités appréciées qui affichent des informations sur les types concernant votre code directement dans l’éditeur et qui, dans certains cas, écrivent de petits extraits de code pour vous. Cela revient à avoir de la documentation de base incluse dans l’éditeur, ce qui vous évite d’avoir à rechercher des informations sur les types dans une fenêtre d’aide distincte. Les fonctionnalités d'IntelliSense varient selon le langage. Pour plus d’informations, consultez [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ Intellisense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Options IntelliSense propres à Visual Basic](../ide/visual-basic-specific-intellisense.md). L’illustration suivante montre certaines fonctionnalités IntelliSense à l'œuvre :  

  ![Liste des membres Visual Studio](../ide/media/vs2017_Intellisense.png)  

-  Les **tildes** sont des soulignements rouges ondulés indiquant des erreurs ou des problèmes potentiels dans votre code en temps réel en cours de frappe. Cela vous permet de les corriger immédiatement sans attendre la détection de l’erreur lors de la compilation ou de l’exécution. Si vous pointez sur le tilde, vous voyez des informations supplémentaires sur l'erreur. Une icône d'ampoule peut également apparaître dans la marge gauche, avec des suggestions pour corriger l'erreur. Pour plus d'informations, consultez [Effectuer des actions rapides avec des ampoules](../ide/perform-quick-actions-with-light-bulbs.md).  

 ![Tildes](../ide/media/vs2017_squiggle.png)  

-  Vous pouvez ouvrir la fenêtre [Hiérarchie d’appels](../ide/reference/call-hierarchy.md) dans le menu contextuel de l’éditeur de texte pour afficher les méthodes qui appellent la méthode sous le signe insertion (point d’insertion) et qui sont appelées par cette méthode.

 ![Fenêtre Hiérarchie d'appels](../ide/media/VSIDE_call_hierarchy.png)

-  [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) vous permet de rechercher les références et les modifications apportées à votre code, les bogues liés, les éléments de travail, les révisions de code et les tests unitaires, tout cela sans quitter l'éditeur.

 ![CodeLens](../ide/media/codelensoverview.png)

-  La fenêtre [Aperçu de la définition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) montre une définition de méthode ou de type inline, sans vous obliger à quitter votre contexte actuel.  

 ![Aperçu de définition](../ide/media/VSIDE_peek_definition.png)

-  L'option de menu contextuel **Atteindre la définition** vous amène directement à l'endroit où la fonction ou l'objet est défini. D'autres commandes de navigation sont également disponibles en cliquant avec le bouton droit dans l'éditeur.

 ![Atteindre la définition](../ide/media/VSIDE_go_to_definition.png)

- Un outil connexe, l’[Explorateur d’objets](http://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), vous permet d’examiner les assemblys .NET ou Windows Runtime sur votre système, pour voir les types qu’ils contiennent ainsi que les méthodes, les propriétés et les événements que ces types contiennent.

  ![Explorateur d’objets montrant le composant System.Timer](../ide/media/objectbrowser.png)  

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Gérer votre code source et collaborer avec d’autres utilisateurs
Vous pouvez gérer votre code source dans des dépôts Git hébergés par tous types de fournisseurs, notamment GitHub. Ou utilisez [Visual Studio Team Services (VSTS)](https://www.visualstudio.com/team-services/) pour gérer le code en même temps que les bogues et les éléments de travail de votre projet entier. Pour en savoir plus sur la gestion des dépôts Git dans Visual Studio à l’aide de Team Explorer, consultez la page [Bien démarrer avec Git et Team Services](https://www.visualstudio.com/en-us/docs/git/gitquickstart-vs2017).  Visual Studio dispose également d’autres fonctionnalités de contrôle de code source intégrées. Pour en savoir plus à ce sujet, consultez le blog [New Git Features in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/).

Visual Studio Team Services est un service basé sur le cloud destiné à héberger des projets de logiciels et à permettre la collaboration dans des équipes. VSTS prend en charge les systèmes de contrôle de code source Git et Team Foundation, ainsi que les méthodologies de développement Scrum, CMMI et Agile. La gestion de version Team Foundation (TFVC) utilise un dépôt de serveur unique et centralisé pour effectuer le suivi et la gestion des versions des fichiers. Les modifications locales sont toujours archivées sur le serveur central, où les autres développeurs peuvent obtenir les dernières modifications.

Team Foundation Server (TFS) est le hub de gestion du cycle de vie des applications pour Visual Studio. Il permet à toutes personnes impliquées dans le processus de développement de participer à une même solution. TFS est également utile pour la gestion des équipes et des projets hétérogènes.

Si vous avez un compte Visual Studio Team Services ou Team Foundation Server sur votre réseau, vous vous y connectez via la fenêtre Team Explorer. Depuis cette fenêtre, vous pouvez vérifier le code dans ou en dehors du contrôle de code source, gérer des éléments de travail, démarrer des builds et accéder aux salles d'équipe et aux espaces de travail. Vous pouvez ouvrir Team Explorer à partir de la zone **Lancement rapide** ou du menu principal, à partir d’**Affichage, Team Explorer** ou d’**Équipe, Gérer les connexions**.
L’illustration suivante montre la fenêtre Team Explorer pour une solution qui est hébergée dans VSTS.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer.png)  

Pour plus d’informations sur Visual Studio Team Services, consultez [Visual Studio Team Services](https://www.visualstudio.com/team-services/). Pour plus d’informations sur Team Foundation Server, consultez [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).


## <a name="connect-to-services-databases-and-cloud-based-resources"></a>Se connecter aux services, bases de données et ressources de Cloud
Le Cloud est essentiel dans le monde connecté actuel, et Visual Studio vous permet de l’exploiter. Par exemple, la fonctionnalité Services connectés facilite la connexion de votre application aux services. Vos applications peuvent l’utiliser pour stocker leurs données sur le stockage Azure, notamment.

![Services connectés](../ide/media/VSIDE_Tour_Connected_Services.png)

Sélectionnez un service sur la page **Services connectés** pour appeler l’Assistant Services connectés, qui configure votre projet et télécharge les packages NuGet nécessaires pour vous permettre de démarrer le codage par rapport au service.

Vous pouvez afficher et gérer vos ressources de Cloud basées sur Azure dans Visual Studio à l’aide de [Cloud Explorer](https://azure.microsoft.com/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/). Cloud Explorer montre les ressources Azure dans tous les comptes gérés sous l’abonnement Azure auquel vous êtes connecté. Vous pouvez obtenir Cloud Explorer en sélectionnant la charge de travail de développement Azure dans le programme d’installation de Visual Studio.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

L’**Explorateur de serveurs** permet de parcourir et de gérer les instances et les ressources SQL Server sur Azure, Salesforce.com, Office 365 et les sites web. Pour ouvrir l’Explorateur de serveurs, dans le menu principal, choisissez **Affichage**, **Explorateur de serveurs**. Consultez la page [Ajouter de nouvelles connexions](https://docs.microsoft.com/visualstudio/data-tools/add-new-connections) pour plus d’informations sur l’Explorateur de serveurs.

[SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) est un environnement de développement puissant pour SQL Server, Azure SQL Database et Azure SQL Data Warehouse. Il vous permet de générer, déboguer, gérer et refactoriser des bases de données. Vous pouvez travailler avec un projet de base de données, ou directement avec une instance de base de données connectée, locale ou hors site.

L’**Explorateur d’objets SQL Server** de Visual Studio offre une vue des objets de base de données similaire à celle de SQL Server Management Studio. L’Explorateur d’objets SQL Server vous permet d’effectuer des tâches simples d’administration et de conception de base de données, y compris la modification des données des tables, la comparaison de schémas et l’exécution de requêtes à l’aide de menus contextuels directement depuis l’Explorateur d’objets SQL Server, et plus encore. Pour plus d’informations, consultez [Gérer les objets à l’aide de l’Explorateur d’objets](https://docs.microsoft.com/sql/ssms/object/manage-objects-by-using-object-explorer).

![Explorateur d'objets SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)  

## <a name="extend-visual-studio"></a>Extension de Visual Studio
Si Visual Studio ne dispose pas de la fonctionnalité exacte dont vous avez besoin, vous pouvez l’ajouter ! Vous pouvez personnaliser l’IDE en fonction de votre flux de travail et du style, ajouter la prise en charge des outils externes non intégrés à Visual Studio et modifier des fonctionnalités existantes pour accroître votre productivité. Visual Studio fournit des outils, des contrôles et des modèles issus de Microsoft, de nos partenaires et de la communauté. Pour en savoir plus sur l’extension de Visual Studio, consultez [Étendre l’IDE de Visual Studio](https://www.visualstudio.com/vs/extend/).

## <a name="learn-more-and-find-out-whats-new"></a>En savoir plus et découvrir les nouveautés
Si vous n’avez jamais utilisé Visual Studio, découvrez les principes de base, en commençant par lire [Bien démarrer avec Visual Studio](../ide/get-started-with-visual-studio.md), ou consultez les cours Visual Studio gratuits disponibles sur [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033).
Si vous voulez découvrir les nouvelles fonctionnalités de Visual Studio 2017, consultez [Nouveautés dans Visual Studio 2017](../ide/whats-new-in-visual-studio.md).

Félicitations, vous avez terminé la visite guidée de l’IDE de Visual Studio ! Nous espérons qu’elle vous aura permis de découvrir ses fonctionnalités principales.

## <a name="see-also"></a>Voir aussi
* [IDE Visual Studio](https://www.visualstudio.com/vs/)
* [Téléchargements Visual Studio](https://www.visualstudio.com/downloads/)
* [Le blog Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Forums Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?category=visualstudio%2Cvsarch%2Cvsdbg%2Cvstest%2Cvstfs%2Cvsdata%2Cvsappdev%2Cvisualbasic%2Cvisualcsharp%2Cvisualc)
* [Microsoft Virtual Academy](https://mva.microsoft.com/)
* [Channel 9](https://channel9.msdn.com/)

