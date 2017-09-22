---
title: "Nouveautés de Visual Studio 2017 │ Microsoft Docs"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.technology:
- vs-acquisition
ms.translationtype: HT
ms.sourcegitcommit: 3cd705d703b3d745c502290422e29b3c6da39ee5
ms.openlocfilehash: 5bf00b7e5ed79f8679b837d0dcabf03550d2b849
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Nouveautés dans Visual Studio 2017 RC
#### <a name="updated-for-the-153-release"></a>Ce qui a été mis à jour dans la version 15.3
Une productivité inégalée pour l’ensemble des développements, applications et plateformes. Utilisez Visual Studio 2017 afin de développer des applications pour Android, iOS, Windows, le web et le Cloud. Écrivez votre code rapidement, déboguez et diagnostiquez facilement, testez souvent et publiez en toute confiance. Vous pouvez également étendre et personnaliser Visual Studio en créant vos propres extensions. Avec cette version, utilisez la gestion de versions, soyez agile et collaborez efficacement !

Voici un récapitulatif des modifications que nous avons apportées :

* **Redéfinition des fondamentaux**. Une nouvelle expérience d’installation signifie que vous pouvez installer plus rapidement ce que vous voulez et quand vous en avez besoin. Que vous souhaitiez charger des projets et des solutions de grande taille, ou travailler sur des dossiers de code, voire sur un seul fichier de code, Visual Studio démarre plus vite. Par ailleurs, Visual Studio vous permet de rester concentré sur la vue d’ensemble, en particulier pour les équipes adoptant DevOps.
* **Performances et productivité**. Nous nous sommes concentrés sur les fonctionnalités nouvelles et modernes du développement d’applications mobiles, de bureau et cloud. De plus, nous avons également amélioré l’acquisition, les performances et les expériences de productivité des développeurs en général. Visual Studio démarre plus vite, est plus réactif et utilise moins de mémoire qu’auparavant.
* **Développement d’applications Cloud avec Azure**. Une suite intégrée d’outils Azure vous permet de créer facilement des applications prioritairement centrées sur le cloud et optimisées par Microsoft Azure. Visual Studio vous permet de facilement configurer, générer, déboguer, packager et déployer des applications et services sur Azure.
* **Développement d’applications mobiles**. Dans Visual Studio 2017, vous pouvez innover et obtenir des résultats rapides grâce à Xamarin, qui unifie vos besoins mobiles multi-plateformes à l’aide d’une base de code et d’un ensemble de compétences essentiels. Favorisez la mobilité de vos équipes existantes, les investissements technologiques, et optez pour le code C# pour créer des expériences consommateur en avance et pour un budget inférieur. Accélérez chaque étape du cycle de vie mobile pour offrir des expériences consommateur de classe mondiale ou un portefeuille d’applications de productivité pour encourager la mobilité de votre personnel.
* **Développement multiplateforme** Livrez sans plus d’effort des logiciels pour toutes les plateformes ciblées. Étendez les processus DevOps à SQL Server à l’aide de Redgate Data Tools et automatisez en toute sécurité les déploiements de bases de données à partir de Visual Studio. Développez et publiez des jeux multiplateformes à l’aide de Visual Studio Tools pour Unity. Sinon, utilisez .NET Core pour écrire des applications et des bibliothèques qui s’exécutent sans modification sur les systèmes d’exploitation Windows, Linux et macOS. (Une nouveauté également dans la version 15.3 : la prise en charge côte à côte des kits SDK .NET Core 2.0.)

> [!NOTE]
> Pour obtenir une liste complète des nouvelles fonctions et fonctionnalités dans Visual Studio 2017, consultez les [Notes de mise à jour](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Voici des informations détaillées sur quelques-unes des nouvelles fonctionnalités et des améliorations les plus marquantes de Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Principes de base redéfinis
### <a name="a-new-setup-experience"></a>Une nouvelle expérience d'installation

[Télécharger Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou [Vérifier la configuration système requise pour Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Visual Studio simplifie et accélère l’installation des fonctionnalités dont vous avez besoin, quand vous en avez besoin. Une désinstallation « propre » est également disponible.

 Le changement le plus important à constater lors de l’installation de Visual Studio est la nouvelle expérience proposée. Dans l’onglet **Charges de travail**, les options d’installation sont regroupées pour représenter les plateformes, les langages et les frameworks courants. Il couvre tout depuis le développement .NET Desktop au développement d’applications sur Windows, Linux et iOS.

Choisissez les charges de travail dont vous avez besoin et modifiez-les quand vous le souhaitez.

 ![Boîte de dialogue d’installation de Visual Studio 2017](../install/media/install-visual-studio-enterprise.png "Écran d’installation de Visual Studio 2017")

Vous voulez choisir vos propres composants au lieu d’utiliser des charges de travail ? Sélectionnez l’onglet **Composants individuels** du programme d’installation. Vous souhaitez installer des modules linguistiques sans avoir à modifier les options de langue de Windows ? Choisissez l’onglet **Modules linguistiques** du programme d’installation.  

Pour en savoir plus sur la nouvelle expérience d’installation, notamment pour obtenir des instructions pas à pas, consultez notre page [Installer Visual Studio](../install/install-visual-studio.md).

## <a name="performance-and-productivity"></a>Performances et productivité
### <a name="sign-in-across-multiple-accounts"></a>Se connecter sur plusieurs comptes  
Nous avons introduit dans Visual Studio un nouveau service d’identité qui permet de partager des comptes d’utilisateur dans Team Explorer, Azure Tools, la publication dans le Windows Store, et bien plus encore.

Vous pouvez rester connecté plus longtemps également. Visual Studio ne vous demande pas de vous reconnecter toutes les 12 heures. Pour en savoir plus, consultez le billet de blog [Invites de connexion à Visual Studio moins nombreuses](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="start-visual-studio-faster"></a>Démarrer Visual Studio plus rapidement
Le nouveau Centre de performances Visual Studio peut vous aider à optimiser le temps de démarrage de votre IDE. Le Centre de performances répertorie toutes les extensions et les fenêtres d’outils susceptibles de ralentir le démarrage de l’IDE. Vous pouvez l’utiliser pour améliorer les performances de démarrage en déterminant quand les extensions démarrent, ou si les fenêtres d’outils sont ouvertes au démarrage.

### <a name="decrease-solution-load-time"></a>Accélérer la vitesse de chargement des solutions
Le fait de travailler sur des solutions qui contiennent de nombreux projets ne signifie pas que vous devez travailler avec tous les fichiers ou projets en même temps. Vous pouvez maintenant modifier et déboguer sans attendre que Visual Studio charge chaque projet. Pour essayer avec des projets managés, activez le **Chargement de solution allégé** à partir d’Outils-> Options-> Projets et solutions.

  ![Boîte de dialogue Options dans Visual Studio 2017](../ide/media/vs2017ide-lightweight-solution-load.png "Visual Studio 2017 - Boîte de dialogue Options - Chargement de solution allégé pour toutes les solutions")

### <a name="faster-on-demand-loading-of-extensions"></a>Accélération du chargement des extensions à la demande
Visual Studio déplace ses extensions (et fonctionne également avec des extensions tierces) pour un chargement à la demande, plutôt qu’au démarrage de l’IDE. Vous êtes curieux de savoir quelles extensions ont un impact sur le démarrage, le chargement de solution et les performances de la frappe ? Vous pouvez afficher ces informations dans Aide -> Gérer le niveau de performance de Visual Studio.

  ![Boîte de dialogue Options dans Visual Studio 2017](../ide/media/vs2017ide-manage-vs-perf.png "Boîte de dialogue Aide de Visual Studio - Gestion des performances")

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gérer vos extensions avec le Gestionnaire d’extensions itinérantes
Il est plus facile de configurer chaque environnement de développement avec vos extensions préférées quand vous vous connectez à Visual Studio. Le nouveau Gestionnaire d’extensions itinérantes effectue le suivi de toutes vos extensions préférées en créant une liste synchronisée dans le Cloud.  

Pour afficher une liste de vos extensions dans Visual Studio, cliquez sur Outils > Extensions et mises à jour, puis cliquez sur le Gestionnaire d’extensions itinérantes.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](../ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 - Outils > Boîte de dialogue Extensions et mises à jour")

Le Gestionnaire d’extensions itinérantes effectue le suivi de toutes les extensions que vous installez, mais vous pouvez choisir celles que vous souhaitez ajouter à votre liste d’itinérance.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Outils > Gestionnaire d’extensions itinérantes")

Quand vous utilisez le Gestionnaire d’extensions itinérantes, trois types d’icônes figurent dans votre liste :
* ![Icône Itinérante](../ide/media/vs2017ide-roamedicon.png "Icône Itinérante") ***Itinérante*** : extension qui fait partie de cette liste d’itinérances, mais qui n’est pas installée sur votre ordinateur.
  (Vous pouvez l’installer à l’aide du bouton **Télécharger**.)
* ![Icône Itinérante et installée](../ide/media/vs2017ide-roamedinstalledicon.png "Icône Itinérante et installée") ***Itinérante et installée*** : toutes les extensions qui font partie de cette liste d’itinérances et qui sont installées dans votre environnement de développement.
  (Si vous décidez de ne pas les rendre itinérantes, vous pouvez les supprimer à l’aide du bouton **Arrêter l’itinérance**.)
* ![Icône Installée](../ide/media/vs2017ide-installedicon.png "Icône Installée") ***Installée*** : toutes les extensions qui sont installées dans cet environnement, mais qui ne font pas partie de votre liste d’itinérances.
  (Vous pouvez ajouter des extensions à la liste d’itinérances à l’aide du bouton **Démarrer l’itinérance**.)

Toute extension que vous téléchargez quand vous êtes connecté est ajoutée à votre liste comme **Itinérante et installée**, et fait donc partie de votre liste d’itinérances, ce qui vous permet d’y accéder à partir de n’importe quel ordinateur.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Bénéficier de la validation de la dépendance d’architecture en direct et des tests unitaires en direct
À mesure que vous tapez du code dans l’éditeur de code, Visual Studio vous informe en temps réel des violations de règle de dépendances architecturales grâce aux diagrammes de validation des dépendances (ou diagrammes de couche).

Les erreurs apparaissent dans la liste des erreurs, tandis que des tildes dans l’éditeur de texte indiquent l’emplacement précis de cette violation. Vous êtes maintenant moins susceptible d’introduire des dépendances indésirables.

![Validation de l’architecture en direct](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Validation des dépendances de l’architecture en direct")

#### <a name="live-unit-testing"></a>Live Unit Testing
Dans Visual Studio Enterprise 2017, les tests unitaires en direct offrent des résultats de tests unitaires et une couverture du code dans l’éditeur lorsque vous rédigez du code. Cette fonctionnalité qui s’utilise avec les projets C# et Visual Basic, à la fois pour le .NET Framework et le .NET Core, prend en charge trois frameworks de test : MSTest, xUnit et NUnit.

![Tests unitaires en direct](../ide/media/lut-codewindow.png "Un exemple de notre nouvelle fonctionnalité Tests unitaires en direct de l’édition Enterprise de Visual Studio")

Pour plus d’informations, consultez le billet de blog [Live Unit Testing in Visual Studio 2017 Enterprise](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/).

#### <a name="set-up-a-cicd-pipeline-to-run-automated-tests-efficiently"></a>Configurer un pipeline CI/CD pour exécuter efficacement les tests automatisés
Les tests automatisés sont un aspect essentiel de tout pipeline DevOps. Cela vous permet de tester et de publier votre solution de manière cohérente et fiable sur des cycles beaucoup plus courts. Les flux CI/CD (d’intégration continue et de livraison continue) peuvent aider à rendre le processus plus efficace.

Pour obtenir plus d’informations sur les tests automatisés, consultez le billet de blog [Pipeline CI/CD pour les tests automatisés dans DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/).

Et, pour plus d’informations sur les nouveautés de l’extension DevLabs [Outils de livraison continue pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio), consultez le billet de blog [Validation en toute confiance : valider la qualité du Code temps](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/).

### <a name="a-focus-on-accessibility"></a>Accent sur l’accessibilité
Dans la version 15.3, nous avons apporté plus de 1 700 correctifs ciblés visant à améliorer la compatibilité entre Visual Studio et les technologies d’assistance qu’utilisent la plupart de nos clients. Il existe des douzaines de scénarios plus compatibles avec les lecteurs d’écran, les thèmes de contraste élevé et autres technologies d’assistance que jamais auparavant. Le débogueur, éditeur et interpréteur de commandes ont tous également obtenus des améliorations significatives.

Pour plus d’informations sur l’accessibilité, consultez le billet de blog [Améliorations de l’accessibilité dans Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/).

### <a name="visual-studio-ide-enhancements"></a>Améliorations de l’environnement de développement intégré (IDE) de Visual Studio
#### <a name="use-new-refactorings"></a>Utiliser les nouvelles refactorisations
Dans cette version 15.3, nous avons ajouté un certain nombre de nouvelles refactorisations, notamment :
*   Résoudre le conflit de fusion
*   Ajouter un paramètre (depuis CallSite)
*   Générer des substitutions
*   Ajouter un argument nommé
*   Ajouter un contrôle de valeur null pour les paramètres
*   Insérer des séparateurs numériques dans les littéraux
*   Changer la base des littéraux numériques (par exemple, hex en binaire)
*   Convertir if-to-switch
*   Supprimer la variable inutilisée

Pour plus d’informations, consultez la page [Refactorisation, génération de code et actions rapides dans Visual Studio](refactoring-code-generation-quick-actions.md).


#### <a name="interact-with-git"></a>Interagir avec Git
Lorsque vous travaillez avec un projet dans Visual Studio, vous pouvez installer et rapidement valider et publier votre code sur un service Git. Vous pouvez également gérer vos référentiels Git en cliquant dans les menus à partir des boutons situés en bas à droite de l’IDE.

![Visual Studio 2017 interagit avec la boîte de dialogue Git](../ide/media/vsIDE-GitInteraction.png "Outils Git dans l’IDE de Visual Studio")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Afficher et parcourir le code avec le visualiseur de structure
Le Visualiseur de structure dessine des lignes de repère de structure (ou guides de mise en retrait) dans votre code. Vous pouvez les utiliser pour visualiser et distinguer le bloc de code dans lequel vous vous trouvez, à tout moment et sans avoir à faire défiler le code. Survolez les lignes pour afficher les info-bulles qui vous permettent de voir l’ouverture de ce bloc et de ses parents. Il est disponible dans tous les langages pris en charge via les syntaxes TextMate, ainsi que C#, Visual Basic et XAML.

![Visualiseur de structure Visual Studio 2017](../ide/media/vsIDE-StructureVisualizer.png "Visualiseur de Structure dans Visual Studio")

#### <a name="experience-improved-navigation-controls"></a>Amélioration des commandes de navigation
Nous avons actualisé l’expérience de navigation pour permettre le déplacement d’un point A vers un point B de manière plus fiable et directe.

* **Atteindre** (Ctrl + F12) &ndash; accède depuis n’importe quel type ou membre de base à ses diverses implémentations.

* **Atteindre** (Ctrl + T ou Ctrl +,) &ndash; accède directement à toute déclaration de fichier/type/membre/symbole. Vous pouvez filtrer votre liste de résultats ou utiliser la syntaxe de requête (par exemple, « f searchTerm » pour les fichiers, « t searchTerm » pour les types, etc.).

 ![Amélioration de Atteindre tout](../ide/media/vs2017ide-navigation-go-to.png "Exemple de la fonctionnalité Atteindre tout améliorée")

* **Rechercher toutes les références (Maj + F12)** &ndash; grâce à la colorisation de syntaxe, vous pouvez regrouper les résultats obtenus via la fonctionnalité Rechercher toutes les références par une combinaison de projets, de définitions et de chemins. Vous pouvez également « verrouiller » les résultats afin de pouvoir continuer à rechercher d’autres références sans perdre les résultats d’origine.

 ![Nouvel outil Rechercher toutes les références](../ide/media/vs2017ide-find-all-references.png "Exemple du nouvel outil Rechercher toutes les références")

* **Guides de mise en retrait** &ndash; lignes verticales grises en pointillé, qui agissent comme des repères dans le code pour fournir du contexte dans le cadre de la vue. Vous les avez peut-être déjà rencontrées dans le logiciel connu Productivity Power Tools.

Pour plus d’informations sur nos nouvelles fonctionnalités de productivité, consultez le billet de blog [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) (Productivité dans Visual Studio 2017) par Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++
Nous avons également ajouté plusieurs améliorations à Visual Studio, notamment la distribution des instructions de base C++ avec Visual Studio, la mise à jour du compilateur grâce à l’amélioration de la prise en charge des fonctionnalités C++ 11 et C++, ainsi que l’ajout et la mise à jour des fonctionnalités dans les bibliothèques C++. Nous avons également amélioré les performances de l’IDE de C++, les charges de travail d’installation et bien plus encore.

Par ailleurs, nous avons corrigé plus de 250 bogues et signalé des problèmes dans le compilateur et les outils, dont la plupart avaient été soumis par des clients via [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Pour obtenir des détails complets, consultez notre page sur les [Nouveautés de Visual C++ dans Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  

### <a name="debugging-and-diagnostics"></a>Débogage et diagnostics
#### <a name="run-to-click"></a>Exécuter jusqu’au clic :
Maintenant, vous pouvez plus facilement avancer pendant le débogage sans avoir à définir un point d’arrêt sur la ligne souhaitée. Lorsque vous êtes arrêté dans l’outil de débogage, il vous suffit de cliquer sur l’icône qui apparaît en regard de la ligne de code. Votre code sera exécuté jusqu’à cette ligne la prochaine fois qu’il sera atteint dans votre chemin de code.

![Déboguer Visual Studio 2017 - Exécuter jusqu’au clic](../ide/media/vs2017ide-RunToClick.png "Exécuter jusqu’au clic dans Visual Studio - Débogage et diagnostic")

#### <a name="the-new-exception-helper"></a>Nouvelle assistance d’exception :
La nouvelle assistance d’exception vous permet de visualiser les informations d’exception d’un coup d’œil. Les informations sont présentées de manière compacte avec un accès instantané aux exceptions internes. Trouvez rapidement ce qui était Null directement dans l’assistance de l’exception quand vous diagnostiquez une exception NullReferenceException.

![Boîte de dialogue de la nouvelle assistance d’exception dans Visual Studio](../ide/media/vs2017ide-ExceptionHelper.png "Boîte de dialogue de la nouvelle assistance d’exception")

Pour plus d’informations, consultez le billet de blog sur l’[utilisation de la nouvelle assistance d’exception dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

## <a name="cloud-app-development-with-azure"></a>Développement d’applications cloud avec Azure
### <a name="azure-functions-tools"></a>Azure Functions Tools
Dans le cadre de la charge de travail du « développement Azure », nous avons ajouté des outils pour vous aider à développer des fonctions Azure avec des bibliothèques de classes C# précompilées. Vous pouvez désormais créer, exécuter et déboguer sur votre ordinateur de développement local, puis publier directement sur Azure depuis Visual Studio.

Pour plus d’informations, consultez la page [Azure Functions Tools pour Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs).

## <a name="mobile-app-development"></a>Développement d’applications mobiles
### <a name="xamarin"></a>Xamarin
Dans le cadre de la charge de travail du « développement mobile avec .NET », les développeurs familiarisés avec C#, .NET et Visual Studio peuvent fournir des applications Android, iOS et Windows natives à l’aide de Xamarin. Les développeurs peuvent bénéficier de la même puissance et de la même productivité quand ils travaillent avec Xamarin pour les applications mobiles, notamment le débogage à distance sur les appareils Android, iOS et Windows, sans devoir apprendre les langages de codage natifs comme Objective-C ou Java.

Pour plus d’informations, consultez la page [Visual Studio et Xamarin](../cross-platform/visual-studio-and-xamarin.md).

### <a name="entitlements-editor"></a>Éditeur de droits
**Nouveauté de 15.3** : pour vos besoins de développement iOS, nous avons ajouté un éditeur de droits autonome. Il offre une interface utilisateur conviviale, facile à parcourir. Pour la lancer, double-cliquez sur votre fichier entitlements.plist.

![Éditeur de droits pour Xamarin](../ide/media/xamarin-entitlements-editor.png "Éditeur droits pour Xamarin")

## <a name="cross-platform-development"></a>Développement multiplateforme
### <a name="redgate-data-tools"></a>Redgate Data Tools
Pour étendre les fonctionnalités DevOps au développement de base de données SQL Server, les outils Redgate Data Tools sont désormais disponibles dans les éditions suivantes de Visual Studio 2017.

Inclus avec Visual Studio Enterprise 2017 :
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) vous permet de développer des scripts de migration, de gérer les modifications de base de données à l’aide du contrôle de code source et d’automatiser en toute sécurité des déploiements de modifications de base de données en même temps que les modifications des applications.
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) vous permet d’écrire du code SQL plus rapidement et avec une plus grande précision grâce à la complétion de code intelligente. SQL Prompt complète automatiquement les objets et les mots clés de la base de données et du système, et propose des suggestions de colonne au fil de votre frappe. Cela aboutit à un code plus propre et à moins d’erreurs, car vous n’avez pas à vous souvenir de chaque nom de colonne ni de chaque alias.

Inclus avec toutes les éditions de Visual Studio 2017 :
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) augmente votre productivité en vous aidant à trouver rapidement des objets et des fragments SQL parmi plusieurs bases de données.

Pour en savoir plus, consultez notre billet de blog [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools pour Unity
Dans le cadre de la charge de travail du « développement de jeux pour Unity », nous avons ajouté des outils pour vous aider dans un développement multiplateforme à créer des jeux 2D et 3D ainsi que du contenu interactif. Créez un seul projet et publiez-le sur 21 plateformes, notamment toutes les plateformes mobiles, le web, WebGL, Mac, PC, postes de travail Linux ou les consoles, avec Visual Studio 2017 et Unity 5.6.

Pour plus d’informations, consultez la page [Visual Studio Tools pour Unity](../cross-platform/visual-studio-tools-for-unity.md).

### <a name="net-core"></a>.NET Core
.NET Core est une implémentation généraliste, multiplateforme, modulaire et open source de .NET Standard qui contient de nombreuses API également présentes dans .NET Framework.

La plateforme .NET Core est constituée de différents composants, dont les compilateurs managés, le runtime, les bibliothèques de classes de base et de nombreux modèles d’application, comme ASP.NET Core. .NET Core prend en charge les trois principaux systèmes d’exploitation : Windows, Linux et macOS. Vous pouvez utiliser .NET Core aussi bien dans le cloud que sur des appareils et des systèmes embarqués/IoT.

Et il inclut désormais la prise en charge de Docker.

**Nouveauté de 15.3** : Visual Studio 2017 version 15.3 prend en charge le développement de .NET Core 2.0. (Dans la version 15.3, l’utilisation de .NET Core 2.0 nécessite de télécharger et d’installer le kit SDK .NET Core 2.0 séparément.)

Pour plus d’informations, consultez la page [Guide .NET Core](https://docs.microsoft.com/dotnet/core/index).

## <a name="talk-to-us"></a>Nous contacter  
 Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C’est simple : nous prenons très au sérieux les commentaires de nos clients, car ils influencent bon nombre de nos décisions.

Si vous souhaitez faire des suggestions sur la façon dont nous pouvons améliorer Visual Studio, ou signaler un problème, consultez la page [Nous contacter](../ide/talk-to-us.md) pour en savoir plus.

### <a name="report-a-problem"></a>Signaler un problème  
 Parfois, un message ne suffit pas pour transmettre l’impact complet du problème que vous avez rencontré. Si vous rencontrez un blocage, un incident ou autre problème de performances, vous pouvez facilement partager avec nous les étapes de reproduction et les fichiers de prise en charge (tels que des captures d’écran et des fichiers de trace et de vidage de tas) à l’aide de l’outil **Signaler un problème**. Pour plus d’informations sur l’utilisation de cet outil, consultez la page [Guide pratique pour signaler un problème](how-to-report-a-problem-with-visual-studio-2017.md).

### <a name="track-your-issue-in-connect"></a>Effectuer le suivi d'un problème dans Connect  
 Si vous voulez savoir où en est la prise en compte de vos commentaires sur Visual Studio, accédez à la page [Connect](http://connect.microsoft.com/) pour y signaler le bogue. Après cela, vous pouvez revenir à Connect pour suivre l’état du bogue.

## <a name="see-also"></a>Voir aussi
* [Notes de publication de Visual Studio 2017](https://www.visualstudio.com/news/vs2015-vs)
* [Nouveautés de Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Nouveautés de C#](https://docs.microsoft.com/dotnet/csharp/csharp-7)  
* [Nouveautés de Team Foundation Server](https://www.visualstudio.com/docs/whats-new)
* [Nouveautés de Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

