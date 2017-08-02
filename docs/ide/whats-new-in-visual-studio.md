---
title: "Nouveautés de Visual Studio 2017 │ Microsoft Docs"
ms.custom: 
ms.date: 04/06/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 28c6a166a423b3341ae32676830861eaa78cb40d
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Nouveautés dans Visual Studio 2017 RC
Une productivité inégalée pour l’ensemble des développements, applications et plateformes. Utilisez Visual Studio 2017 afin de développer des applications pour Android, iOS, Windows, le web et le Cloud. Écrivez votre code rapidement, déboguez et diagnostiquez facilement, testez souvent et publiez en toute confiance. Vous pouvez également étendre et personnaliser Visual Studio en créant vos propres extensions. Bénéficiez de la gestion de version et collaborez efficacement avec cette nouvelle version !

> [!NOTE]
> Pour obtenir une liste complète des nouvelles fonctions et fonctionnalités dans Visual Studio 2017, consultez les [Notes de mise à jour](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Voici un récapitulatif des modifications que nous avons apportées :

* **Performances et productivité**. Nous nous sommes concentrés non seulement sur les fonctionnalités de développement de bureau, de cloud et mobiles modernes, mais nous avons également amélioré l’acquisition globale, les performances et les expériences générales de productivité en matière de développement. Visual Studio démarre plus vite, est plus réactif et utilise moins de mémoire qu’auparavant.
* **Redéfinition des fondamentaux**. Une nouvelle expérience d’installation signifie que vous pouvez installer plus rapidement ce que vous voulez et quand vous en avez besoin. Visual Studio démarre plus rapidement, que vous souhaitiez charger des projets et des solutions de grande taille, ou travailler sur des dossiers de code, voire sur un seul fichier de code. Par ailleurs, Visual Studio vous permet de rester concentré sur la vue d’ensemble, en particulier pour les équipes adoptant DevOps.
* **Développement d’applications Cloud avec Azure**. Une suite intégrée d’outils Azure qui vous permettent de créer des applications prioritairement centrées sur le Cloud et alimentées par Microsoft Azure. Visual Studio vous permet de facilement configurer, générer, déboguer, packager et déployer des applications et services sur Azure.
* **Développement d’applications mobiles**. Dans Visual Studio 2017, vous pouvez innover et obtenir des résultats rapides grâce à Xamarin, qui unifie vos besoins mobiles multi-plateformes à l’aide d’une base de code et d’un ensemble de compétences essentiels. Favorisez la mobilité de vos équipes existantes, les investissements technologiques, et optez pour le code C# pour créer des expériences consommateur en avance et pour un budget inférieur. Accélérez chaque étape du cycle de vie mobile pour offrir des expériences consommateur de classe mondiale ou un portefeuille d’applications de productivité pour encourager la mobilité de votre personnel.

Voici des informations détaillées supplémentaires sur certains des changements les plus importants.

## <a name="performance-improvements"></a>Amélioration des performances

### <a name="a-new-setup-experience"></a>Une nouvelle expérience d'installation  
[Télécharger Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou [Vérifier la configuration système requise pour Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Visual Studio simplifie et accélère l’installation des fonctionnalités dont vous avez besoin, quand vous en avez besoin. Une désinstallation « propre » est également disponible.

 Le changement le plus important que vous constaterez lors de l’installation de Visual Studio est la nouvelle expérience proposée. Dans l’onglet **Charges de travail**, les options d’installation sont regroupées pour représenter les plateformes, les langages et les frameworks courants. Il couvre tout depuis le développement .NET Desktop au développement d’applications sur Windows, Linux et iOS.   

 ![Boîte de dialogue d’installation de Visual Studio 2017](~/install/media/vs2017-workloads.PNG "Écran d’installation de Visual Studio 2017")

Choisissez les charges de travail dont vous avez besoin et modifiez-les quand vous le souhaitez.

Vous voulez choisir vos propres composants au lieu d’utiliser des charges de travail ? Il vous suffit de sélectionner l’onglet **Composants individuels** du programme d’installation. Vous souhaitez installer des modules linguistiques sans avoir à modifier les options de langue de Windows ? Choisissez l’onglet **Modules linguistiques** du programme d’installation.  

Pour en savoir plus sur la nouvelle expérience d’installation, notamment pour obtenir des instructions pas à pas, consultez notre page [Installer Visual Studio](../install/install-visual-studio.md).

### <a name="start-visual-studio-faster"></a>Démarrer Visual Studio plus rapidement
Le nouveau Centre de performances Visual Studio peut vous aider à optimiser le temps de démarrage de votre IDE. Le Centre de performances répertorie toutes les extensions et les fenêtres d’outils susceptibles de ralentir le démarrage de l’IDE. Vous pouvez l’utiliser pour améliorer les performances de démarrage en déterminant quand les extensions démarrent, ou si les fenêtres d’outils sont ouvertes au démarrage.

### <a name="decrease-solution-load-time"></a>Accélérer la vitesse de chargement des solutions
Le fait de travailler sur des solutions qui contiennent de nombreux projets ne signifie pas que vous devez travailler avec tous les fichiers ou projets en même temps. Vous pouvez maintenant modifier et déboguer sans attendre que Visual Studio charge chaque projet. Pour essayer avec des projets managés, activez le **Chargement de solution allégé** à partir d’Outils-> Options-> Projets et solutions.

  ![Boîte de dialogue Options dans Visual Studio 2017](~/ide/media/vs2017ide-LightweightSolutionLoad.PNG "Boîte de dialogue Options dans Visual Studio 2017 - Chargement de solution allégé")

### <a name="faster-on-demand-loading-of-extensions"></a>Accélération du chargement des extensions à la demande
Visual Studio déplace ses extensions (et fonctionne également avec des extensions tierces) pour un chargement à la demande, plutôt qu’au démarrage de l’IDE. Vous êtes curieux de savoir quelles extensions ont un impact sur le démarrage, le chargement de solution et les performances de la frappe ? Vous pouvez afficher ces informations dans Aide -> Gérer le niveau de performance de Visual Studio.

  ![Boîte de dialogue Options dans Visual Studio 2017](~/ide/media/vs2017ide-manage-vs-perf.png "Boîte de dialogue Aide de Visual Studio - Gestion des performances")

## <a name="productivity-improvements"></a>Améliorations de la productivité

### <a name="sign-in-across-multiple-accounts"></a>Se connecter sur plusieurs comptes  
Nous avons introduit dans Visual Studio un nouveau service d’identité qui permet de partager des comptes d’utilisateur dans Team Explorer, Azure Tools, la publication dans le Windows Store, et bien plus encore.

Vous pouvez rester connecté plus longtemps également. Visual Studio ne vous demande pas de vous reconnecter toutes les 12 heures. Pour en savoir plus, consultez le billet de blog [Invites de connexion à Visual Studio moins nombreuses](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gérer vos extensions avec le Gestionnaire d’extensions itinérantes
Il est plus facile de configurer chaque environnement de développement avec vos extensions préférées quand vous vous connectez à Visual Studio. Le nouveau Gestionnaire d’extensions itinérantes effectue le suivi de toutes vos extensions préférées en créant une liste synchronisée dans le Cloud.  

Pour afficher une liste de vos extensions dans Visual Studio, cliquez sur Outils > Extensions et mises à jour, puis cliquez sur le Gestionnaire d’extensions itinérantes.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](~/ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 - Outils > Boîte de dialogue Extensions et mises à jour")

Le Gestionnaire d’extensions itinérantes effectue le suivi de toutes les extensions que vous installez, mais vous pouvez choisir celles que vous souhaitez ajouter à votre liste d’itinérance.

![Visual Studio 2017 - Boîte de dialogue Extensions et mises à jour](~/ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Outils > Gestionnaire d’extensions itinérantes")

Quand vous utilisez le Gestionnaire d’extensions itinérantes, trois types d’icônes figurent dans votre liste :
* ![Icône Itinérante](~/ide/media/vs2017ide-roamedicon.png "Icône Itinérante") ***Itinérante*** : extension qui fait partie de cette liste d’itinérances, mais qui n’est pas installée sur votre ordinateur.
  (Vous pouvez l’installer à l’aide du bouton **Télécharger**.)
* ![Icône Itinérante et installée](~/ide/media/vs2017ide-roamedinstalledicon.png "Icône Itinérante et installée") ***Itinérante et installée*** : toutes les extensions qui font partie de cette liste d’itinérances et qui sont installées dans votre environnement de développement.
  (Si vous décidez de ne pas les rendre itinérantes, vous pouvez les supprimer à l’aide du bouton **Arrêter l’itinérance**.)
* ![Icône Installée](~/ide/media/vs2017ide-installedicon.png "Icône Installée") ***Installée*** : toutes les extensions qui sont installées dans cet environnement, mais qui ne font pas partie de votre liste d’itinérances.
  (Vous pouvez ajouter des extensions à la liste d’itinérances à l’aide du bouton **Démarrer l’itinérance**.)

Toute extension que vous téléchargez quand vous êtes connecté est ajoutée à votre liste comme **Itinérante et installée**, et fait donc partie de votre liste d’itinérances, ce qui vous permet d’y accéder à partir de n’importe quel ordinateur.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Bénéficier de la validation de la dépendance d’architecture en direct et des tests unitaires en direct

Visual Studio peut maintenant vous informer en temps réel des violations de règle de dépendances architecturales à mesure que vous tapez du code dans l’Éditeur de code grâce aux diagrammes de validation des dépendances (ou diagrammes de couche).

Les erreurs apparaissent dans la liste des erreurs et des tildes dans l’éditeur de texte indiquent l’emplacement précis de cette violation. Vous êtes maintenant moins susceptible d’introduire des dépendances indésirables.

![Validation de l’architecture en direct](~/ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Validation des dépendances de l’architecture en direct")

#### <a name="live-unit-testing"></a>Tests unitaires en direct :

Dans Visual Studio Enterprise 2017, les tests unitaires en direct offrent des résultats de tests unitaires et une couverture du code dans l’éditeur lorsque vous rédigez du code. Cela fonctionne avec les projets C# et Visual Basic pour le .NET Framework et prend en charge trois frameworks de test : MSTest, xUnit et NUnit.

![Tests unitaires en direct](~/ide/media/lut-codewindow.png "Un exemple de notre nouvelle fonctionnalité Tests unitaires en direct de l’édition Enterprise de Visual Studio")

Pour plus d’informations, consultez le billet de blog [Live Unit Testing in Visual Studio 2017 Enterprise](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/).

### <a name="devops"></a>DevOps
#### <a name="redgate-data-tools"></a>Redgate Data Tools :
Pour étendre les fonctionnalités DevOps au développement de base de données SQL Server, les outils Redgate Data Tools sont désormais disponibles dans les éditions suivantes de Visual Studio 2017.

Inclus avec Visual Studio Enterprise 2017 :
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) vous permet de développer des scripts de migration, de gérer les modifications de base de données à l’aide du contrôle de code source et d’automatiser en toute sécurité des déploiements de modifications de base de données en même temps que les modifications des applications.
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) vous permet d’écrire du code SQL plus rapidement et avec une plus grande précision grâce à la complétion de code intelligente. SQL Prompt complète automatiquement les objets et les mots clés de la base de données et du système, et propose des suggestions de colonne au fil de votre frappe. Cela aboutit à un code plus propre et à moins d’erreurs, car vous n’avez pas à vous souvenir de chaque nom de colonne ni de chaque alias.

Inclus avec toutes les éditions de Visual Studio 2017 :
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) augmente votre productivité en vous aidant à trouver rapidement des objets et des fragments SQL parmi plusieurs bases de données.

Pour en savoir plus, consultez notre billet de blog [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="visual-studio-ide-enhancements"></a>Améliorations de l’environnement de développement intégré (IDE) de Visual Studio
#### <a name="interact-with-git"></a>Interagissez avec Git :
Lorsque vous travaillez avec un projet dans Visual Studio, vous pouvez installer et rapidement valider et publier votre code sur un service Git. Vous pouvez également gérer vos référentiels Git en cliquant dans les menus à partir des boutons situés en bas à droite de l’IDE.

![Visual Studio 2017 interagit avec la boîte de dialogue Git](~/ide/media/vsIDE-GitInteraction.png "Outils Git dans l’IDE de Visual Studio")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Afficher et parcourir le code avec le Visualiseur de structure :
Le Visualiseur de structure dessine des lignes de repère de structure (ou guides de mise en retrait) dans votre code. Vous pouvez les utiliser pour visualiser et distinguer le bloc de code dans lequel vous vous trouvez à tout moment sans avoir à faire défiler le code. Survolez les lignes pour afficher les info-bulles qui vous permettent de voir l’ouverture de ce bloc et de ses parents. Il est disponible dans tous les langages pris en charge via les syntaxes TextMate, ainsi que C#, Visual Basic et XAML.

![Visualiseur de structure Visual Studio 2017](~/ide/media/vsIDE-StructureVisualizer.png "Visualiseur de Structure dans Visual Studio")

#### <a name="experience-improved-navigation-controls"></a>Amélioration des commandes de navigation :
Nous avons actualisé l’expérience de navigation pour permettre le déplacement d’un point A vers un point B de manière plus fiable et directe.

* **Atteindre** (Ctrl + F12) &ndash; accède depuis n’importe quel type ou membre de base à ses diverses implémentations.

* **Atteindre** (Ctrl + T ou Ctrl +,) &ndash; accède directement à toute déclaration de fichier/type/membre/symbole. Vous pouvez filtrer votre liste de résultats ou utiliser la syntaxe de requête (par exemple, « f searchTerm » pour les fichiers, « t searchTerm » pour les types, etc.).

 ![Amélioration de Atteindre tout](~/ide/media/vs2017ide-navigation-go-to.png "Exemple de la fonctionnalité Atteindre tout améliorée")

* **Rechercher toutes les références (Maj + F12)** &ndash; grâce à la colorisation de syntaxe, vous pouvez regrouper les résultats obtenus via la fonctionnalité Rechercher toutes les références par une combinaison de projets, de définitions et de chemins. Vous pouvez également « verrouiller » les résultats afin de pouvoir continuer à rechercher d’autres références sans perdre les résultats d’origine.

 ![Nouvel outil Rechercher toutes les références](~/ide/media/vs2017ide-find-all-references.png "Exemple du nouvel outil Rechercher toutes les références")

* **Guides de mise en retrait** &ndash; lignes verticales grises en pointillé, qui agissent comme des repères dans le code pour fournir du contexte dans le cadre de la vue. Vous les avez peut-être déjà rencontrés dans le logiciel connu Productivity Power Tools.

Pour plus d’informations sur nos nouvelles fonctionnalités de productivité, consultez le billet de blog [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) (Productivité dans Visual Studio 2017) par Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++
Nous avons également ajouté plusieurs améliorations à Visual Studio, notamment la distribution des instructions de base C++ avec Visual Studio, la mise à jour du compilateur grâce à l’amélioration de la prise en charge des fonctionnalités C++ 11 et C++, ainsi que l’ajout et la mise à jour des fonctionnalités dans les bibliothèques C++. Nous avons également amélioré les performances de l’IDE de C++, les charges de travail d’installation et bien plus encore.

Par ailleurs, nous avons corrigé plus de 250 bogues et signalé des problèmes dans le compilateur et les outils, dont la plupart avaient été soumis par des clients via [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Pour obtenir des détails complets, consultez notre page sur les [Nouveautés de Visual C++ dans Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  

### <a name="debugging-and-diagnostics"></a>Débogage et diagnostics

#### <a name="run-to-click"></a>Exécuter jusqu’au clic :

Maintenant, vous pouvez plus facilement avancer pendant le débogage sans avoir à définir un point d’arrêt sur la ligne souhaitée. Lorsque vous êtes arrêté dans l’outil de débogage, il suffit de cliquer sur l’icône qui apparaît en regard de la ligne de code survolée par votre souris. Votre code sera exécuté jusqu’à cette ligne la prochaine fois qu’il sera atteint dans votre chemin de code.

![Déboguer Visual Studio 2017 - Exécuter jusqu’au clic](~/ide/media/vs2017ide-RunToClick.png "Exécuter jusqu’au clic dans Visual Studio - Débogage et diagnostic")

#### <a name="the-new-exception-helper"></a>Nouvelle assistance d’exception :

La nouvelle assistance d’exception vous permet de visualiser les informations d’exception d’un coup d’œil. Les informations sont présentées de manière compacte avec un accès instantané aux exceptions internes. Trouvez rapidement ce qui était Null directement dans l’assistance de l’exception quand vous diagnostiquez une exception NullReferenceException.

![Boîte de dialogue de la nouvelle assistance d’exception dans Visual Studio](~/ide/media/vs2017ide-ExceptionHelper.png "Boîte de dialogue de la nouvelle assistance d’exception")

Pour plus d’informations, consultez le billet de blog sur l’[utilisation de la nouvelle assistance d’exception dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

## <a name="talk-to-us"></a>Nous contacter  
 Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C'est simple : nous prenons très au sérieux les commentaires de nos clients. Ils influencent bon nombre de nos décisions.  

Si vous souhaitez faire des suggestions sur la façon dont nous pouvons améliorer Visual Studio, ou signaler un problème, consultez la page [Nous contacter](../ide/talk-to-us.md).  

### <a name="report-a-problem"></a>Signaler un problème  
 Parfois, un message ne suffit pas pour transmettre l’impact complet du problème que vous avez rencontré. Si vous rencontrez un blocage, un incident ou autre problème de performances, vous pouvez facilement partager avec nous les étapes de reproduction et les fichiers de prise en charge (tels que des captures d’écran et des fichiers de trace et de vidage de tas) à l’aide de l’outil **Signaler un problème**. Pour plus d’informations sur l’utilisation de cet outil, consultez la page [Guide pratique pour signaler un problème](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Effectuer le suivi d'un problème dans Connect  
 Si vous voulez savoir où en est la prise en compte de vos commentaires sur Visual Studio, il vous suffit d’accéder à la page [Connect](http://connect.microsoft.com/) et d’y signaler le bogue. Après cela, vous pouvez revenir à Connect pour suivre l’état du bogue.  

## <a name="see-also"></a>Voir aussi  
* [Nouveautés de Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Nouveautés de C#](https://docs.microsoft.com/en-us/dotnet/csharp/csharp-7)  
* [Nouveautés de Team Foundation Server](https://www.visualstudio.com/en-us/docs/whats-new)
* [Notes de mise à jour de Visual Studio](https://www.visualstudio.com/news/vs2015-vs)

