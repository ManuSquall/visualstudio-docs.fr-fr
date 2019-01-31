---
title: Nouveautés de Visual Studio 2017
titleSuffix: ''
description: Découvrez les nouvelles fonctionnalités de Visual Studio 2017.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: '>= vs-2017'
ms.openlocfilehash: 3dd6a4d1dc8c17773a509576ad489a7ba3d752ce
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55090100"
---
# <a name="whats-new-in-visual-studio-2017"></a>Nouveautés de Visual Studio 2017

**Mis à jour pour la [version 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Vous envisagez de mettre à niveau une version antérieure de Visual Studio ? Visual Studio 2017 peut vous apporter : Une productivité inégalée pour l’ensemble des développements, applications et plateformes. Utilisez Visual Studio 2017 afin de développer des applications pour Android, iOS, Windows, le web et le Cloud. Écrivez votre code rapidement, déboguez et diagnostiquez facilement, testez souvent et publiez en toute confiance. Vous pouvez également étendre et personnaliser Visual Studio en créant vos propres extensions. Avec cette version, utilisez la gestion de versions, soyez agile et collaborez efficacement !

>[!div class="button"]
>[Télécharger Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Voici un récapitulatif général des changements par rapport à la version antérieure, Visual Studio 2015 :

* **[Principes de base redéfinis](#redefined-fundamentals)**. Une nouvelle expérience d’installation signifie que vous pouvez installer plus rapidement ce que vous voulez et quand vous en avez besoin.
* **[Performances et productivité](#performance-and-productivity)**. Nous nous sommes concentrés sur les fonctionnalités nouvelles et modernes du développement d’applications mobiles, de bureau et cloud. En outre, Visual Studio démarre plus vite, est plus réactif et utilise moins de mémoire qu’auparavant.
* **[Développement d’applications cloud avec Azure](#cloud-app-development-with-azure)**. Une suite intégrée d’outils Azure vous permet de créer facilement des applications prioritairement centrées sur le cloud et optimisées par Microsoft Azure. Visual Studio vous permet de facilement configurer, générer, déboguer, packager et déployer des applications et services sur Azure.
* **[Développement d’applications Windows](#windows-app-development)**. Avec les modèles UWP fournis dans Visual Studio 2017, créez un projet unique pour tous les appareils Windows 10 &ndash; PC, tablette, téléphone, Xbox, HoloLens, Surface Hub, etc.
* **[Développement d’applications mobiles](#mobile-app-development)**. Innovez et obtenez des résultats rapides grâce à Xamarin, qui unifie vos exigences pour les mobiles multi-plateformes en une seule base de code et à un même ensemble de compétences.
* **[Développement multiplateforme](#cross-platform-development)**. Livrez sans plus d’effort des logiciels pour toutes les plateformes ciblées. Étendez les processus DevOps à SQL Server à l’aide de Redgate Data Tools et automatisez en toute sécurité les déploiements de bases de données à partir de Visual Studio. Sinon, utilisez .NET Core pour écrire des applications et des bibliothèques qui s’exécutent sans modification sur les systèmes d’exploitation Windows, Linux et macOS.
* **[Développement de jeux](#games-development)**. Avec Visual Studio Tools for Unity (VSTU), vous pouvez utiliser Visual Studio pour écrire des scripts d'éditeur et de jeu en C#, puis utiliser son débogueur performant pour rechercher et corriger les erreurs.
* **[Développement IA](#ai-development)**. Avec Visual Studio Tools for AI, vous pouvez utiliser les fonctionnalités de productivité de Visual Studio pour accélérer l’innovation en matière d’intelligence artificielle (IA). Générez, testez et déployez des solutions de Deep Learning / IA qui s’intègrent directement à Azure Machine Learning pour des fonctionnalités d’expérimentation robustes.

> [!NOTE]
> Pour obtenir une liste complète des nouvelles fonctions et fonctionnalités disponibles dans Visual Studio 2017, consultez les [notes de la version actuelle](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Pour avoir un aperçu des fonctionnalités à venir, consultez les [notes de la préversion](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Voici des informations détaillées sur quelques-unes des nouvelles fonctionnalités et des améliorations les plus marquantes de Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Principes de base redéfinis

### <a name="a-new-setup-experience"></a>Une nouvelle expérience d'installation

Visual Studio simplifie et accélère l’installation des fonctionnalités dont vous avez besoin, quand vous en avez besoin. Une désinstallation « propre » est également disponible.

Le changement le plus important à constater lors de l’installation de Visual Studio est la nouvelle expérience proposée. Dans l’onglet **Charges de travail**, les options d’installation sont regroupées pour représenter les plateformes, les langages et les frameworks courants. Il couvre tout depuis le développement .NET Desktop au développement d’applications sur Windows, Linux et iOS.

Choisissez les charges de travail dont vous avez besoin et modifiez-les quand vous le souhaitez.

 ![Boîte de dialogue de configuration de Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

Vous disposez aussi d’options pour optimiser votre installation :

* Vous voulez choisir vos propres composants au lieu d’utiliser des charges de travail ? Sélectionnez l’onglet **Composants individuels** du programme d’installation.
* Vous souhaitez installer des modules linguistiques sans avoir à modifier les options de langue de Windows ? Choisissez l’onglet **Modules linguistiques** du programme d’installation.
* **Nouveautés de la version 15.7** : Vous voulez changer l’emplacement où Visual Studio s’installe ? Choisissez l’onglet **Options d’installation** du programme d’installation.

Pour en savoir plus sur la nouvelle expérience d’installation, notamment pour obtenir des instructions pas à pas, consultez la page [Installer Visual Studio](../install/install-visual-studio.md).

### <a name="a-focus-on-accessibility"></a>Accent sur l’accessibilité

**Nouveauté de la version 15.3** : Nous avons apporté plus de 1 700 correctifs ciblés visant à améliorer la compatibilité entre Visual Studio et les principales technologies d’assistance utilisées. Il existe des douzaines de scénarios plus compatibles avec les lecteurs d’écran, les thèmes de contraste élevé et autres technologies d’assistance que jamais auparavant. Le débogueur, l’éditeur et l’interpréteur de commandes ont tous également obtenus des améliorations significatives.

Pour plus d’informations sur l’accessibilité, consultez le billet de blog [Améliorations de l’accessibilité dans Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/).

## <a name="performance-and-productivity"></a>Performances et productivité

### <a name="sign-in-across-multiple-accounts"></a>Se connecter sur plusieurs comptes

Nous avons introduit dans Visual Studio un nouveau service d’identité qui permet de partager des comptes d’utilisateur dans Team Explorer, Azure Tools, la publication dans le Microsoft Store, et bien plus encore.

Vous pouvez rester connecté plus longtemps également. Visual Studio ne vous demande pas de vous reconnecter toutes les 12 heures. Pour plus d’informations, consultez le billet de blog [Fewer Visual Studio sign-in prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="start-visual-studio-faster"></a>Démarrer Visual Studio plus rapidement

Le nouveau Centre de performances Visual Studio peut vous aider à optimiser le temps de démarrage de votre IDE. Le Centre de performances répertorie toutes les extensions et les fenêtres d’outils susceptibles de ralentir le démarrage de l’IDE. Vous pouvez l’utiliser pour améliorer les performances de démarrage en déterminant quand les extensions démarrent, ou si les fenêtres d’outils sont ouvertes au démarrage.

### <a name="faster-on-demand-loading-of-extensions"></a>Accélération du chargement des extensions à la demande

Visual Studio déplace ses extensions (et fonctionne également avec des extensions tierces) pour un chargement à la demande, plutôt qu’au démarrage de l’IDE. Vous êtes curieux de savoir quelles extensions ont un impact sur le démarrage, le chargement de solution et les performances de la frappe ? Vous pouvez afficher ces informations dans **Aide** > **Gérer le niveau de performance de Visual Studio**.

  ![Boîte de dialogue Option de Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gérer vos extensions avec le Gestionnaire d’extensions itinérantes

Il est plus facile de configurer chaque environnement de développement avec vos extensions préférées quand vous vous connectez à Visual Studio. Le nouveau Gestionnaire d’extensions itinérantes effectue le suivi de toutes vos extensions préférées en créant une liste synchronisée dans le Cloud.

Pour voir une liste de vos extensions dans Visual Studio, cliquez sur **Outils** > **Extensions et mises à jour**, puis cliquez sur le **Gestionnaire d’extensions itinérantes**.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](media/vs2017ide-extensions-and-updates.png)

Le Gestionnaire d’extensions itinérantes effectue le suivi de toutes les extensions que vous installez, mais vous pouvez choisir celles que vous souhaitez ajouter à votre liste d’itinérance.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](media/vs2017ide-RoamingExtensionManager.png)

Quand vous utilisez le Gestionnaire d’extensions itinérantes, trois types d’icônes figurent dans votre liste :

* ![Icône Itinérante](media/vs2017ide-roamedicon.png) **_Itinérante_**  : Extension qui fait partie de cette liste d’itinérances, mais qui n’est pas installée sur votre machine.
  (Vous pouvez l’installer à l’aide du bouton **Télécharger**.)
* ![Icône Itinérante et installée](media/vs2017ide-roamedinstalledicon.png) **_Itinérante et installée_**: Toutes les extensions qui font partie de cette liste d’itinérances et qui sont installées dans votre environnement de développement.
  (Si vous décidez de ne pas les rendre itinérantes, vous pouvez les supprimer à l’aide du bouton **Arrêter l’itinérance**.)
* ![Icône Installée](media/vs2017ide-installedicon.png) **_Installée_**  : Toutes les extensions qui sont installées dans cet environnement, mais qui ne font pas partie de votre liste d’itinérances.
  (Vous pouvez ajouter des extensions à la liste d’itinérances à l’aide du bouton **Démarrer l’itinérance**.)

Toute extension que vous téléchargez quand vous êtes connecté est ajoutée à votre liste dans la catégorie **Itinérante et installée**. L’extension fait alors partie de votre liste d’itinérance, ce qui vous permet d’y accéder à partir de n’importe quel ordinateur.

### <a name="experience-live-unit-testing"></a>Essayer Live Unit Testing

Dans Visual Studio Enterprise 2017, les tests unitaires en direct offrent des résultats de tests unitaires et une couverture du code dans l’éditeur lorsque vous rédigez du code. Cette fonctionnalité qui s’utilise avec les projets C# et Visual Basic, à la fois pour le .NET Framework et le .NET Core, prend en charge trois frameworks de test : MSTest, xUnit et NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Pour plus d’informations, consultez [Présentation de Live Unit Testing](../test/live-unit-testing-intro.md). Pour obtenir une liste des nouvelles fonctionnalités disponibles dans chaque version de Visual Studio Enterprise 2017, consultez [Nouveautés de Live Unit Testing](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Configurer un pipeline CI/CD

#### <a name="automated-testing"></a>Tests automatisés

Les tests automatisés sont un aspect essentiel de tout pipeline DevOps. Cela vous permet de tester et de publier votre solution de manière cohérente et fiable sur des cycles beaucoup plus courts. Les flux CI/CD (d’intégration continue et de livraison continue) peuvent aider à rendre le processus plus efficace.

Pour obtenir plus d’informations sur les tests automatisés, consultez le billet de blog [Pipeline CI/CD pour les tests automatisés dans DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/).

Pour plus d’informations sur les nouveautés de l’extension DevLabs [Outils de livraison continue pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio), consultez le billet de blog [Commit with confidence: Commit time code quality](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/).

### <a name="visual-studio-ide-enhancements"></a>Améliorations de l’environnement de développement intégré (IDE) de Visual Studio

#### <a name="multi-caret-editing"></a>Modification avec signes insertion multiples

**Nouveautés de la version 15.8** : L’édition simultanée de plusieurs emplacements dans un fichier est désormais chose facile. Commencez par créer des points d’insertion et des sélections à plusieurs endroits dans un fichier. Utilisez ensuite la fonctionnalité de modification avec signes insertion multiples pour effectuer la même modification à plusieurs endroits à la fois.

Pour plus d’informations, consultez la section [Sélection avec signes insertion multiples](finding-and-replacing-text.md#multi-caret-selection) dans la page [Rechercher et remplacer du texte](finding-and-replacing-text.md).

#### <a name="keep-keybinding-profiles-consistent"></a>Maintenir la cohérence des profils de combinaison de touches

**Nouveautés de la version 15.8** : Désormais, vous pouvez maintenir la cohérence de vos combinaisons de touches entre les outils à l’aide de deux nouveaux profils de clavier : Visual Studio Code et ReSharper (Visual Studio). Vous trouverez ces schémas sous **Outils** > **Options** > **Général** > **Clavier** et dans le menu déroulant supérieur.

  ![Nouveaux profils de combinaison de touches pour Visual Studio Code et ReSharper](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Utiliser les nouvelles refactorisations

La refactorisation consiste à améliorer du code existant. Ce processus modifie la structure interne du code sans en changer le comportement. Nous ajoutons souvent de nouvelles refactorisations. En voici quelques-unes :

* Ajouter un paramètre (depuis CallSite)
* Générer des substitutions
* Ajouter un argument nommé
* Ajouter un contrôle de valeur null pour les paramètres
* Insérer des séparateurs numériques dans les littéraux
* Changer la base des littéraux numériques (par exemple, hex en binaire)
* Convertir if-to-switch
* Supprimer la variable inutilisée

Pour plus d’informations, consultez [Actions rapides](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interagir avec Git

Lorsque vous travaillez avec un projet dans Visual Studio, vous pouvez installer et rapidement valider et publier votre code sur un service Git. Vous pouvez également gérer vos référentiels Git en cliquant dans les menus à partir des boutons situés en bas à droite de l’IDE.

![Visual Studio 2017 interagit avec la boîte de dialogue Git](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Amélioration des commandes de navigation

Nous avons actualisé l’expérience de navigation pour permettre le déplacement d’un point A vers un point B de manière plus fiable et directe.

* **Nouveautés de la version 15.4** : **Atteindre la définition** (**Ctrl**+**Clic** ou **F12**) &ndash; Si vous utilisez la souris, vous pouvez maintenant accéder plus rapidement à la définition d’un membre en appuyant sur **Ctrl** puis en cliquant sur le membre. Vous pouvez également appuyer sur **Ctrl** et pointer sur un symbole de code pour le souligner et le transformer en lien. Pour plus d’informations, consultez [Atteindre la définition et Aperçu de la définition](go-to-and-peek-definition.md).

* **Accéder à l’implémentation** (**Ctrl**+**F12**) &ndash; Accédez aux différentes implémentations d’un membre ou d’un type à partir du membre ou du type de base.

* **Atteindre tout** (**Ctrl**+**T** ou **Ctrl**+**,**) &ndash; Accédez directement aux déclarations de fichier/type/membre/symbole. Vous pouvez filtrer votre liste de résultats ou utiliser la syntaxe de requête (par exemple, « f searchTerm » pour les fichiers, « t searchTerm » pour les types, etc.).

  ![Amélioration de la fonctionnalité Atteindre tout](media/vs2017ide-navigation-go-to.png)

* **Rechercher toutes les références** (**Maj**+**F12**) &ndash; Grâce à la colorisation de la syntaxe, vous pouvez regrouper les résultats de la fonctionnalité Rechercher toutes les références par projet, définition et chemin, selon la combinaison choisie. Vous pouvez également « verrouiller » les résultats afin de pouvoir continuer à rechercher d’autres références sans perdre les résultats d’origine.

  ![Nouvel outil Rechercher toutes les références](media/vs2017ide-find-all-references.png)

* **Visualiseur de structure** &ndash; Les lignes verticales grises en pointillé (guides de mise en retrait) servent de repères dans le code pour fournir du contexte dans votre cadre d’affichage. Vous les avez peut-être déjà rencontrées dans le logiciel connu Productivity Power Tools. Vous pouvez les utiliser pour visualiser et distinguer le bloc de code dans lequel vous vous trouvez, à tout moment et sans avoir à faire défiler le code. Pointez sur les lignes pour afficher une info-bulle qui développe le bloc de code et ses éléments parents. Cette fonctionnalité est disponible dans tous les langages pris en charge par le biais des syntaxes TextMate, ainsi que C#, Visual Basic et XAML.

  ![Visualiseur de structure Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Pour plus d’informations sur les nouvelles fonctionnalités de productivité, consultez le billet de blog [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) posté par Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++

Nous avons également ajouté plusieurs améliorations à Visual Studio, notamment la distribution des instructions de base C++ avec Visual Studio, la mise à jour du compilateur grâce à l’amélioration de la prise en charge des fonctionnalités C++ 11 et C++, ainsi que l’ajout et la mise à jour des fonctionnalités dans les bibliothèques C++. Nous avons également amélioré les performances de l’IDE de C++, les charges de travail d’installation et bien plus encore.

Par ailleurs, nous avons corrigé plus de 250 bogues et problèmes signalés dans le compilateur et les outils, dont la plupart avaient été soumis par des clients par le biais de la [Communauté de développeurs C++](https://developercommunity.visualstudio.com/spaces/62/index.html "Communauté de développeurs C++").

Pour plus d’informations, consultez la page [Nouveautés de Visual C++ dans Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).

### <a name="debugging-and-diagnostics"></a>Débogage et diagnostics

#### <a name="run-to-click"></a>Exécuter jusqu’au clic

Maintenant, vous pouvez plus facilement avancer pendant le débogage sans avoir à définir un point d’arrêt sur la ligne souhaitée. Lorsque vous êtes arrêté dans l’outil de débogage, il vous suffit de cliquer sur l’icône qui apparaît en regard de la ligne de code. Votre code sera exécuté jusqu’à cette ligne la prochaine fois qu’il sera atteint dans votre chemin de code.

![Déboguer Visual Studio 2017 - Exécuter jusqu’au clic](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nouvelle assistance d’exception

La nouvelle assistance d’exception vous permet de visualiser les informations d’exception d’un coup d’œil. Les informations sont présentées de manière compacte avec un accès instantané aux exceptions internes. Trouvez rapidement ce qui était Null directement dans l’assistance de l’exception quand vous diagnostiquez une exception NullReferenceException.

![Boîte de dialogue de la nouvelle assistance d’exception dans Visual Studio](media/vs2017ide-ExceptionHelper.png)

Pour plus d’informations, consultez le billet de blog [Use the new Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/devops/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

#### <a name="snapshots-and-intellitrace-step-back"></a>Captures instantanées et retour en arrière IntelliTrace

**Nouveauté de la version 15.5** : Le retour en arrière IntelliTrace crée automatiquement une capture instantanée de votre application à chaque point d’arrêt et chaque étape du débogueur. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils **Déboguer**. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**. Quand vous passez à l’étape précédente ou suivante d’un événement, vous activez automatiquement le débogage d’historique pour l’événement sélectionné.

![Nouvelle boîte de dialogue Assistance sur l’exception dans Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Boutons Étape précédente et Étape suivante")

Pour plus d’informations, consultez la page [Afficher des captures instantanées avec le retour en arrière IntelliTrace](../debugger/view-historical-application-state.md).

### <a name="containerization"></a>Mise en conteneur

Les conteneurs augmentent la densité des applications et réduisent les coûts de développement, tout en améliorant la productivité et l’agilité DevOps.

#### <a name="docker-container-tooling"></a>Outils des conteneurs Docker

**Nouveauté de la version 15.5** :

* Visual Studio fournit des outils pour les conteneurs Docker qui prennent maintenant en charge les fichiers Dockerfile à plusieurs étapes, ce qui simplifie la création d’images conteneur optimisées.
* Par défaut, Visual Studio tire (pull), génère et exécute automatiquement les images de conteneur nécessaires en arrière-plan quand vous ouvrez un projet qui prend en charge Docker. Vous pouvez désactiver cette option via le paramètre **Démarrer automatiquement les conteneurs en arrière-plan** dans Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Développement d’applications cloud avec Azure

### <a name="azure-functions-tools"></a>Azure Functions Tools

Dans le cadre de la charge de travail du « développement Azure », nous avons ajouté des outils pour vous aider à développer des fonctions Azure avec des bibliothèques de classes C# précompilées. Vous pouvez désormais créer, exécuter et déboguer sur votre ordinateur de développement local, puis publier directement sur Azure depuis Visual Studio.

Pour plus d’informations, consultez la page [Azure Functions Tools pour Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs).

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Déboguer des applications ASP.NET en production à l’aide de points d’ancrage et de journalisation dans des applications Azure en production

**Nouveauté de la version 15.5** : Le débogueur de capture instantanée prend une capture instantanée de vos applications en production au moment de l’exécution du code qui vous intéresse. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

La fonctionnalité de capture instantanée est disponible pour les applications web suivantes qui s’exécutent dans Azure App Service :

* Applications ASP.NET exécutées sur .NET Framework version 4.6.1 ou ultérieure.
* Applications ASP.NET Core exécutées sur .NET Core version 2.0 ou ultérieure sur Windows.

Pour plus d’informations, consultez [Déboguer des applications ASP.NET en production en utilisant des points d’ancrage et des points de journalisation ](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Développement d'applications Windows

### <a name="universal-windows-platform"></a>Plateforme Windows universelle

La plateforme Windows universelle (UWP) est la plateforme d’applications pour Windows 10. Avec seulement un ensemble d’API, un package d’application et un Store, vous pouvez développer des applications UWP qui s’exécutent sur tous les appareils Windows 10 &ndash; PC, tablette, téléphone, Xbox, HoloLens, Surface Hub, etc. UWP prend en charge plusieurs tailles d’écran et de nombreux modèles d’interaction (tactile, souris, clavier, contrôleur de jeu ou stylet). La conception des applications UWP s’articule autour de l’idée que les utilisateurs veulent pouvoir utiliser TOUS leurs appareils indifféremment, en choisissant l’appareil qui leur semble le plus pratique ou le plus performant pour la tâche qu’ils ont à faire.

 ![Plateforme Windows universelle](../cross-platform/media/uwp_coreextensions.png)

Choisissez votre langage de développement préféré entre &mdash;C#, Visual Basic, C++ ou JavaScript&mdash; pour créer une application de plateforme Windows universelle exécutable sur les appareils Windows 10. Visual Studio 2017 fournit un modèle d’application UWP pour chaque langage, avec lequel vous pouvez créer un projet unique pour tous les types d’appareils. Après avoir terminé votre projet, vous pouvez créer un package d’application et le soumettre ensuite sur le Microsoft Store à partir de Visual Studio pour distribuer votre application aux utilisateurs d’appareils Windows 10.

**Nouveauté de la version 15.5** : Visual Studio 2017 version 15.5 offre une prise en charge optimale du SDK Windows 10 Fall Creators Update (10.0.16299.0). Windows 10 Fall Creators Update apporte aussi de nombreuses améliorations pour les développeurs d’applications UWP. Voici quelques-uns des changements majeurs : 

* **Prise en charge de .NET Standard 2.0**<br/>En plus de simplifier le processus de développement des applications, Windows 10 Fall Creators Update est la première version de Windows 10 à offrir la prise en charge de .NET Standard 2.0. [.NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/) est une implémentation de référence de la bibliothèque de classes de base que toutes les plateformes .NET peuvent implémenter. L’objectif de .NET Standard est de permettre aux développeurs d’applications .NET de partager plus facilement du code entre les différentes plateformes .NET dont ils ont besoin.
* **Le meilleur d’UWP et de Win32**<br/>Nous avons ajouté la fonctionnalité [Pont du bureau](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) à la plateforme Windows 10 pour que Windows 10 puisse mieux répondre aux besoins de tous les développeurs d’applications .NET ciblant UWP, WPF, Windows Forms ou Xamarin. Avec le nouveau type de projet de création de package d’application disponible dans Visual Studio 2017 version 15.5, vous pouvez créer des packages d’application Windows pour vos projets WPF ou Windows Forms, de la même manière que pour des projets UWP. Une fois que vous avez créé le package de votre application, vous pouvez utiliser toutes les fonctionnalités de déploiement d’applications Windows 10, puis distribuer votre application par le biais de Microsoft Store (pour les applications consommateur) ou de Microsoft Store pour Entreprises et Éducation. Les applications packagées ont accès à la surface d’API UWP complète et aux API Win32 du bureau. Vous pouvez donc maintenant moderniser progressivement vos applications WPF et Windows Forms avec des API UWP et des fonctionnalités Windows 10. De plus, vous pouvez ajouter vos composants Win32 dans vos applications UWP qui sont disponibles sur le bureau avec toutes les fonctionnalités Win32.

Pour plus d’informations sur UWP, consultez la page [Développer des applications pour la plateforme Windows universelle (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md).

## <a name="mobile-app-development"></a>Développement d’applications mobiles

### <a name="xamarin"></a>Xamarin

Dans le cadre de la charge de travail du « développement mobile avec .NET », les développeurs familiarisés avec C#, .NET et Visual Studio peuvent fournir des applications Android, iOS et Windows natives à l’aide de Xamarin. Les développeurs peuvent bénéficier de la même puissance et de la même productivité quand ils travaillent avec Xamarin pour les applications mobiles, notamment le débogage à distance sur les appareils Android, iOS et Windows, sans devoir apprendre les langages de codage natifs comme Objective-C ou Java.

Pour plus d’informations, consultez la page [Visual Studio et Xamarin](/xamarin/).

### <a name="entitlements-editor"></a>Éditeur de droits

**Nouveautés de la version 15.3** : Pour vos besoins de développement iOS, nous avons ajouté un éditeur de droits autonome. Il offre une interface utilisateur conviviale, facile à parcourir. Pour le lancer, double-cliquez sur votre fichier *entitlements.plist*.

![Éditeur de droits pour Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio Tools pour Xamarin

**Nouveautés de la version 15.4** : Xamarin Live permet aux développeurs de déployer, tester et déboguer en continu leurs applications, directement sur des appareils iOS et Android. Après avoir téléchargé Xamarin Live Player &mdash;disponible dans l’App Store ou sur Google Play&mdash;, vous pouvez associer votre appareil avec Visual Studio et révolutionner la façon dont vous créez des applications mobiles. Cette fonctionnalité est désormais incluse dans Visual Studio et peut être activée en accédant à **Outils** > **Options** > **Xamarin** > **Autres** > **Activer Xamarin Live Player**.

![Animation de l’association, du déploiement et des modes d’édition Xamarin Live Player](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Prise en charge de l’Émulateur Android de Google

**Nouveautés de la version 15.8** : Quand vous exécutez Hyper-V, vous pouvez désormais utiliser l’Émulateur Android de Google avec d’autres technologies basées sur Hyper-V, notamment les machines virtuelles Hyper-V, les outils Docker, l’émulateur HoloLens, et bien plus encore. (Cette fonctionnalité nécessite la Mise à jour d’avril 2018 de Windows 10 ou une version ultérieure.)

![Émulateur Android de Google avec les technologies Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Éditeur en mode Fractionné du concepteur Xamarin.Android

Autres **nouveautés de la version 15.8** : Nous avons apporté des améliorations significatives à l’expérience du concepteur pour Xamarin.Android. Un tout nouvel éditeur en mode Fractionné a été introduit pour vous permettre de créer, modifier et afficher un aperçu de vos dispositions.

![Éditeur en mode Fractionné du concepteur Xamarin.Android](media/android-designer-split-view.png)

Pour plus d’informations, consultez [Accélération matérielle pour les performances de l’émulateur](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Nouveauté de la version 15.5** : Visual Studio App Center &mdash;maintenant disponible pour toutes les applications Android, iOS, macOS et Windows&mdash; fournit l’ensemble des fonctionnalités dont vous avez besoin pour gérer le cycle de vie de vos applications, comme l’automatisation des builds, le test sur des appareils réels dans le cloud, la distribution à des testeurs de versions bêta et sur des App Store, et la surveillance de l’utilisation dans des conditions réelles au moyen des incidents et de l’analytique. Les applications écrites en code Objective-C, Swift, Java, C#, Xamarin et React Native prennent en charge l’ensemble de ces fonctionnalités.

  ![Environnement de test Visual Studio App Center](media/app-center-test-env.png)

Pour plus d’informations, consultez le billet de blog [Introducing App Center: Build, test, distribute and monitor apps in the cloud](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/).

## <a name="cross-platform-development"></a>Développement multiplateforme

### <a name="redgate-data-tools"></a>Redgate Data Tools

Pour étendre les fonctionnalités DevOps au développement de base de données SQL Server, les outils Redgate Data Tools sont désormais disponibles dans Visual Studio.

Inclus avec Visual Studio Enterprise 2017 :

* [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) vous permet de développer des scripts de migration, de gérer les modifications de base de données à l’aide du contrôle de code source et d’automatiser en toute sécurité des déploiements de modifications de base de données en même temps que les modifications des applications.
* [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) vous permet d’écrire du code SQL plus rapidement et avec une plus grande précision grâce à la complétion de code intelligente. SQL Prompt complète automatiquement les objets et les mots clés de la base de données et du système, et propose des suggestions de colonne au fil de votre frappe. Cela aboutit à un code plus propre et à moins d’erreurs, car vous n’avez pas à vous souvenir de chaque nom de colonne ni de chaque alias.

Inclus avec toutes les éditions de Visual Studio 2017 :

* [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) augmente votre productivité en vous aidant à trouver rapidement des objets et des fragments SQL parmi plusieurs bases de données.

Pour en savoir plus, consultez le billet de blog [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="net-core"></a>.NET Core

.NET Core est une implémentation généraliste, multiplateforme, modulaire et open source de .NET Standard qui contient de nombreuses API également présentes dans .NET Framework.

La plateforme .NET Core est constituée de différents composants, dont les compilateurs managés, le runtime, les bibliothèques de classes de base et de nombreux modèles d’application, comme ASP.NET Core. .NET Core prend en charge les trois principaux systèmes d’exploitation : Windows, Linux et macOS. Vous pouvez utiliser .NET Core aussi bien dans le cloud que sur des appareils et des systèmes embarqués/IoT.

Il offre aussi maintenant la prise en charge de Docker.

**Nouveautés de la version 15.3** : Visual Studio 2017 version 15.3 prend en charge le développement de .NET Core 2.0. L’utilisation de .NET Core 2.0 nécessite de télécharger et d’installer le kit SDK .NET Core 2.0 séparément.

Pour plus d’informations, consultez la page [Guide .NET Core](/dotnet/core/index).

## <a name="games-development"></a>Développement de jeux

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools pour Unity

Dans le cadre de la charge de travail du « développement de jeux pour Unity », nous avons ajouté des outils pour vous aider dans un développement multiplateforme à créer des jeux 2D et 3D ainsi que du contenu interactif. Créez un seul projet et publiez-le sur 21 plateformes, notamment toutes les plateformes mobiles, le web, WebGL, Mac, PC, postes de travail Linux ou les consoles, avec Visual Studio 2017 et Unity 5.6.

Pour plus d’informations, consultez la page [Visual Studio Tools pour Unity](../cross-platform/visual-studio-tools-for-unity.md).

## <a name="ai-development"></a>Développement IA

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools pour IA

**Nouveauté de la version 15.5** : Utilisez les fonctionnalités de productivité de Visual Studio pour accélérer l’innovation IA aujourd’hui. Utilisez les fonctionnalités intégrées de l’éditeur de code comme la coloration syntaxique, IntelliSense et la mise en forme automatique du texte. Vous pouvez tester de façon interactive votre application d’apprentissage profond (deep learning) dans votre environnement local en effectuant un débogage pas à pas des variables locales et des modèles.

  ![IDE du deep learning](../ai/media/about/ide.png)

Pour plus d’informations, consultez la page [Visual Studio Tools pour AI](../ai/about-ai-tools.md).

## <a name="whats-next"></a>Étapes suivantes

Nous mettons souvent à jour Visual Studio 2017 avec de nouvelles fonctionnalités susceptibles de faciliter l’expérience de développement. Voici un récapitulatif des principales mises à jour actuellement en préversion expérimentale :

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)**, un nouvel outil qui vous permet de partager une base de code et son contexte avec un collègue, et de bénéficier d’une collaboration bidirectionnelle instantanée directement à partir de Visual Studio. Avec Live Share, un collègue peut lire, accéder, modifier et déboguer un projet que vous avez partagé avec lui, de manière sécurisée et fluide.<br><br>Pour plus d’informations, consultez le [FAQ sur Live Share](/visualstudio/liveshare/faq).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**, une nouvelle fonctionnalité qui simplifie le développement de logiciel en faisant appel à l’IA pour fournir une complétion de code plus performante et sensible au contexte. Elle guide les développeurs afin qu’ils codent conformément aux modèles et aux styles de l’équipe, recherche les problèmes de code difficiles à intercepter et focalise les revues de code sur les zones les plus importantes. <br><br>Pour plus d’informations, consultez [Questions fréquentes (FAQ) sur IntelliCode](/visualstudio/intellicode/faq).

Vous souhaitez en savoir plus sur les autres fonctionnalités prévues pour Visual Studio 2017 ? Consultez la page [Feuille de route Visual Studio](/visualstudio/productinfo/vs2018-roadmap).

## <a name="contact-us"></a>Nous contacter

 Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C'est simple : nous prenons très au sérieux les commentaires de nos clients. Ils influencent bon nombre de nos décisions.

Si vous souhaitez faire des suggestions sur la façon dont nous pouvons améliorer Visual Studio, ou en savoir plus sur les options de support produit, consultez la page [Nous contacter](talk-to-us.md).

### <a name="report-a-problem"></a>Signaler un problème

 Parfois, un message ne suffit pas pour transmettre l’impact complet du problème que vous avez rencontré. Si vous rencontrez un blocage, un incident ou un autre problème de performance, vous pouvez utiliser l’outil **Signaler un problème** pour nous envoyer facilement les étapes de reproduction du problème et les fichiers utiles pour le support technique (captures d’écran, fichiers de trace et heap dump, par exemple). Pour plus d’informations sur l’utilisation de cet outil, consultez la page [Guide pratique pour signaler un problème](how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Voir aussi

* [Notes de publication de Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)
* [Nouveautés de Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Nouveautés de C#](/dotnet/csharp/whats-new)
* [Nouveautés de Team Foundation Server](/tfs/server/whats-new?view=vsts)
* [Nouveautés de Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Nouveautés de Visual Studio 2019](whats-new-visual-studio-2019.md)
