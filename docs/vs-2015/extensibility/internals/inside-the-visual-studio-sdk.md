---
title: Dans le Kit de développement logiciel de Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 3c6c7bb6d149281048d281cb7af13fe51d75ffd5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443900"
---
# <a name="inside-the-visual-studio-sdk"></a>Dans le kit SDK Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette section fournit des informations détaillées sur les extensions de Visual Studio, y compris l’architecture de Visual Studio, composants, services, schémas, utilitaires et autres.  
  
## <a name="extensibility-architecture"></a>Architecture d’extensibilité  
 L’illustration suivante montre l’architecture d’extensibilité de Visual Studio. Packages VS fournissent des fonctionnalités d’application, qui sont partagée entre l’IDE en tant que services. L’IDE standard offre également un large éventail de services, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui permettent d’accéder à la fonctionnalité de fenêtrage IDE.  
  
 ![Graphique Architecture d’environnement](../../extensibility/internals/media/environment.gif "environnement")  
Vue généralisée de l’architecture de Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 Les VSPackages sont des modules logiciels qui constituent et étendent Visual Studio avec des éléments, des services, des projets, des éditeurs et des concepteurs d’interfaces utilisateur. Les VSPackages sont l’unité architecturale au centre de Visual Studio. Pour plus d'informations, consultez [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 L’interpréteur de commandes de Visual Studio fournit des fonctionnalités de base et prend en charge les communications entre son composant VSPackages et des extensions MEF. Pour plus d’informations, consultez [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Conseils sur l’expérience utilisateur  
 Si vous envisagez de concevoir de nouvelles fonctionnalités pour Visual Studio, vous devez prendre un coup de œil à ces instructions pour les conseils de conception et de facilité d’utilisation : [Recommandations pour l’expérience utilisateur Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Commandes  
 Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier.  
  
 Lorsque vous étendez Visual Studio, vous pouvez créer des commandes et les inscrire auprès de l’interpréteur de commandes de Visual Studio. Vous pouvez spécifier la façon dont ces commandes seront affichent dans l’IDE, par exemple, dans un menu ou une barre d’outils. En règle générale, une commande personnalisée s’affiche sur le **outils** menu et une commande pour afficher une fenêtre outil apparaît sur le **Windows autres** sous-menu de la **vue** menu.  
  
 Lorsque vous créez une commande, vous devez également créer un gestionnaire d’événements pour celle-ci. Le Gestionnaire d’événements détermine quand la commande est visible ou activée, vous permet de modifier son texte et de garantit que la commande répond correctement quand il est activé. Dans la plupart des cas, l’IDE gère les commandes à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Dans Visual Studio, les commandes sont gérées en commençant par le contexte de commande plus profond, basée sur la sélection locale, puis en continuant pour le contexte le plus extérieur, basé sur la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts.  
  
 Pour plus d’informations, consultez [commandes, Menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menus et barres d’outils  
 Menus et barres d’outils permettent aux utilisateurs d’appeler des commandes. Menus des lignes ou colonnes de commandes qui sont généralement affichés comme des éléments de texte en haut, une fenêtre outil. Sous-menus sont des menus secondaire qui s’affichent lorsqu’un utilisateur clique sur les commandes qui incluent une petite flèche. Menus contextuels s’affichent quand un utilisateur clique sur certains éléments d’interface utilisateur. Certains noms de menu courantes **fichier**, **modifier**, **vue**, et **fenêtre**. Pour plus d’informations, consultez [extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Barres d’outils sont des lignes ou colonnes de boutons et autres contrôles, tels que les zones de liste modifiable, zones de liste et zones de texte. Boutons de barre d’outils ont généralement des images d’icônes, par exemple une icône de dossier pour un **ouvrir un fichier** commande ou une imprimante pour un **impression** commande. Tous les éléments de barre d’outils sont associés à des commandes. Lorsque vous cliquez sur un bouton de barre d’outils, sa commande associée s’exécute. Dans le cas d’un contrôle de liste déroulante, chaque élément dans la liste déroulante est associé à une autre commande. Certains contrôles de barre d’outils, comme un contrôle splitter, sont des hybrides. Un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui affiche plusieurs commandes lorsque vous cliquez dessus.  
  
## <a name="tool-windows"></a>Fenêtres d'outils  
 Fenêtres Outil sont utilisées dans l’IDE pour afficher des informations. **Boîte à outils**, **l’Explorateur de solutions**, **propriétés** fenêtre, et **navigateur Web** sont des exemples de fenêtres Outil.  
  
 Fenêtres Outil offrent généralement différents contrôles avec lesquels l’utilisateur peut interagir. Par exemple, le **propriétés** fenêtre permet à l’utilisateur de définir les propriétés des objets qui jouent un rôle particulier. Le **propriétés** fenêtre est spécialisé en ce sens, mais également général car il peut être utilisé dans de nombreuses situations différentes. De même, le **sortie** est spécialisée dans la fenêtre, car elle fournit textuel de la sortie, mais général car de nombreux sous-systèmes dans Visual Studio peuvent l’utiliser pour fournir la sortie à l’utilisateur de Visual Studio.  
  
 Envisagez l’image suivante de Visual Studio, qui contient plusieurs fenêtres d’outils.  
  
 ![Capture d’écran](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Certaines fenêtres Outil sont ancrées ensemble sur un seul volet qui affiche la fenêtre outil de l’Explorateur de solutions et masque les autres fenêtres Outil, mais les rend disponibles en cliquant sur les onglets. L’illustration montre deux autres fenêtres Outil, le **liste d’erreurs** et **sortie** fenêtre, ancrée ensemble sur un seul volet.  
  
 Si vous est également affiché, le volet de document principal, qui montre plusieurs fenêtres de l’éditeur. Bien que les fenêtres Outil ont généralement qu’une seule instance (par exemple, vous pouvez ouvrir qu’un seul **l’Explorateur de solutions**), éditeur windows peuvent avoir plusieurs instances, chacun d’eux est utilisé pour modifier un document distinct, mais qui sont ancrées dans le même volet. L’illustration montre un volet de document qui a deux fenêtres de l’éditeur, une fenêtre du Concepteur de formulaire et une fenêtre de navigateur qui affiche la Page de démarrage. Toutes les fenêtres dans le volet de document sont disponibles en cliquant sur les onglets, mais la fenêtre d’éditeur qui contient le fichier de EditorPane.cs est visible et actif.  
  
 Lorsque vous étendez Visual Studio, vous pouvez créer outil windows qui permettent aux utilisateurs de Visual Studio interagissent avec votre extension. Vous pouvez également créer vos propres éditeurs qui permettent aux utilisateurs de Visual Studio à modifier des documents. Étant donné que vos fenêtres Outil et les éditeurs seront intégrés dans Visual Studio, il est inutile de les programmer pour ancrer ou s’affichent correctement sur un onglet. Lorsqu’ils sont inscrits correctement dans Visual Studio, ils auront automatiquement les fonctionnalités standard de fenêtres Outil et fenêtres de document dans Visual Studio. Pour plus d’informations, consultez [extension et personnalisation de Windows d’outil](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Fenêtres de document  
 Une fenêtre de document est une fenêtre enfant encadré d’une fenêtre d’interface multidocument (MDI). Fenêtres de document sont généralement utilisés pour héberger les éditeurs de texte, des éditeurs de formulaire (également appelé concepteurs) ou des contrôles d’édition, mais elles peuvent héberger également d’autres types fonctionnels. Le **nouveau fichier** boîte de dialogue inclut des exemples de fenêtres de document fournies par Visual Studio.  
  
 La plupart des éditeurs sont spécifiques à un langage de programmation ou à un type de fichier, telles que des pages HTML, des jeux de frames, des fichiers C++ ou des fichiers d’en-tête. En sélectionnant un modèle dans le **nouveau fichier** boîte de dialogue, un utilisateur crée dynamiquement une fenêtre de document pour l’Éditeur du type de fichier qui est associé au modèle. Une fenêtre de document est également créée lorsqu’un utilisateur ouvre un fichier existant.  
  
 Fenêtres de document sont limitées à la zone cliente MDI. Chaque fenêtre de document comporte un onglet situé en haut, et l’ordre de tabulation est lié à d’autres fenêtres qui peuvent être ouverts dans la zone MDI. Clic droit sur l’onglet d’une fenêtre de document affiche un menu contextuel qui inclut des options pour fractionner la zone MDI en plusieurs groupes d’onglets de horizontale ou verticale. Fractionnement de la zone MDI permet à plusieurs fichiers à afficher en même temps. Pour plus d’informations, consultez [Document Windows](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Éditeurs  
 L’éditeur Visual Studio vous permet de personnaliser et son utilisation pour votre propre type de contenu au moyen de Managed Extensibility Framework (MEF). Dans de nombreux cas, vous devrez pas créer un VSPackage pour étendre l’éditeur, si vous souhaitez inclure des fonctionnalités à partir de l’interpréteur de commandes (par exemple, une commande de menu ou une touche de raccourci), vous pouvez associer une extension MEF avec un VSPackage.  
  
 Vous pouvez également créer un éditeur personnalisé, par exemple si vous souhaitez lire et écrire dans une base de données, ou si vous souhaitez utiliser un concepteur. Vous pouvez également utiliser un éditeur externe tel que le bloc-notes ou WordPad de Microsoft. Pour plus d’informations, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Services de langage  
 Si vous souhaitez que l’éditeur de Visual Studio pour prendre en charge de nouveaux mots clés de programmation ou même un nouveau langage de programmation, vous créez un service de langage. Chaque service de langage peut implémenter certaines fonctionnalités de l’éditeur entièrement, partiellement ou pas du tout. Selon la façon dont il est configuré, le service de langage peut fournir la coloration syntaxique, correspondance des accolades, prise en charge IntelliSense et autres fonctionnalités dans l’éditeur.  
  
 Au cœur d’un service de langage sont un analyseur et un analyseur. Un scanneur (ou un analyseur lexical) divise un fichier source en éléments sont appelés jetons, et un analyseur établit les relations entre ces jetons. Lorsque vous créez un service de langage, vous devez implémenter l’analyseur et le moteur d’analyse afin que Visual Studio puisse comprendre les jetons et la grammaire du langage. Vous pouvez créer des services de langage managé ou non managé. Pour plus d’informations, consultez [extensibilité du Service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projets  
 Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser et à générer le code source et autres ressources. Les projets permettent d’organiser, générer, déboguer et déployer le code source, des références aux services Web et bases de données et d’autres ressources. Les VSPackages peuvent étendre le système de projet Visual Studio en fournissant des types de projets, les sous-types de projet et les outils personnalisés.  
  
 Les projets peuvent également être collectées dans une solution, qui est un regroupement d’un ou plusieurs projets qui fonctionnent ensemble pour créer une application. Informations d’état et de projet qui se rapportent à la solution sont stockées dans deux fichiers de solution, le fichier textuel solution (.sln) et le fichier solution binaire des options (.suo) utilisateur. Ces fichiers sont similaires pour les fichiers de groupe (.vbg) qui ont été utilisés dans les versions antérieures de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], ainsi que l’espace de travail (.dsw) et l’utilisateur options (.opt) les fichiers qui ont été utilisés dans les versions antérieures de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Pour plus d’informations, consultez [projets](../../extensibility/internals/projects.md) et [Solutions](../../extensibility/internals/solutions-overview.md).  
  
## <a name="project-and-item-templates"></a>Modèles de projet et d’élément  
 Visual Studio inclut des modèles de projet prédéfinis et des modèles d’élément de projet. Vous pouvez également rendre vos propres modèles ou acquérir des modèles à partir de la Communauté et puis de les intégrer à Visual Studio. Le [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio) est l’endroit idéal pour les modèles et les extensions.  
  
 Les modèles contiennent la structure de projet et les fichiers de base qui sont nécessaires pour générer un type particulier d’application, de contrôle, de bibliothèque ou de classe. Lorsque vous souhaitez développer des logiciels qui ressemble à un des modèles, créez un projet qui est basé sur le modèle, puis modifiez les fichiers dans ce projet.  
  
> [!NOTE]
> Cette architecture de modèle n’est pas pris en charge pour [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projets. Pour plus d’informations sur la création [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] modèles de projet, consultez [conception d’un Assistant](http://msdn.microsoft.com/library/a7c0be7e-9297-4fed-83e3-5645c896d56b).  
  
 Pour plus d’informations, consultez [Ajout d’un projet et des modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Propriétés et les Options  
 Le **propriétés** fenêtre affiche les propriétés d’un ou plusieurs éléments sélectionnés : [Étendre les propriétés](../../extensibility/internals/extending-properties.md) pages d’Options contiennent des jeux d’options qui se rapportent à un composant particulier, comme un langage de programmation ou à un VSPackage : [Options et Pages d’Options](../../extensibility/internals/options-and-options-pages.md). Les paramètres sont généralement liés par l’interface utilisateur des fonctionnalités qui peuvent être importées et exportées : [Prise en charge pour les paramètres utilisateur](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Services de Visual Studio  
 Un service fournit un ensemble spécifique d’interfaces pour les composants à consommer. Visual Studio fournit un ensemble de services qui peut être utilisé par tous les composants, y compris les extensions. Par exemple, Visual Studio services activer des fenêtres Outil pour être affiché ou masqué de manière dynamique, activer l’accès à l’aide, barre d’état ou d’événements d’interface utilisateur. L’éditeur Visual Studio fournit également des services pouvant être importé par les extensions de l’éditeur. Pour plus d’informations, consultez [utilisation et fourniture de Services](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Débogueur  
 Le débogueur est l’interface utilisateur pour les composants de débogage spécifiques au langage. Si vous avez créé un nouveau service de langage, vous devrez créer un moteur de débogage spécifiques à raccorder au débogueur. Pour plus d’informations, consultez [extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Contrôle de code source  
 Pour plus d’informations sur l’implémentation d’un plug-in de contrôle de code source ou d’un VSPackage, consultez [contrôle de code Source](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Assistants  
 Vous pouvez créer un Assistant conjointement avec un nouveau type de projet, afin que l’Assistant peut aider vos utilisateurs les bonnes décisions lorsqu’ils créent un nouveau projet de ce type. Pour plus d’informations, consultez [Assistants](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Outils personnalisés  
 Outils personnalisés vous permettent d’associer un outil à un élément dans un projet et d’exécuter cet outil chaque fois que le fichier est enregistré. Pour plus d’informations, consultez [outils personnalisés](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Utilitaires VSSDK  
 L’extensibilité de Visual Studio inclut un ensemble d’utilitaires dont vous avez besoin pour pouvoir fonctionner avec différents aspects de VSPackages. Pour plus d’informations, consultez [utilitaires VSSDK](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>À l’aide du programme d’installation de Windows  
 Dans certains cas, vous devrez peut-être utiliser le programme d’installation de Windows, plutôt que le programme d’installation VSIX : par exemple, vous devrez peut-être écrire dans le Registre. Pour plus d’informations sur l’utilisation du programme d’installation de Windows avec vos extensions, consultez [installation les VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Visionneuse d'aide  
 Vous pouvez intégrer votre propre aide et les pages de la touche F1 dans la visionneuse d’aide. Pour plus d’informations, consultez [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
