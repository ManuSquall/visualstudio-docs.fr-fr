---
title: "Dans le Kit de d&#233;veloppement logiciel de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "feuille de route, intégration de Visual Studio SDK"
  - "Feuille de route SDK Visual Studio integration"
  - "Guide d'intégration, Visual Studio SDK"
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Dans le Kit de d&#233;veloppement logiciel de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette section fournit des informations détaillées sur les extensions de Visual Studio, y compris l'architecture de Visual Studio, les composants, services, schémas, utilitaires et autres.  
  
## Architecture d'extensibilité  
 L'illustration suivante montre l'architecture d'extensibilité de Visual Studio. Packages VS fournissent des fonctionnalités d'application, qui sont partagée entre l'IDE en tant que services. L'IDE standard offre également une large gamme de services, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui permettent d'accéder à la fonctionnalité de fenêtrage IDE.  
  
 ![Graphique Architecture d’environnement](../../extensibility/internals/media/environment.png "environment")  
Vue généralisée de l'architecture de Visual Studio  
  
## Packages VS  
 Les VSPackages sont des modules logiciels qui constituent et étendent Visual Studio avec des éléments, les services, les projets, les éditeurs et les concepteurs l'interface utilisateur. Les VSPackages sont l'unité centrale et architecture de Visual Studio. Pour plus d'informations, consultez [Packages VS](../../extensibility/internals/vspackages.md).  
  
## Shell Visual Studio  
 L'interpréteur de commandes de Visual Studio fournit des fonctionnalités de base et prend en charge les communications entre les extensions du composant VSPackages et MEF. Pour plus d'informations, consultez [Shell Visual Studio](../../extensibility/internals/visual-studio-shell.md).  
  
## Consignes d'environnement utilisateur  
 Si vous envisagez de concevoir de nouvelles fonctionnalités de Visual Studio, prenez un coup de œil à ces instructions pour les conseils de conception et de facilité d'utilisation : [Consignes d'environnement utilisateur Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## Commandes  
 Commandes sont des fonctions qui accomplissent les tâches, telles que l'impression d'un document, l'actualisation d'une vue ou en créant un nouveau fichier.  
  
 Lorsque vous étendez Visual Studio, vous pouvez créer des commandes et les enregistrer avec l'interpréteur de commandes de Visual Studio. Vous pouvez spécifier comment ces commandes seront affichent dans l'IDE, par exemple, dans un menu ou une barre d'outils. Apparaît généralement une commande personnalisée sur le **outils** menu et une commande permettant d'afficher une fenêtre outil apparaît sur le **autres fenêtres** sous\-menu de la **affichage** menu.  
  
 Lorsque vous créez une commande, vous devez également créer un gestionnaire d'événements pour celle\-ci. Le Gestionnaire d'événements détermine quand la commande est visible ou activé, vous permet de modifier son texte et garantit que la commande répond correctement lorsqu'il est activé. Dans la plupart des cas, l'IDE gère les commandes à l'aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Les commandes de Visual Studio sont gérées depuis le contexte de commande plus profond, en fonction de la sélection locale et en cours de traitement pour le contexte le plus extérieur, en fonction de la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour le script.  
  
 Pour plus d'informations, consultez [Commandes, Menus et barres d'outils](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Menus et barres d'outils  
 Menus et barres d'outils permettent aux utilisateurs d'appeler des commandes. Menus des lignes ou colonnes de commandes qui sont généralement affichés comme des éléments de texte en haut, une fenêtre outil. Sous\-menus sont des menus secondaires qui s'affichent lorsqu'un utilisateur clique sur les commandes qui incluent une petite flèche. Menus contextuels s'affichent lorsqu'un utilisateur clique sur certains éléments d'interface utilisateur. Certains noms de menu courantes **fichier**, **Modifier**, **mode**, et **fenêtre**. Pour plus d'informations, consultez [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Barres d'outils des lignes ou colonnes de boutons et autres contrôles, tels que les zones de texte, zones de liste et zones de liste déroulante. Boutons de barre d'outils ont généralement des images d'icônes, par exemple une icône de dossier pour un **Ouvrir le fichier** commande ou une imprimante pour un **Print** commande. Tous les éléments de barre d'outils sont associés à des commandes. Lorsque vous cliquez sur un bouton de barre d'outils, la commande associée s'exécute. Dans le cas d'un contrôle de liste déroulante, chaque élément dans la liste déroulante est associé à une autre commande. Certains contrôles de barre d'outils, telle qu'un contrôle splitter, sont des hybrides. Un côté du contrôle est un bouton de barre d'outils et l'autre extrémité est une flèche vers le bas qui affiche plusieurs commandes lorsque vous cliquez dessus.  
  
## Fenêtres d'outils  
 Fenêtres Outil sont utilisés dans l'IDE pour afficher des informations.**Boîte à outils**, **l'Explorateur de solutions**, **propriétés** fenêtre, et **navigateur Web** sont des exemples de fenêtres Outil.  
  
 Fenêtres Outil offrent généralement de divers contrôles avec lesquels l'utilisateur peut interagir. Par exemple, le **propriétés** fenêtre permet à l'utilisateur de définir les propriétés des objets qui jouent un rôle particulier. Le **propriétés** fenêtre est spécialisé en ce sens, mais également générale, car il peut être utilisé dans de nombreuses situations différentes. De même, le **sortie** est spécialisée dans la fenêtre, car elle fournit une sortie texte, mais général car de nombreux sous\-systèmes dans Visual Studio peuvent utiliser pour fournir un résultat à l'utilisateur de Visual Studio.  
  
 Pensez à l'image suivante de Visual Studio, qui contient plusieurs fenêtres Outil.  
  
 ![Capture d'écran](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Certaines fenêtres Outil sont ancrées ensemble sur un seul volet qui affiche la fenêtre outil de l'Explorateur de solutions et masque les autres fenêtres Outil, mais les rend disponibles en cliquant sur les onglets. L'illustration montre deux autres fenêtres Outil, la **liste d'erreurs** et **sortie** fenêtre, ancrée ensemble sur un seul volet.  
  
 Également indiqué est le volet du document principal, qui affiche plusieurs fenêtres de l'éditeur. Bien que les fenêtres Outil ont généralement qu'une seule instance \(par exemple, vous pouvez ouvrir qu'un seul **l'Explorateur de solutions**\), fenêtres d'éditeur peuvent avoir plusieurs instances, chacune d'elles est utilisé pour modifier un document distinct, mais qui sont ancrés dans le même volet. L'image montre un volet de document qui possède deux fenêtres de l'éditeur, une fenêtre de concepteur d'écran et une fenêtre de navigateur qui affiche la Page de démarrage. Toutes les fenêtres dans le volet de document sont disponibles en cliquant sur les onglets, mais la fenêtre de l'éditeur qui contient le fichier de EditorPane.cs est visible et actif.  
  
 Lorsque vous étendez Visual Studio, vous pouvez créer outil windows qui permet aux utilisateurs de Visual Studio interagissent avec votre extension. Vous pouvez également créer vos propres éditeurs qui permettent aux utilisateurs de Visual Studio de modifier des documents. Parce que vos fenêtres Outil et les éditeurs seront intégrés dans Visual Studio, il est inutile de les programmer pour ancrer et s'affichent correctement dans un onglet. Lorsqu'ils sont inscrits correctement dans Visual Studio, ils auront automatiquement les fonctionnalités standards de fenêtres Outil et les fenêtres de document dans Visual Studio. Pour plus d'informations, consultez [Extension et personnalisation des fenêtres Outil](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## Fenêtres de document  
 Une fenêtre de document est une fenêtre enfant encadré d'une fenêtre d'interface multidocument \(MDI\). Fenêtres de document sont généralement utilisés pour héberger les éditeurs de texte, des éditeurs de formulaire \(également appelé concepteurs\) ou des contrôles d'édition, mais ils peuvent également héberger des autres types fonctionnelles. Le **nouveau fichier** boîte de dialogue inclut des exemples de fenêtres de document par Visual Studio.  
  
 La plupart des éditeurs sont spécifiques à un langage de programmation ou à un type de fichier, telles que des pages HTML, des jeux de frames, des fichiers C\+\+ ou des fichiers d'en\-tête. En sélectionnant un modèle dans le **nouveau fichier** boîte de dialogue, un utilisateur crée dynamiquement une fenêtre de document de l'éditeur pour le type de fichier qui est associé au modèle. Une fenêtre de document est également créée lorsqu'un utilisateur ouvre un fichier existant.  
  
 Fenêtres de document sont limitées à la zone cliente MDI. Chaque fenêtre de document comporte un onglet en haut, et l'ordre de tabulation est lié à d'autres fenêtres qui peuvent être ouverts dans la zone MDI. Clic droit sur l'onglet d'une fenêtre de document affiche un menu contextuel qui inclut des options pour fractionner la zone MDI en plusieurs groupes de l'onglet horizontal ou vertical. Fractionnement de la zone MDI permet à plusieurs fichiers à afficher en même temps. Pour plus d'informations, consultez [Fenêtres de document](../../extensibility/internals/document-windows.md).  
  
## Éditeurs  
 L'éditeur Visual Studio vous permet de personnaliser et l'utiliser pour votre propre type de contenu au moyen de Managed Extensibility Framework \(MEF\). Dans de nombreux cas, vous devrez pas créer un VSPackage pour étendre l'éditeur, si vous souhaitez inclure des fonctionnalités à partir de l'interpréteur de commandes \(par exemple, une commande de menu ou une touche de raccourci\), vous pouvez associer une extension de MEF avec un VSPackage.  
  
 Vous pouvez également créer un éditeur personnalisé, par exemple si vous souhaitez lire et écrire dans une base de données, ou si vous souhaitez utiliser un concepteur. Vous pouvez également utiliser un éditeur externe, tel que bloc\-notes ou Microsoft WordPad. Pour plus d'informations, consultez [Éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
## Services de langage  
 Si vous souhaitez que l'éditeur de Visual Studio pour prendre en charge les nouveaux mots clés de programmation ou même un nouveau langage de programmation, vous créez un service de langage. Chaque service de langage peut implémenter certaines fonctionnalités de l'éditeur entièrement, partiellement ou pas du tout. Selon la façon dont il est configuré, le service de langage peut fournir la syntaxe, accolades correspondantes, prise en charge IntelliSense et autres fonctionnalités de l'éditeur.  
  
 Au cœur d'un service de langage sont un analyseur et un analyseur. Un scanneur \(ou un analyseur lexical\) divise un fichier source en éléments appelés jetons, et un analyseur établit les relations entre ces jetons. Lorsque vous créez un service de langage, vous devez implémenter l'analyseur et le moteur d'analyse afin que Visual Studio puisse comprendre les jetons et la grammaire du langage. Vous pouvez créer des services de langage managé ou non managé. Pour plus d'informations, consultez [Extensibilité du Service de langage ancien](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## Projets  
 Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser et générer le code source et autres ressources. Projets permettent d'organiser, générer, déboguer et déployer le code source, des références aux services Web et bases de données et d'autres ressources. Les VSPackages peuvent étendre le système de projet Visual Studio en fournissant des types de projets, sous\-types de projets et des outils personnalisés.  
  
 Les projets peuvent également être regroupées dans une solution, qui est un regroupement d'un ou plusieurs projets qui fonctionnent ensemble pour créer une application. Informations d'état et de projet qui se rapportent à la solution sont stockées dans deux fichiers de solution, le fichier texte solution \(.sln\) et le fichier solution binaire des options \(.suo\) utilisateur. Ces fichiers sont similaires aux fichiers de groupe \(.vbg\) qui ont été utilisés dans les versions antérieures de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], et l'espace de travail \(.dsw\) et l'utilisateur options \(.opt\) les fichiers qui ont été utilisés dans les versions antérieures de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)].  
  
 Pour plus d’informations, consultez [Projets](../../extensibility/internals/projects.md) et [Solutions](../../extensibility/internals/solutions.md).  
  
## Projet et modèles d'élément  
 Visual Studio inclut des modèles de projet prédéfinis et des modèles d'élément de projet. Vous pouvez également rendre vos propres modèles ou acquérir des modèles à partir de la Communauté et ensuite intégrées à Visual Studio. Le [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) est l'endroit idéal pour les modèles et les extensions.  
  
 Les modèles contiennent la structure de projet et les fichiers qui sont requis pour créer un type particulier d'application, de contrôle, de bibliothèque ou de classe de base. Lorsque vous souhaitez développer un logiciel semblable à l'un des modèles, créez un projet basé sur le modèle, puis modifiez les fichiers dans le projet.  
  
> [!NOTE]
>  Cette architecture de modèle n'est pas pris en charge pour [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] projets. Pour plus d'informations sur la création [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] modèles de projet, consultez [Conception d'un Assistant](/visual-cpp/ide/designing-a-wizard).  
  
 Pour plus d'informations, consultez [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Propriétés et les Options  
 Le **propriétés** affiche les propriétés d'éléments uniques ou multiples sélectionnés : [Étendre les propriétés](../../extensibility/internals/extending-properties.md) pages Options contiennent des jeux d'options qui se rapportent à un composant particulier, comme un langage de programmation ou un VSPackage : [Options et Pages d’Options](../../extensibility/internals/options-and-options-pages.md). Les paramètres sont généralement liés à l'interface utilisateur des fonctionnalités qui peuvent être importées et exportées : [Prise en charge pour les paramètres utilisateur](../../extensibility/internals/support-for-user-settings.md).  
  
## Services Visual Studio  
 Un service fournit un ensemble spécifique d'interfaces pour les composants à consommer. Visual Studio fournit un ensemble de services qui peut être utilisé par tous les composants, y compris les extensions. Par exemple, les services de Visual Studio permettent de fenêtres Outil pour être affiché ou masqué de manière dynamique, activer l'accès à l'aide, barre d'état ou des événements de l'interface utilisateur. L'éditeur Visual Studio fournit également des services qui peuvent être importés par les extensions de l'éditeur. Pour plus d'informations, consultez [À l'aide et fournir des Services](../../extensibility/using-and-providing-services.md).  
  
## Débogueur  
 Le débogueur est l'interface utilisateur pour les composants de débogage spécifiques à une langue. Si vous avez créé un nouveau service de langage, vous devrez créer un moteur de débogage spécifiques à raccorder le débogueur. Pour plus d'informations, consultez [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Contrôle de code source  
 Pour plus d'informations sur l'implémentation d'un plug\-in de contrôle de code source ou un VSPackage, consultez [Contrôle de code source](../../extensibility/internals/source-control.md).  
  
## Assistants  
 Vous pouvez créer un Assistant conjointement avec un nouveau type de projet, afin que l'Assistant peut aider vos utilisateurs prendre les bonnes décisions lorsqu'ils créent un nouveau projet de ce type. Pour plus d'informations, consultez [Assistants](../../extensibility/internals/wizards.md).  
  
## Outils personnalisés  
 Outils personnalisés vous permettent d'associer un outil à un élément dans un projet et exécutez cet outil chaque fois que le fichier est enregistré. Pour plus d'informations, consultez [Outils personnalisés](../../extensibility/internals/custom-tools.md).  
  
## Utilitaires VSSDK  
 VSSDK inclut un ensemble d'utilitaires dont vous avez besoin pour travailler avec différents aspects des VSPackages. Pour plus d'informations, consultez [Utilitaires VSSDK](../../extensibility/internals/vssdk-utilities.md).  
  
## À l'aide de Windows Installer  
 Dans certains cas, vous devrez peut\-être utiliser le programme d'installation de Windows plutôt que l'installateur VSIX : par exemple, vous devrez peut\-être écrire dans le Registre. Pour plus d'informations sur l'utilisation de Windows Installer avec vos extensions, consultez [Installation de packages VS avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## La visionneuse d'aide  
 Vous pouvez intégrer votre propre aide et les pages de la touche F1 dans la visionneuse d'aide. Pour plus d'informations, consultez [Kit de développement logiciel de Microsoft Help Viewer](../../extensibility/internals/microsoft-help-viewer-sdk.md).