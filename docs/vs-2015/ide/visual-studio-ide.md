---
title: Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 76e1d9c4a7cbfdfc2a7011668eb58a5ea9741d3d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780677"
---
# <a name="visual-studio-ide"></a>Environnement IDE de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 est une suite d'outils permettant de créer des logiciels, qui couvre la phase de planification, la conception de l'interface utilisateur, par le codage, le test, le débogage, l'analyse de la qualité et de la performance du code, le déploiement sur les clients et la collecte de la télémétrie sur l'utilisation. Ces outils sont conçus pour fonctionner ensemble avec la meilleure intégration possible et sont tous exposés via l'environnement de développement intégré (IDE) de Visual Studio.

Vous pouvez utiliser Visual Studio pour créer de nombreux types d'applications, que ce soit des applications commerciales simples et des jeux pour clients mobiles ou des grands systèmes complexes destinés aux entreprises et aux centres de données. Vous pouvez créer :

- Des applications et des jeux qui fonctionnent non seulement sur Windows, mais également sur Android et iOS.

- Des sites web et des services web basés sur ASP.NET, JQuery, AngularJS et d’autres frameworks répandus.

- Des applications pour des plateformes et des appareils variés (Azure, Office, SharePoint, Hololens, Kinect et Internet des objets), pour n’en citer que quelques-uns.

- Des jeux et des applications graphiques pour différents appareils Windows, notamment la Xbox, utilisant DirectX.

Visual Studio prend en charge par défaut C#, C et C++, JavaScript, F# et Visual Basic. Visual Studio fonctionne avec et s’intègre parfaitement aux applications tierces comme Unity via l’extension [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) et à Apache Cordova via [Visual Studio Tools pour Apache Cordova](http://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Vous pouvez étendre Visual Studio vous-même en créant des outils personnalisés qui effectuent des tâches spécialisées.

Si vous n’avez jamais utilisé Visual Studio, découvrez les principes de base avec nos didacticiels et procédures pas à pas [Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md) .

Si vous souhaitez savoir sur les nouvelles fonctionnalités dans Visual Studio 2015, consultez [What ' s New in Visual Studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Installation de Visual Studio
 Vous pouvez déterminer quelle édition de Visual Studio vous convient en consultant la rubrique [Éditions Visual Studio](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Vous pouvez installer Visual Studio 2015 en le téléchargeant à partir de [Téléchargements Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Si vous voulez en savoir plus sur le processus d’installation, consultez [Installation de Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Principes de base de l'IDE
 L'illustration suivante montre l'IDE Visual Studio avec un projet ouvert, la fenêtre de l'Explorateur de solutions, qui permet de naviguer dans les fichiers du projet, et la fenêtre Team Explorer, qui permet de naviguer dans le contrôle des sources et le suivi des éléments de travail. Les fonctionnalités de la barre de titre figurant avec une légende sont expliquées ci-dessous plus en détail.

 ![IDE de Visual Studio](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Connexion
 Quand vous démarrez Visual Studio pour la première fois, vous pouvez vous connecter avec votre compte Microsoft, ou avec votre compte professionnel ou celui de votre établissement scolaire. Le fait d’être connecté vous permet de synchroniser vos paramètres, comme les dispositions des fenêtres, entre plusieurs appareils et de vous connecter automatiquement aux services dont vous pouvez avoir besoin, comme des abonnements Azure et Visual Studio Team Services. Si vous avez une licence d'abonnement, vous devez vous connecter à Visual Studio régulièrement pour maintenir votre jeton de licence actualisé. Si vous avez une licence de clé de produit, vous ne devez pas vous connecter, mais le faire facilite votre connexion à Visual Studio Team Services et à vos comptes avec Azure, Office 365 et Salesforce.com. Pour plus d’informations, consultez [Connexion à Visual Studio](../ide/signing-in-to-visual-studio.md).

 Si vous avez plusieurs comptes Visual Studio Team Services, plusieurs comptes Azure ou plusieurs abonnements MSDN, vous pouvez les lier et accéder ainsi aux ressources et aux services de tous vos comptes avec une seule connexion. Pour plus d'informations, consultez [Work with multiple user accounts](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Maintien du produit à jour
 L'icône de notification dans le coin supérieur droit de la barre de titre vous indique quand des mises à jour sont disponibles pour Visual Studio ou pour des composants associés que vous avez installés. Vous pouvez choisir d'ignorer ou de prendre en compte ces notifications. Pour plus d'informations, consultez [Notifications de Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Recherche d'éléments et obtention d'aide
 La fenêtre [Lancement rapide](../ide/reference/quick-launch-environment-options-dialog-box.md) présentée ci-dessous est un moyen rapide de rechercher des commandes, des outils, des fonctionnalités, etc., de Visual Studio quand vous ne connaissez pas le raccourci clavier ou l'emplacement du menu. Tapez simplement ce que vous recherchez et la fenêtre Lancement rapide vous donne un lien vers ce que vous cherchez.

 ![Résultats du lancement rapide pour « nouveau projet »](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN est le site web de Microsoft pour la documentation technique ; vous lisez en ce moment même cette page sur le site MSDN ! Dans Visual Studio, vous pouvez appuyer sur **F1** pour accéder à la page d'aide MSDN pour la fenêtre active. Vous pouvez également appuyer sur **F1** dans l'éditeur de code pour accéder à la page d'aide MSDN pour l'API ou le mot clé à la position actuelle du point d'insertion. Par exemple, dans un fichier C#, placez le signe insertion quelque part dans une déclaration `System.String` ou juste après celle-ci, et appuyez sur **F1** pour accéder à la page d’aide MSDN pour <xref:System.String>.

### <a name="giving-feedback"></a>Commentaires
 Il est facile de nous envoyer des commentaires sur Visual Studio quand vous le souhaitez. Cliquez sur l’icône de commentaires dans la barre de titre en regard de **Lancement rapide** , puis cliquez sur **Signaler un problème** ou **Faire une suggestion**. Les versions préliminaires de Visual Studio disposent également d’une option **Évaluer ce produit** . Nous examinons tous ces commentaires et nous les utilisons pour améliorer le produit. Pour plus d'informations, consultez [Talk to Us](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Personnalisation de l'IDE
 Vous pouvez personnaliser la disposition des fenêtres en fonction de votre style de développement. Vous pouvez ancrer, détacher ou masquer n'importe quelle fenêtre à tout moment, et vous pouvez aussi exécuter l'éditeur en mode plein écran. Vous pouvez créer et enregistrer plusieurs dispositions de fenêtres personnalisées, qui montrent seulement les fenêtres dont vous avez besoin pour des contextes spécifiques. Par exemple, vous pouvez créer une disposition en plein écran pour ne voir que l'éditeur de code. Vous pouvez aussi créer des dispositions différentes pour le débogage et pour les opérations en équipe. Pour plus d’informations, consultez [Personnalisation des dispositions de fenêtres](../ide/customizing-window-layouts-in-visual-studio.md).

 Vous pouvez personnaliser Visual Studio de beaucoup d'autres façons et retrouver votre paramétrage ailleurs si vous travaillez sur plusieurs ordinateurs. Pour plus d'informations, consultez [Personnalisation de l'IDE](../ide/personalizing-the-visual-studio-ide.md).

 Il existe des raccourcis clavier pour presque tout, que vous pouvez également personnaliser. Pour créer des raccourcis, tapez « Clavier » dans la zone Lancement rapide pour ouvrir la boîte de dialogue Clavier. Dans cette boîte de dialogue, vous pouvez appuyer sur F1 pour accéder à la page d'aide MSDN si vous avez besoin de plus d'informations sur les options. Pour plus d'informations, consultez [Raccourcis clavier par défaut dans Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Connexion à Visual Studio Team Services et à Team Foundation Server
 Visual Studio Team Services (VSTS) est un service basé sur le cloud destiné à héberger des projets de logiciels et à permettre la collaboration dans des équipes. VSTS prend en charge les systèmes de contrôle de code source Git et Team Foundation, ainsi que les méthodologies de développement Scrum, CMMI et Agile. La gestion de version Team Foundation (TFVC) utilise un dépôt de serveur unique et centralisé pour effectuer le suivi et la gestion des versions des fichiers. Les modifications locales sont toujours archivées sur le serveur central, où les autres développeurs peuvent obtenir les dernières modifications. Team Foundation Server (TFS) 2015 est le hub de gestion du cycle de vie des applications pour Visual Studio. Il permet à toutes personnes impliquées dans le processus de développement de participer à une même solution. TFS est également utile pour la gestion des équipes et des projets hétérogènes.

 Si vous avez un compte Visual Studio Team Services ou Team Foundation Server sur votre réseau, vous vous y connectez via la fenêtre Team Explorer. Depuis cette fenêtre, vous pouvez vérifier le code dans ou en dehors du contrôle de code source, gérer des éléments de travail, démarrer des builds et accéder aux salles d'équipe et aux espaces de travail. Vous pouvez ouvrir Team Explorer depuis **lancement rapide** ou dans le menu principal à partir de **vue &#124; Team Explorer** ou à partir de **équipe &#124; gérer les connexions**.  Pour plus d’informations sur Visual Studio Team Services, consultez [www.visualstudio.com](https://www.visualstudio.com/). Pour plus d’informations sur Team Foundation Server, consultez [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 L’illustration suivante montre le volet Team Explorer pour une solution qui est hébergée dans VSTS :

 ![Visual Studio Team Explorer](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Création de solutions et de projets
 Même si vous pouvez utiliser Visual Studio pour parcourir les fichiers de code individuels, le plus souvent, vous travaillerez dans un *projet*. Un projet Visual Studio est une collection de fichiers et de ressources qui sont compilés en un seul fichier exécutable binaire pour des applications (par exemple un fichier .exe, DLL ou appx). Pour les sites web non-ASP.NET, aucun fichier exécutable n'est généré, et le projet contient seulement du code HTML, des fichiers JavaScript et des images. Comme vous devrez parfois créer plusieurs fichiers binaires ou plusieurs sites web qui sont étroitement liés, Visual Studio propose le concept de solution, qui peut contenir plusieurs projets ou sites web. Quand vous créez un projet, vous créez en fait un « projet dans une solution » et vous pouvez, si nécessaire, ajouter ultérieurement des projets à cette solution. Par exemple, si vous avez un projet de DLL, vous pouvez ajouter un projet .exe à la solution, qui charge et utilise la DLL.

 Un *modèle de projet* est une collection de fichiers de code prédéfinis et de paramètres de configuration qui vous permettent de créer rapidement un type spécifique d'application. Visual Studio est fourni avec de nombreux modèles de projet et, si aucun des modèles par défaut ne vous convient, vous pouvez créer vos propres modèles. Après avoir créé un projet avec un modèle, vous pouvez commencer à y écrire votre propre code, dans les fichiers fournis ou dans des fichiers que vous ajoutez. Pour plus d’informations, consultez [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md). L'illustration suivante montre la boîte de dialogue Nouveau projet, avec les modèles de projet disponibles pour les applications ASP.NET.

 ![Visual Studio de boîte de dialogue Nouveau projet](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Conception de l'interface utilisateur
 Un concepteur est un outil intuitif qui vous permet de créer une interface utilisateur sans écrire de code. Vous pouvez faire glisser des contrôles d’interface utilisateur, comme des zones de liste, des calendriers et des boutons depuis la fenêtre [Toolbox](../ide/reference/toolbox.md) sur une surface de conception qui représente la fenêtre ou la boîte de dialogue. Vous pouvez redimensionner et réorganiser les éléments sans écrire de code. Les concepteurs sont inclus pour tous les types de projets ayant une interface utilisateur.

 Si votre projet a une interface utilisateur basée sur XAML, le concepteur par défaut est Blend pour Visual Studio. Il s'agit d'un outil graphique sophistiqué qui fonctionne dans une parfaite intégration avec Visual Studio.

 ![Artboard](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Mode Conception** Affiche la conception visuelle de votre document. Dans cette vue, tracez ou modifiez des objets sur l'aire de conception.|
|![](../designers/media/b1-2.png "B1_2")|**Fil d'Ariane** Déplacez-vous rapidement entre le mode de modification des modèles, le mode modification des styles et l'étendue de modification des objets d'un objet sélectionné.|
|![](../designers/media/b1-3.png "B1_3")|**Zoom** Permet de zoomer sur l'aire de conception ou les objets sur l'aire de conception.|
|![](../designers/media/b1-4.png "B1_4")|**Contrôles de l'aire de conception** Utilisez ces contrôles (**Afficher la grille d'accrochage**, **Aligner sur le quadrillage** et **Activer/Désactiver l'alignement sur les lignes d'alignement**) pour définir les options d'alignement. L'alignement est utile pour caler des objets les uns sur les autres ou sur des lignes régulièrement espacées sur l'aire de conception.|
|![](../designers/media/b1-5.png "B1_5")|**Éditeur de code** Modifie manuellement le code XAML, C#, C++ ou Visual Basic dans l'Éditeur de code.|

 Pour plus d’informations, consultez [XAML de conception dans Visual Studio et Blend pour Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Écriture, navigation et compréhension du code
 Si vous êtes développeur, la fenêtre de l'éditeur est l'endroit où vous passerez probablement le plus de temps. Visual Studio comprend des éditeurs pour C#, C++, Visual Basic, JavaScript, XML, HTML, CSS et F#, tandis que des tiers offrent des éditeurs (et des compilateurs) sous forme de plug-ins pour de nombreux autres langages.

 Vous pouvez modifier des fichiers individuels dans l’éditeur de texte en cliquant sur **fichier &#124; Open &#124; fichier.** . Pour modifier des fichiers dans un projet ouvert, cliquez sur le nom du fichier dans l'Explorateur de solutions. Le code est colorisé, et vous pouvez personnaliser le jeu de couleurs en tapant « Couleurs » dans la zone de lancement rapide. Vous pouvez avoir un grand nombre de fenêtres d'éditeur de texte ouvertes en même temps sous forme d'onglets. Vous pouvez fractionner chaque fenêtre indépendamment. Vous pouvez également exécuter l'éditeur de texte en mode plein écran.

 ![GreetingsConsoleApp.cpp dans l’éditeur de code](../ide/media/c-ide-editorlinenumberswordwrapon.png "IDE_EditorLineNumbersWordWrapOn C ++")

 L'éditeur de texte est très interactif (si vous voulez qu'il le soit) et offre de nombreuses fonctionnalités de productivité qui vous aident à écrire du code plus vite et mieux. Les fonctionnalités varient selon le langage, et leur utilisation n'est pas obligatoire (tapez « Éditeur » dans la zone Lancement rapide) pour activer ou désactiver les fonctionnalités. Voici quelques-unes des fonctionnalités de productivité courantes :

1. La[Refactoring](../ide/refactoring-in-visual-studio.md) inclut des opérations comme le renommage intelligent des variables, le déplacement de lignes de code sélectionnées dans une fonction distincte, le déplacement de code à d’autres endroits, la réorganisation des paramètres des fonctions, etc.

2. *IntelliSense* est un terme couvrant un ensemble de fonctionnalités appréciées qui affichent des informations sur les types concernant votre code directement dans l'éditeur et qui, dans certains cas, écrivent de petits extraits de code pour vous. Cela revient à avoir de la documentation de base incluse dans l'éditeur, ce qui vous évite d'avoir à rechercher des informations sur les types dans une fenêtre d'aide distincte. Les fonctionnalités d'IntelliSense varient selon le langage. Pour plus d’informations, consultez [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ Intellisense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Options IntelliSense propres à Visual Basic](../ide/visual-basic-specific-intellisense.md). L’illustration suivante montre certaines fonctionnalités IntelliSense à l'œuvre :

    ![Liste des membres Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. Les**tildes** vous signalent des erreurs ou des problèmes potentiels dans votre code en temps réel au fil de votre saisie, ce qui vous permet de les corriger immédiatement sans attendre que l'erreur soit découverte au moment de la compilation ou de l'exécution. Si vous pointez sur le tilde, vous voyez des informations supplémentaires sur l'erreur. Une icône d'ampoule peut également apparaître dans la marge gauche, avec des suggestions pour corriger l'erreur. Pour plus d'informations, consultez [Perform quick actions with light bulbs](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Ampoule avec pointage de la souris](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. Les [signets](../ide/setting-bookmarks-in-code.md) vous permettent d'accéder rapidement à des lignes spécifiques dans les fichiers sur lesquels vous travaillez activement.

5. Vous pouvez appeler la fenêtre [Call Hierarchy](../ide/reference/call-hierarchy.md) dans le menu contextuel de l’éditeur de texte pour afficher les méthodes qui appellent la méthode sous le signe insertion et qui sont appelées par cette méthode.

6. **CodeLens** vous permet de rechercher les références et les modifications apportées à votre code, les bogues liés, les éléments de travail, les révisions de code et les tests unitaires, tout cela sans quitter l'éditeur. Pour plus d’informations, consultez [Rechercher les modifications du code et d’autres éléments de l’historique](../ide/find-code-changes-and-other-history-with-codelens.md).

7. La fenêtre **Aperçu de la définition** montre une définition de méthode ou de type inline, sans vous obliger à quitter votre contexte actuel. Cette fenêtre fonctionne désormais également pour XAML.

8. L'option de menu contextuel **Atteindre la définition** vous amène directement à l'endroit où la fonction ou l'objet est défini. D'autres commandes de navigation sont également disponibles en cliquant avec le bouton droit dans l'éditeur.

9. Un outil connexe, l'[Explorateur d'objets](http://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), vous permet d'examiner les assemblys .NET ou Windows Runtime sur votre système, pour voir les types qu'ils contiennent ainsi que les méthodes et les propriétés que ces types contiennent.

     ![Explorateur d’objets montrant le composant System.Timer](../ide/media/objectbrowser.png "ObjectBrowser")

   La plupart des éléments du menu Edition et du menu Affichage se rapportent d'une façon ou d'une autre à l'éditeur de code. Pour plus d’informations sur l’éditeur, consultez [Écriture de code](../ide/writing-code-in-the-code-and-text-editor.md) et [Modification de votre code](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Compilation et génération de votre code

La génération d'un projet consiste à compiler le code source et à effectuer les étapes nécessaires pour produire l'exécutable. Les opérations de génération varient selon les langages, et les sites web standard n'ont pas de génération du tout. Quel que soit le type de projet, le menu Générer est l'emplacement standard pour ces commandes. Pour compiler et exécuter votre code avec une seule frappe au clavier, appuyez sur F5. Chaque compilateur est entièrement configurable via l'IDE. La barre d'outils Générer vous permet de spécifier s'il faut générer une version de débogage de votre programme, avec des symboles et une vérification des erreurs supplémentaire activée pour la prise en charge des points d'arrêt et le pas à pas dans le débogueur, ou bien une version Release, que vous livrerez au final aux clients. Vous pouvez configurer davantage de paramètres de génération, ainsi que de nombreux autres paramètres sur la page des propriétés pour un projet. Cliquez avec le bouton droit sur le nœud du projet dans l'Explorateur de solutions, puis choisissez Propriétés. Vous pouvez également effectuer des générations à partir de la ligne de commande.

La sortie de la génération, incluant des messages d’erreur ou de réussite, apparaît dans la fenêtre **Sortie**. Le **liste d’erreurs** présente des informations détaillées sur les erreurs de build.

## <a name="debugging-your-code"></a>Débogage de votre code
 Le débogueur de pointe de Visual Studio vous permet de déboguer du code en cours d'exécution dans votre projet local, sur un appareil distant ou sur un émulateur, comme ceux destinés à Android ou Windows Phone. Vous pouvez parcourir le code instruction par instruction et examiner les variables au fil de la progression, vous pouvez avancer pas à pas dans des applications multithread, et vous pouvez définir des points d'arrêt qui sont atteints seulement quand une condition spécifiée est vraie. Tout ceci peut être configuré dans l'éditeur de code lui-même, ce qui vous permet de ne pas quitter le contexte de votre code.

 ![Fenêtre d’aperçu de paramètres de point d’arrêt](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Le débogueur lui-même comprend plusieurs fenêtres qui vous permettent d'afficher et de manipuler des variables locales, la pile des appels et d'autres aspects de l'environnement d'exécution. Vous pouvez trouver ces fenêtres dans le menu **Débogage** .

 La [Immediate Window](../ide/reference/immediate-window.md) vous permet de taper une expression et de voir son résultat immédiatement.

 La fenêtre [IntelliTrace](http://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) enregistre chaque appel de méthode et d'autres événements dans un programme .NET en cours d'exécution et peut vous aider à localiser rapidement l'origine d'un problème.

 Pour plus d'informations, consultez [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Test de votre code
 Visual Studio inclut une infrastructure de test unitaire pour le code managé (.NET) et une pour le C++ natif. Pour créer des tests unitaires, ajoutez simplement un projet de test à votre solution, écrivez vos tests, puis exécutez-les à partir de la fenêtre Explorateur de tests. Pour plus d’informations, consultez [Tests unitaires sur votre code](../test/unit-test-your-code.md).

 ![Explorateur de tests unitaires](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analyse de la qualité et des performances du code
 Visual Studio inclut des outils puissants pour l'analyse statique et à l'exécution. Les outils d'analyse statique vous aident à identifier les erreurs potentielles dans la conception, la globalisation, l'interopérabilité, la performance, la sécurité et d'autres catégories. Les tests de performance, ou de profilage, mesurent la façon dont votre programme s'exécute. Vous accédez à ces outils à partir du menu **Analyse** . Pour plus d'informations, consultez [Amélioration de la qualité avec les outils de diagnostic de Visual Studio](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Connexion à des services cloud et à des bases de données
 La fenêtre [Explorateur de serveurs](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) de Visual Studio montre les ressources de tous les comptes gérés sous votre compte de personnalisation (celui avec lequel vous vous êtes connecté), y compris des instances SQL Server, Azure, Salesforce.com, Office 365 et des sites web.

 ![Explorateur de serveurs](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio inclut [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT) qui vous permet de générer, déboguer, maintenir et refactoriser des bases de données. Vous pouvez travailler avec un projet de base de données, ou directement avec une instance de base de données connectée, locale ou hors site.

 L'Explorateur d'objets SQL Server de Visual Studio offre une vue des objets de base de données similaire à celle de SQL Server Management Studio. L'Explorateur d'objets SQL Server vous permet d'effectuer des tâches simples d'administration et de conception de base de données, y compris la modification des données des tables, la comparaison de schémas et l'exécution de requêtes à l'aide de menus contextuels directement depuis l'Explorateur d'objets SQL Server. SSDT inclut également des types de projets spéciaux et des outils de développement de solutions SQL Server 2012 Analysis Services, Reporting Services et Integration Services Business Intelligence (anciennement appelé Business Intelligence Development Studio).

 ![Explorateur d’objets SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Déploiement de votre application terminée
 Quand votre application est prête à être déployée auprès des clients, Visual Studio fournit les outils nécessaires, qu'elle soit déployée dans le Windows Store, sur un site SharePoint ou à l'aide des technologies InstallShield ou Windows Installer. Ils sont tous accessibles via l'IDE. Pour plus d'informations, consultez [Déploiement d'applications, de services et de composants](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Outils d'architecture et de modélisation (version Enterprise uniquement)
 Vous pouvez utiliser les outils d'architecture et de modélisation de Visual Studio pour concevoir et modéliser votre application. Ces outils vous aident à visualiser la structure, le comportement et les relations du code. Vous pouvez créer des modèles à différents niveaux de détails tout au long du cycle de vie d'application dans le cadre de votre processus de développement. Vous pouvez suivre les spécifications, les tâches, les cas de test, les bogues et les autres travaux associés à vos modèles, en liant des éléments de modèle aux éléments de travail de Team Foundation Server et de votre plan de développement. Pour plus d'informations, consultez [Concevoir et modéliser votre application](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Extension de Visual Studio via le Kit de développement logiciel (SDK) Visual Studio
 Visual Studio est une plateforme extensible. Une extension de Visual Studio est un outil personnalisé qui s'intègre à l'IDE. Vous pouvez ajouter des extensions de tiers ou créer les vôtres. Pour plus d'informations, consultez [Développement d'extensions Visual Studio](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 Les [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) constituent une référence essentielle pour ceux qui écrivent des extensions pour Visual Studio. Ces recommandations spécifiques à une plateforme comprennent des informations sur la conception des boîtes de dialogue, sur les polices, les couleurs, les icônes, les contrôles communs et sur d'autres modèles d'interaction, qui permettront à votre nouvelle fonctionnalité de s'intégrer sans problème à Visual Studio.

## <a name="in-this-guide"></a>Dans ce guide

|||
|-|-|
|[Comptes d’utilisateur et mises à jour](../ide/user-accounts-and-updates.md)|[Personnalisation de l’IDE](../ide/personalizing-the-visual-studio-ide.md)|
|[Guide pratique pour se déplacer dans l’IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md)|
|[Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|[Projets et solutions](../ide/solutions-and-projects-in-visual-studio.md)|
|[Écriture de code](../ide/writing-code-in-the-code-and-text-editor.md)|[Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)|
|[Outils de profilage](../profiling/profiling-tools.md)|[Améliorer la qualité du code](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Conception des interfaces utilisateur](../designers/designing-user-interfaces.md)|[Analyse et modélisation de l’architecture](../modeling/analyze-and-model-your-architecture.md)|
|[Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)|[Déploiement d’applications, de services et de composants](../deployment/deploying-applications-services-and-components.md)|
|[Prise en charge de l’IDE de Visual Studio 64 bits](../ide/visual-studio-ide-64-bit-support.md)|[Sécurité](../ide/security-in-visual-studio.md)|
|[Exemples Visual Studio](../ide/visual-studio-samples.md)|[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)|
|[Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)|[Informations de référence sur l’interface utilisateur](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Voir aussi

- [Installation de Visual Studio 2015](../install/install-visual-studio-2015.md)
- [Modification de votre code](https://www.visualstudio.com/features/ide-vs)
- [Nouveautés dans Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)
- [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Nous contacter](../ide/talk-to-us.md)