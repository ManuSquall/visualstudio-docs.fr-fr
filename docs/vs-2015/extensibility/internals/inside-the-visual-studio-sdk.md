---
title: Dans le kit de développement logiciel (SDK) Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3bdc65a145b64071087d72fce9967c67cc2f8426
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687535"
---
# <a name="inside-the-visual-studio-sdk"></a>Dans le kit SDK Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette section fournit des informations détaillées sur les extensions Visual Studio, y compris l’architecture de Visual Studio, les composants, les services, les schémas, les utilitaires et les autres.  
  
## <a name="extensibility-architecture"></a>Architecture d’extensibilité  
 L’illustration suivante montre l’architecture d’extensibilité de Visual Studio. Les VSPackages fournissent des fonctionnalités d’application, qui sont partagées dans l’environnement de développement intégré (IDE) en tant que services. L’IDE standard offre également un large éventail de services, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , qui fournissent l’accès aux fonctionnalités de fenêtrage de l’IDE.  
  
 ![Graphique Architecture d'environnement](../../extensibility/internals/media/environment.gif "environnement")  
Vue généralisée de l’architecture Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 Les VSPackages sont des modules logiciels qui constituent et étendent Visual Studio avec des éléments, des services, des projets, des éditeurs et des concepteurs d’interfaces utilisateur. Les VSPackages sont l’unité architecturale centrale de Visual Studio. Pour plus d'informations, consultez [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Le shell Visual Studio fournit des fonctionnalités de base et prend en charge les communications croisées entre ses VSPackages de composant et les extensions MEF. Pour plus d’informations, consultez [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Conseils sur l’expérience utilisateur  
 Si vous envisagez de concevoir de nouvelles fonctionnalités pour Visual Studio, vous devez consulter ces instructions pour obtenir des conseils sur la conception et la convivialité : [instructions relatives à l’expérience utilisateur de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Commandes  
 Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier.  
  
 Quand vous étendez Visual Studio, vous pouvez créer des commandes et les inscrire avec le shell Visual Studio. Vous pouvez spécifier la façon dont ces commandes s’affichent dans l’IDE, par exemple, dans un menu ou une barre d’outils. En général, une commande personnalisée s’affiche dans le menu **Outils** et une commande permettant d’afficher une fenêtre outil s’affiche dans le sous-menu **autres fenêtres** du menu **affichage** .  
  
 Lorsque vous créez une commande, vous devez également créer un gestionnaire d’événements pour celle-ci. Le gestionnaire d’événements détermine quand la commande est visible ou activée, vous permet de modifier son texte et garantit que la commande répond de manière appropriée lorsqu’elle est activée. Dans la plupart des cas, l’IDE gère les commandes à l’aide de l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Dans Visual Studio, les commandes sont gérées en commençant par le contexte de commande le plus profond, en fonction de la sélection locale, et en poursuivant jusqu’au contexte le plus à l’extérieur, en fonction de la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts.  
  
 Pour plus d’informations, consultez [commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menus et barres d’outils  
 Les menus et les barres d’outils permettent aux utilisateurs d’appeler des commandes. Les menus sont des lignes ou des colonnes de commandes qui sont généralement affichées en tant qu’éléments de texte individuels en haut d’une fenêtre outil. Les sous-menus sont des menus secondaires qui s’affichent lorsqu’un utilisateur clique sur des commandes qui incluent une petite flèche. Les menus contextuels apparaissent quand un utilisateur clique avec le bouton droit sur certains éléments de l’interface utilisateur. Les noms de menu courants sont **fichier**, **Edition**, **affichage**et **fenêtre**. Pour plus d’informations, consultez [extension des menus et des commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Les barres d’outils sont des lignes ou des colonnes de boutons et d’autres contrôles, tels que les zones de liste modifiable, les zones de liste et les zones de texte. Les boutons de la barre d’outils ont généralement des images d’icône, telles qu’une icône de dossier pour une commande **ouvrir un fichier** ou une imprimante pour une commande **Imprimer** . Tous les éléments de la barre d’outils sont associés à des commandes. Lorsque vous cliquez sur un bouton de barre d’outils, la commande qui lui est associée s’exécute. Dans le cas d’un contrôle déroulant, chaque élément de la liste déroulante est associé à une commande différente. Certains contrôles de barre d’outils, tels qu’un contrôle Splitter, sont des hybrides. Un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui affiche plusieurs commandes lorsque l’utilisateur clique dessus.  
  
## <a name="tool-windows"></a>Fenêtres d'outils  
 Les fenêtres outil sont utilisées dans l’IDE pour afficher des informations. La **boîte à outils**, **Explorateur de solutions**, la fenêtre **Propriétés** et le **navigateur Web** sont des exemples de fenêtres outil.  
  
 Les fenêtres outil offrent généralement différents contrôles avec lesquels l’utilisateur peut interagir. Par exemple, la fenêtre **Propriétés** permet à l’utilisateur de définir des propriétés d’objets qui remplissent un but particulier. La fenêtre **Propriétés** est spécialisée dans ce sens, mais également générale, car elle peut être utilisée dans de nombreuses situations différentes. De même, la fenêtre de **sortie** est spécialisée, car elle fournit une sortie basée sur du texte, mais générale, car de nombreux sous-systèmes de Visual Studio peuvent l’utiliser pour fournir la sortie à l’utilisateur Visual Studio.  
  
 Prenons l’image suivante de Visual Studio, qui contient plusieurs fenêtres outil.  
  
 ![Capture d’écran](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Certaines fenêtres outil sont ancrées ensemble sur un volet unique qui affiche la fenêtre outil Explorateur de solutions et masque les autres fenêtres outil, mais les met à disposition en cliquant sur les onglets. L’image montre deux autres fenêtres outil, la **liste d’erreurs** et la fenêtre **sortie** , ancrées ensemble sur un seul volet.  
  
 Le volet document principal, qui affiche plusieurs fenêtres d’éditeur, s’affiche également. Bien que les fenêtres outil n’aient généralement qu’une seule instance (par exemple, vous ne pouvez ouvrir qu’une seule **Explorateur de solutions**), les fenêtres de l’éditeur peuvent avoir plusieurs instances, chacune d’elles étant utilisée pour modifier un document distinct, mais toutes sont ancrées dans le même volet. L’image montre un volet de document qui a deux fenêtres d’éditeur, une fenêtre de concepteur de formulaires et une fenêtre de navigateur qui affiche la page de démarrage. Toutes les fenêtres du volet de document sont disponibles en cliquant sur les onglets, mais la fenêtre de l’éditeur qui contient le fichier EditorPane.cs est visible et active.  
  
 Quand vous étendez Visual Studio, vous pouvez créer des fenêtres outil qui permettent aux utilisateurs de Visual Studio d’interagir avec votre extension. Vous pouvez également créer vos propres éditeurs qui permettent aux utilisateurs de Visual Studio de modifier des documents. Étant donné que vos fenêtres outil et éditeurs seront intégrés à Visual Studio, vous n’avez pas à les programmer pour les ancrer ou les afficher correctement dans un onglet. Lorsqu’ils sont correctement inscrits dans Visual Studio, ils disposent automatiquement des fonctionnalités standard des fenêtres outil et des fenêtres de document dans Visual Studio. Pour plus d’informations, consultez [extension et personnalisation des fenêtres outil](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Fenêtres de document  
 Une fenêtre de document est une fenêtre enfant encadrée d’une fenêtre d’interface multidocument (MDI, multiple-document interface). Les fenêtres de document sont généralement utilisées pour héberger des éditeurs de texte, des éditeurs de formulaires (également appelés concepteurs) ou des contrôles d’édition, mais elles peuvent également héberger d’autres types fonctionnels. La boîte de dialogue **nouveau fichier** contient des exemples de fenêtres de document fournies par Visual Studio.  
  
 La plupart des éditeurs sont spécifiques à un langage de programmation ou à un type de fichier, tels que des pages HTML, des jeux de frames, des fichiers C++ ou des fichiers d’en-tête. En sélectionnant un modèle dans la boîte de dialogue **nouveau fichier** , un utilisateur crée dynamiquement une fenêtre de document pour l’éditeur pour le type de fichier associé au modèle. Une fenêtre de document est également créée lorsqu’un utilisateur ouvre un fichier existant.  
  
 Les fenêtres de document sont limitées à la zone cliente MDI. Chaque fenêtre de document possède un onglet en haut, et l’ordre des onglets est lié à d’autres fenêtres qui peuvent être ouvertes dans la zone MDI. Cliquez avec le bouton droit sur l’onglet d’une fenêtre de document pour afficher un menu contextuel qui comprend des options permettant de fractionner la zone MDI en plusieurs groupes d’onglets horizontaux ou verticaux. Le fractionnement de la zone MDI permet d’afficher plusieurs fichiers en même temps. Pour plus d’informations, consultez [fenêtres de document](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Éditeurs  
 L’éditeur Visual Studio vous permet de le personnaliser et de l’utiliser pour votre propre type de contenu au moyen de la Managed Extensibility Framework (MEF). Dans de nombreux cas, vous n’aurez pas besoin de créer un VSPackage pour étendre l’éditeur. Toutefois, si vous souhaitez inclure des fonctionnalités à partir de l’interpréteur de commandes (par exemple, une commande de menu ou une touche de raccourci), vous pouvez combiner une extension MEF avec un VSPackage.  
  
 Vous pouvez également créer un éditeur personnalisé, par exemple si vous souhaitez lire et écrire dans une base de données, ou si vous souhaitez utiliser un concepteur. Vous pouvez également utiliser un éditeur externe tel que le bloc-notes ou Microsoft WordPad. Pour plus d’informations, consultez [éditeur et extensions du service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Services de langage  
 Si vous souhaitez que l’éditeur Visual Studio prenne en charge de nouveaux mots clés de programmation ou même un nouveau langage de programmation, vous créez un service de langage. Chaque service de langage peut implémenter certaines fonctionnalités de l’éditeur entièrement, partiellement ou pas du tout. Selon la façon dont il est configuré, le service de langage peut fournir une mise en surbrillance de la syntaxe, une correspondance des accolades, une prise en charge IntelliSense et d’autres fonctionnalités de l’éditeur.  
  
 Le cœur d’un service de langage est un analyseur et un scanneur. Un scanneur (ou analyseur lexical) divise un fichier source en éléments appelés jetons, et un analyseur établit les relations entre ces jetons. Lorsque vous créez un service de langage, vous devez implémenter l’analyseur et le scanneur afin que Visual Studio puisse comprendre les jetons et la grammaire du langage. Vous pouvez créer des services de langage managés ou non gérés. Pour plus d’informations, consultez [extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projets  
 Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser et créer le code source et d’autres ressources. Les projets vous permettent d’organiser, de générer, de déboguer et de déployer du code source, des références à des services Web et à des bases de données, ainsi que d’autres ressources. Les VSPackages peuvent étendre le système de projet Visual Studio en fournissant des types de projets, des sous-types de projet et des outils personnalisés.  
  
 Les projets peuvent également être rassemblés dans une solution, qui est un regroupement d’un ou de plusieurs projets qui fonctionnent ensemble pour créer une application. Les informations de projet et d’État relatives à la solution sont stockées dans deux fichiers de solution, le fichier de solution textuelle (. sln) et le fichier d’option d’utilisateur de solution binaire (. suo). Ces fichiers sont similaires aux fichiers de groupe (. vbg) qui ont été utilisés dans les versions antérieures de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , et aux fichiers de l’espace de travail (. dsw) et des options utilisateur (. opt) qui ont été utilisés dans les versions antérieures de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] .  
  
 Pour plus d’informations, consultez [projets](../../extensibility/internals/projects.md) et [solutions](../../extensibility/internals/solutions-overview.md).  
  
## <a name="project-and-item-templates"></a>Modèles de projet et d’élément  
 Visual Studio comprend des modèles de projet prédéfinis et des modèles d’élément de projet. Vous pouvez également créer vos propres modèles ou acquérir des modèles à partir de la Communauté, puis les intégrer dans Visual Studio. La [Galerie de code MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) est l’endroit où vous pouvez accéder aux modèles et extensions.  
  
 Les modèles contiennent la structure du projet et les fichiers de base requis pour générer un genre particulier d’application, de contrôle, de bibliothèque ou de classe. Lorsque vous souhaitez développer un logiciel qui ressemble à l’un des modèles, créez un projet basé sur le modèle, puis modifiez les fichiers de ce projet.  
  
> [!NOTE]
> Cette architecture de modèle n’est pas prise en charge pour les [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projets. Pour plus d’informations sur la création de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] modèles de projet, consultez [conception d’un Assistant](https://msdn.microsoft.com/library/a7c0be7e-9297-4fed-83e3-5645c896d56b).  
  
 Pour plus d’informations, consultez [Ajout de modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Propriétés et options  
 La fenêtre **Propriétés** affiche les propriétés d’un ou plusieurs éléments sélectionnés : l' [extension des propriétés](../../extensibility/internals/extending-properties.md) les pages d’options contiennent des ensembles d’options relatives à un composant particulier, comme un langage de programmation ou un VSPackage : les [pages Options et options](../../extensibility/internals/options-and-options-pages.md). Les paramètres sont généralement des fonctionnalités liées à l’interface utilisateur qui peuvent être importées et exportées : [prise en charge des paramètres utilisateur](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Services Visual Studio  
 Un service fournit un ensemble spécifique d’interfaces que les composants doivent consommer. Visual Studio fournit un ensemble de services qui peuvent être utilisés par tous les composants, y compris les extensions. Par exemple, les services Visual Studio permettent d’afficher ou de masquer des fenêtres outil de manière dynamique, permettant d’accéder à l’aide, à la barre d’État ou aux événements de l’interface utilisateur. L’éditeur Visual Studio fournit également des services qui peuvent être importés par les extensions de l’éditeur. Pour plus d’informations, consultez [utilisation et fourniture de services](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Débogueur  
 Le débogueur est l’interface utilisateur des composants de débogage spécifiques au langage. Si vous avez créé un nouveau service de langage, vous devrez créer un moteur de débogage spécifique pour raccorder le débogueur. Pour plus d’informations, consultez [extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Contrôle de code source  
 Pour plus d’informations sur l’implémentation d’un plug-in ou d’un VSPackage de contrôle de code source, consultez [contrôle de code source](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Assistants  
 Vous pouvez créer un Assistant conjointement avec un nouveau type de projet, afin que l’Assistant puisse aider vos utilisateurs à prendre les bonnes décisions lorsqu’ils créent un nouveau projet de ce type. Pour plus d’informations, consultez [assistants](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Outils personnalisés  
 Les outils personnalisés vous permettent d’associer un outil à un élément d’un projet et d’exécuter cet outil à chaque fois que le fichier est enregistré. Pour plus d’informations, consultez [outils personnalisés](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Utilitaires VSSDK  
 Le VSSDK comprend un ensemble d’utilitaires dont vous pouvez avoir besoin pour travailler avec différents aspects des VSPackages. Pour plus d’informations, consultez [VSSDK Utilities](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Utilisation de Windows Installer  
 Dans certains cas, vous devrez peut-être utiliser le Windows Installer plutôt que le programme d’installation VSIX : par exemple, vous devrez peut-être écrire dans le registre. Pour plus d’informations sur l’utilisation de Windows Installer avec vos extensions, consultez [installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Visionneuse de l’aide  
 Vous pouvez intégrer votre propre aide et les pages F1 dans la visionneuse d’aide. Pour plus d’informations, consultez [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
