---
title: "Nouveautés dans Visual Studio 2017 RC | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2016
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
translationtype: Human Translation
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Nouveautés dans Visual Studio 2017 RC
Bienvenue dans Visual Studio 2017 RC, une suite intégrée d’outils de productivité pour les développeurs, de services cloud et d’extensions qui vous permettent, à vous et votre équipe, de créer de superbes applications et de magnifiques jeux pour le web, le Windows Store, le Bureau, Android et iOS.  

Dans cette version Release Candidate de Visual Studio, nous nous sommes concentrés sur les améliorations de performances et de productivité. Du point de vue des performances, Visual Studio démarre plus rapidement, est plus réactif et utilise moins de mémoire. Du point de vue de la productivité, nous avons ajouté ou mis à jour des fonctionnalités qui peuvent vous aider à être plus efficace quand vous utilisez Visual Studio.

> [!TIP]
> Pour voir notre nouvelle version RC en action, regardez la vidéo sur les [nouveautés dans Visual Studio](https://channel9.msdn.com/events/connect/2016/159) sur Channel 9.   

Voici un récapitulatif des modifications que nous avons apportées :

* **Améliorations de la productivité**. Les améliorations apportées à la navigation dans le code, à IntelliSense, à la refactorisation, aux corrections de code et au débogage vous font gagner du temps et facilitent les tâches quotidiennes, quel que soit le langage ou la plateforme. De plus, si votre équipe a adopté DevOps, Visual Studio 2017 simplifie le fonctionnement interne du développement et accélère le flux de génération du code grâce aux toutes nouvelles fonctionnalités en temps réel, telles que le test unitaire en direct et la validation en temps réel des dépendances architecturales.
* **Redéfinition des fondamentaux**.  Nous portons un intérêt renouvelé à l’amélioration des tâches fondamentales que les développeurs doivent effectuer tous les jours. De la toute nouvelle installation modulaire et légère adaptée aux besoins du développeurs, à l’IDE plus rapide du début à la fin, en passant par les nouvelles façons d’afficher, de modifier et de déboguer le code sans projets et solutions, Visual Studio 2017 aide les développeurs à se focaliser sur la vision d’ensemble.
* **Simplification du développement Azure**. Suite intégrée d’outils Azure qui permettent aux développeurs de créer des applications prioritairement centrées sur le cloud et alimentées par Microsoft Azure. Visual Studio vous permet de facilement configurer, générer, déboguer, packager et déployer des applications et services sur Microsoft Azure directement à partir de l’IDE.
* **Développement mobile cinq étoiles**. Avec les fonctionnalités avancées de débogage, de profilage et de génération de tests unitaires, Visual Studio 2017 avec Xamarin accélère et facilite la création, la connexion et le paramétrage d’applications mobiles pour Android, iOS et Windows. Les développeurs peuvent aussi choisir de développer des applications mobiles avec le développement de bibliothèque multiplateforme Apache Cordova ou Visual C++ dans Visual Studio.  

Voici plus d’informations sur les changements les plus importants.

> [!NOTE]
> Pour obtenir une liste complète des nouvelles fonctions et fonctionnalités dans Visual Studio 2017 RC et la version RC Refresh suivante, consultez les [Notes de mise à jour](https://www.visualstudio.com/news/vs2015-vs). Pour obtenir la liste des problèmes et solutions de contournement, consultez la section [Problèmes connus](https://www.visualstudio.com/news/vs2015-vs#knownissues) des Notes de mise à jour.   

## <a name="performance-improvements"></a>Amélioration des performances

### <a name="a-new-setup-experience"></a>Une nouvelle expérience d'installation  
[Télécharger Visual Studio Enterprise 2017 RC](https://aka.ms/vs/15/preview/vs_enterprise) ou [Vérifier la configuration système requise pour Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Nous avons remanié l’expérience d’installation de Visual Studio pour qu’il soit encore plus facile d’installer uniquement les fonctionnalités dont vous avez besoin, quand vous en avez besoin. Nous avons également réduit l’encombrement minimal pour que Visual Studio s’installe plus rapidement avec moins d’impact sur le système. Une désinstallation « propre » est également disponible.

 Le changement le plus important que vous constaterez quand vous installerez Visual Studio est sa nouvelle expérience d’installation. Sous l’onglet **Charges de travail** figurent des options d’installation regroupées afin de représenter les frameworks, les langages et les plateformes courants, couvrant tout ce qui va du développement d’applications de bureau .NET à la science des données avec R, Python et F#.  

 ![Boîte de dialogue d’installation de Visual Studio 2017 RC ](../ide/media/willow1.png "VS2017RC_Setup_screen")

Choisissez les charges de travail dont vous avez besoin et modifiez-les quand vous le souhaitez. L’installation minimale nécessite seulement quelques centaines de mégaoctets, mais inclut néanmoins la prise en charge de la modification du code de base pour plus de&20; langages, ainsi que le contrôle de code source.

Nous avons également ajouté différentes méthodes d’installation de Visual Studio. Vous voulez choisir vos propres composants au lieu d’utiliser des charges de travail ? Il vous suffit de sélectionner l’onglet **Composants individuels** du programme d’installation. Vous souhaitez installer des modules linguistiques sans avoir à modifier les options de langue de Windows ? Choisissez l’onglet **Modules linguistiques** du programme d’installation.  

Pour en savoir plus sur la nouvelle expérience d’installation, notamment pour obtenir des instructions pas à pas, consultez notre page [Installer Visual Studio](../install/install-visual-studio.md).


### <a name="start-visual-studio-faster"></a>Démarrer Visual Studio plus rapidement
Si Visual Studio détecte que la vitesse de démarrage de l’IDE est lente, il fournit un nouveau Centre de performances Visual Studio pour vous aider à accélérer l’opération. Le Centre de performances répertorie toutes les extensions et les fenêtres d’outils qui ralentissent le démarrage de l’IDE. Vous pouvez l’utiliser pour améliorer les performances de démarrage en déterminant quand les extensions démarrent, ou si les fenêtres d’outils sont ouvertes au démarrage.

### <a name="decrease-solution-load-time"></a>Accélérer la vitesse de chargement des solutions
Le fait de travailler sur des solutions qui contiennent plus de 100 projets ne signifie pas que vous devez travailler avec tous les fichiers ou projets en même temps. Vous pouvez maintenant modifier et déboguer sans attendre que Visual Studio charge chaque projet. Pour essayer avec des projets managés, activez le **Chargement de solution allégé** à partir d’Outils-> Options-> Projets et solutions.

  ![Boîte de dialogue Options dans Visual Studio 2017 RC](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "Boîte de dialogue Options dans Visual Studio 2017 RC - Chargement de solution allégé")

### <a name="faster-on-demand-loading-of-extensions"></a>Accélération du chargement des extensions à la demande
Le concept est simple : charger les extensions quand elles sont nécessaires plutôt qu’au démarrage de Visual Studio. Tout d’abord, nous avons fait en sorte que nos extensions Python et Xamarin soient chargées à la demande. Ensuite, nous mettons actuellement tout en œuvre pour que toutes les extensions fournies avec Visual Studio (et celles fournies par des fournisseurs tiers) adoptent ce modèle. Vous êtes curieux de savoir quelles extensions ont un impact sur le démarrage, le chargement de solution et les performances de la frappe ? Vous pouvez afficher ces informations dans Aide -> Gérer le niveau de performance de Visual Studio.

  ![Boîte de dialogue Options dans Visual Studio 2017 RC](../ide/media/vs2017ide-ManageVSperf.png "Boîte de dialogue Aide de VS2017RC - Gestion des performances")

## <a name="productivity-improvements"></a>Améliorations de la productivité

### <a name="sign-in-across-multiple-accounts"></a>Se connecter sur plusieurs comptes  
Nous avons introduit dans Visual Studio 2017 RC un nouveau service d’identité qui permet de partager des comptes d’utilisateur parmi les outils de développement Microsoft, tels que Team Explorer, Azure Tools, la publication dans le Windows Store, et bien plus encore.

Vous pouvez aussi rester connecté plus longtemps. Nous ne vous demanderons plus de vous reconnecter toutes les 12 heures. Pour en savoir plus, consultez le billet de blog [Invites de connexion à Visual Studio moins nombreuses](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gérer vos extensions avec le Gestionnaire d’extensions itinérantes
Il est désormais encore plus facile de configurer chaque environnement de développement avec vos extensions préférées quand vous vous connectez à Visual Studio. Notre nouveau Gestionnaire d’extensions itinérantes effectue le suivi des toutes vos extensions préférées en créant une liste synchronisée dans le cloud.  

Pour afficher une liste de vos extensions dans Visual Studio, cliquez sur Outils > Extensions et mises à jour, puis cliquez sur le Gestionnaire d’extensions itinérantes.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017 - Outils > Boîte de dialogue Extensions et mises à jour")

Le Gestionnaire d’extensions itinérantes effectue le suivi de toutes les extensions que vous installez, mais vous pouvez choisir celles que vous souhaitez ajouter à votre liste d’itinérance.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Outils > Gestionnaire d’extensions itinérantes")

Quand vous utilisez le Gestionnaire d’extensions itinérantes, trois types d’icônes figurent dans votre liste :
* ![Icône Itinérante](../ide/media/vs2017ide-roamedicon.png "Icône Itinérante") ***Icône Itinérante*** : extension qui fait partie de cette liste d’itinérances, mais qui n’est pas installée sur votre ordinateur.
  (Vous pouvez l’installer à l’aide du bouton **Télécharger**.)
* ![Icône Itinérante et installée](../ide/media/vs2017ide-roamedinstalledicon.png "Icône Itinérante et installée") ***Icône Itinérante et installée*** : toutes les extensions qui font partie de cette liste d’itinérances et qui sont installées dans votre environnement de développement.
  (Si vous décidez de ne pas les rendre itinérantes, vous pouvez les supprimer à l’aide du bouton **Arrêter l’itinérance**.)
* ![Icône Installée](../ide/media/vs2017ide-installedicon.png "Icône Installée") ***Icône Installée*** : toutes les extensions qui sont installées dans cet environnement, mais qui ne font pas partie de votre liste d’itinérances.
  (Vous pouvez ajouter des extensions à la liste d’itinérances à l’aide du bouton **Démarrer l’itinérance**.)

Ces icônes montrent l’état actuel de votre liste. Vous pouvez avoir n’importe quelle extension dans n’importe quel état, alors personnalisez-les comme bon vous semble ! Ou laissez-nous faire ! Toute extension que vous téléchargez quand vous êtes connecté est ajoutée à votre liste comme **Itinérante et installée**, et fait donc partie de votre liste d’itinérances, ce qui vous permet d’y accéder à partir de n’importe quel ordinateur !

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Bénéficier de la validation de la dépendance d’architecture en direct et des tests unitaires en direct

Dans Visual Studio Enterprise 2017 RC, si vous avez configuré des diagrammes de Validation de la dépendance (également appelés diagrammes de couche), vous pouvez maintenant être informé en temps réel des violations de règle de dépendances architecturales à mesure que vous tapez du code dans l’Éditeur de code.

Les erreurs apparaissent dans la liste Erreurs, et des tildes dans l’Éditeur de texte vous indiquent l’emplacement précis d’une violation. Vous êtes maintenant moins susceptible d’introduire des dépendances indésirables.

![Validation de l’architecture en direct](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Validation des dépendances de l’architecture en direct")

#### <a name="live-unit-testing"></a>Tests unitaires en direct :

Les tests unitaires en direct sont une nouvelle fonctionnalité disponible uniquement dans l’édition Enterprise de Visual Studio. Elle permet de visualiser les résultats des tests unitaires et la couverture du code en direct sur l’éditeur au fur et à mesure que vous écrivez du code. Elle fonctionne avec les projets C#/VB pour le .NET Framework et prend en charge trois frameworks de test : MSTest, xUnit et NUnit.

### <a name="visual-studio-ide-enhancements"></a>Améliorations de l’environnement de développement intégré (IDE) de Visual Studio
#### <a name="interact-with-git"></a>Interagissez avec Git :
Des contrôles dans la partie inférieure de l’IDE de Visual Studio vous permettent de valider et de publier rapidement vos projets GIT, et de gérer vos dépôts Git.

![Boîte de dialogue d’installation de Visual Studio 2017 RC](../ide/media/vsIDE-GitInteraction.png "Git-tools-in-the-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Afficher et parcourir le code avec le Visualiseur de structure :
Une nouvelle fonctionnalité appelée Visualiseur de structure est disponible dans l’Éditeur de code Visual Studio. Elle affiche des lignes verticales entre les zones imbriquées du code, ce qui facilite l’affichage et la navigation dans le code. Elle est disponible pour tous les langages compatibles avec TextMate, ainsi que pour Visual C#, Visual Basic et XAML.

![Boîte de dialogue d’installation de Visual Studio 2017 RC](../ide/media/vsIDE-StructureVisualizer.png "Structure-Visualizer-in-VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>Bénéficiez d’une amélioration de la fonction Naviguer vers :
Nous avons amélioré la fonction Naviguer vers. Nous avons simplifié la fenêtre Naviguer vers et nous avons ajouté la prise en charge de caractères de filtre supplémentaires qui vous permettent d’affiner vos recherches dans le code.

#### <a name="create-apps-in-even-more-programming-languages"></a>Créez des applications dans davantage de langages de programmation :
Vous pouvez créer des applications dans Visual Studio à l’aide d’un plus grand nombre de langages de programmation (par rapport aux versions précédentes), et les solutions et projets ne sont plus obligatoires. Votre code bénéficie de la coloration syntaxique, de la saisie semi-automatique des instructions de base et, dans certains cas, de la prise en charge de Naviguer vers et d’autres fonctions. Si votre langage préféré n’est pas pris en charge, vous pouvez créer sa prise en charge à l’aide des grammaires TextMate.

### <a name="visual-c"></a>Visual C++
Visual Studio 2017 RC comprend un grand nombre de mises à jour et de correctifs de l’environnement Visual C++. Nous avons corrigé plus de 250 bogues et signalé des problèmes dans le compilateur et les outils, dont la plupart avaient été soumis par des clients via [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Nous avons également ajouté plusieurs améliorations, notamment la distribution des instructions de base C++ avec Visual Studio, la mise à jour du compilateur grâce à l’amélioration de la prise en charge des fonctionnalités C++&11; et C++, l’ajout et la mise à jour des fonctionnalités dans les bibliothèques C++, ainsi que l’amélioration des performances de l’IDE de C++, des charges de travail d’installation, et ainsi de suite.

Pour obtenir des détails complets, consultez notre page sur les [Nouveautés de Visual C++ dans Visual 2017 RC](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  


### <a name="debugging-and-diagnostics"></a>Débogage et diagnostics
Le débogage est désormais plus rapide et n’entraîne aucun retard lors de l’édition.

Par exemple : dans une version antérieure de Visual Studio, nous avons introduit ce que l’on appelle le processus d’hébergement pour les projets WPF, Windows Forms et Console gérée pour accélérer le débogage en exécutant un processus en arrière-plan afin de l’utiliser dans la session de débogage suivante. Cette fonctionnalité était bien intentionnée, mais Visual Studio cessait de répondre pendant quelques secondes quand vous arrêtiez le débogage ou utilisiez Visual Studio après la fin de la session de débogage.

Dans Visual Studio 2017, nous avons désactivé le processus d’hébergement et optimisé le débogage pour qu’il soit aussi rapide sans le processus d’hébergement, et même plus rapide pour les projets qui n’ont jamais utilisé le processus d’hébergement (tels que les projets ASP.NET, Windows universel et C++).

#### <a name="run-to-click"></a>Exécuter jusqu’au clic :
Désormais, pendant le débogage, vous pouvez cliquer sur l’icône en regard d’une ligne de code pour exécuter cette ligne. Vous n’êtes plus obligé de définir des points d’arrêt temporaires pour exécuter votre code en plusieurs étapes et d’arrêter l’exécution sur la ligne de votre choix.

![Déboguer Visual Studio 2017 RC - Exécuter jusqu’au clic](../ide/media/vs2017ide-RunToClick.png "Exécuter jusqu’au clic dans Visual Studio 2017 - Débogage et diagnostic")

#### <a name="the-new-exception-helper"></a>Nouvelle assistance d’exception :

Vous pouvez utiliser la nouvelle assistance d’exception pour afficher les informations liées aux exceptions dans une boîte de dialogue non modale compacte avec accès immédiat aux exceptions internes.

Trouvez rapidement ce qui était Null directement dans l’assistance de l’exception quand vous diagnostiquez une exception NullReferenceException.

Vous pouvez aussi exclure les arrêts sur des types d’exceptions levées pour des modules spécifiques en cochant la case pour ajouter une condition quand vous êtes arrêté au niveau d’une exception levée.

![Nouvelle boîte de dialogue d’assistance de l’exception](../ide/media/vs2017ide-ExceptionHelper.png "Nouvelle boîte de dialogue d’assistance de l’exception")

Pour plus d’informations, consultez le billet de blog sur l’[utilisation de la nouvelle assistance d’exception dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

## <a name="talk-to-us"></a>Nous contacter  
 Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C'est simple : nous prenons très au sérieux les commentaires de nos clients. Ils influencent bon nombre de nos décisions.  

Si vous souhaitez faire des suggestions sur la façon dont nous pouvons améliorer Visual Studio, ou signaler un problème, consultez la page [Nous contacter](../ide/talk-to-us.md).  

### <a name="report-a-problem"></a>Signaler un problème  
 Parfois, un message ne suffit pas pour transmettre l’impact complet du problème que vous avez rencontré. Si vous rencontrez un blocage, un incident ou autre problème de performances, vous pouvez facilement partager avec nous les étapes de reproduction et les fichiers de prise en charge (tels que des captures d’écran et des fichiers de trace et de vidage de tas) à l’aide de l’outil **Signaler un problème**. Pour plus d’informations sur l’utilisation de cet outil, consultez la page [Guide pratique pour signaler un problème](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Effectuer le suivi d'un problème dans Connect  
 Si vous voulez savoir où en est la prise en compte de vos commentaires sur Visual Studio, il vous suffit d’accéder à la page [Connect](http://connect.microsoft.com/), et d’y signaler le bogue. Après cela, vous pouvez revenir à Connect pour suivre l’état du bogue.  

## <a name="see-also"></a>Voir aussi  
* [Nouveautés de Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Nouveautés de C#](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [Nouveautés de Team Foundation Server](https://www.visualstudio.com/en-us/docs/whats-new)
* [Notes de mise à jour de Visual Studio](https://www.visualstudio.com/news/vs2015-vs)

