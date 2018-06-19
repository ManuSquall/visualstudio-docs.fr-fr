---
title: Dans le Kit de développement logiciel de Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fff6b720c11f3342a5894489186f57d397dd91b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134560"
---
# <a name="inside-the-visual-studio-sdk"></a>Dans le kit SDK Visual Studio
Cette section fournit des informations détaillées sur les extensions de Visual Studio, y compris l’architecture de Visual Studio, les composants, services, schémas, utilitaires et similaires.  
  
## <a name="extensibility-architecture"></a>Architecture d’extensibilité  
 L’illustration suivante montre l’architecture d’extensibilité de Visual Studio. Les VSPackages fournissent des fonctionnalités d’application, qui sont partagée entre l’IDE en tant que services. L’IDE standard offre également une large gamme de services, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui permettent d’accéder à la fonctionnalité de fenêtrage IDE.  
  
 ![Graphique Architecture d’environnement](../../extensibility/internals/media/environment.gif "environnement")  
Vue généralisée de l’architecture de Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 Les VSPackages sont des modules logiciels qui constituent et étendent Visual Studio avec des éléments, des services, des projets, des éditeurs et des concepteurs d’interfaces utilisateur. Les VSPackages sont l’unité architecturale au centre de Visual Studio. Pour plus d’informations, consultez [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 L’interpréteur de commandes de Visual Studio fournit des fonctionnalités de base et prend en charge les communications entre ses composants VSPackages et des extensions MEF. Pour plus d’informations, consultez [Shell Visual Studio](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Conseils sur l’expérience utilisateur  
 Si vous envisagez de concevoir de nouvelles fonctionnalités de Visual Studio, vous devez examiner ces instructions pour obtenir des conseils de conception et de facilité d’utilisation : [recommandations expérience utilisateur de Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Commandes  
 Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier.  
  
 Lors de l’extension Visual Studio, vous pouvez créer des commandes et les enregistrer avec l’interpréteur de commandes de Visual Studio. Vous pouvez spécifier la façon dont ces commandes seront affiche dans l’IDE, par exemple, dans un menu ou une barre d’outils. En règle générale, une commande personnalisée s’affiche sur le **outils** menu et une commande permettant d’afficher une fenêtre outil apparaît sur le **autres fenêtres** sous-menu du **vue** menu.  
  
 Lorsque vous créez une commande, vous devez également créer un gestionnaire d’événements pour celle-ci. Le Gestionnaire d’événements détermine quand la commande est visible ou activé, vous permet de modifier son texte et garantit que la commande répond correctement quand elle est activée. Dans la plupart des cas, l’IDE gère les commandes à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Dans Visual Studio, les commandes sont gérées en commençant par le contexte de commande plus profond, en fonction de la sélection locale, puis en continuant pour le contexte le plus extérieur, en fonction de la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts.  
  
 Pour plus d’informations, consultez [commandes, Menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menus et barres d’outils  
 Menus et barres d’outils permettent aux utilisateurs d’appeler des commandes. Les menus sont des lignes ou des colonnes des commandes qui sont généralement affichées comme des éléments de texte en haut, une fenêtre outil. Sous-menus sont des menus secondaire qui s’affichent lorsqu’un utilisateur clique sur les commandes qui incluent une petite flèche. Menus contextuels s’affichent lorsqu’un utilisateur clique sur certains éléments d’interface utilisateur. Certains noms de menu courantes **fichier**, **modifier**, **vue**, et **fenêtre**. Pour plus d’informations, consultez [étendant les Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Barres d’outils sont les lignes ou colonnes de boutons et autres contrôles, tels que les zones de liste déroulante, zones de liste et zones de texte. Boutons de barre d’outils ont généralement des images d’icône, par exemple une icône de dossier pour un **ouvrir le fichier** commande ou une imprimante pour un **impression** commande. Tous les éléments de barre d’outils sont associés à des commandes. Lorsque vous cliquez sur un bouton de barre d’outils, sa commande associée s’exécute. Dans le cas d’un contrôle de liste déroulante, chaque élément dans la liste déroulante est associé à une commande différente. Certains contrôles de barre d’outils, par exemple un contrôle splitter, sont des hybrides. Un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui affiche plusieurs commandes lorsque vous cliquez dessus.  
  
## <a name="tool-windows"></a>Fenêtres d'outils  
 Fenêtres Outil sont utilisées dans l’IDE pour afficher des informations. **Boîte à outils**, **l’Explorateur de solutions**, **propriétés** fenêtre, et **navigateur Web** sont des exemples de fenêtres Outil.  
  
 Fenêtres Outil offrent généralement différents contrôles avec lesquels l’utilisateur peut interagir. Par exemple, le **propriétés** fenêtre permet à l’utilisateur de définir les propriétés des objets qui jouent un rôle particulier. Le **propriétés** fenêtre est spécialisé dans ce sens, mais également général car il peut être utilisé dans de nombreuses situations différentes. De même, la **sortie** fenêtre est spécialisé, car il fournit une sortie basée sur le texte, mais général car plusieurs sous-systèmes dans Visual Studio peuvent utiliser pour fournir la sortie à l’utilisateur de Visual Studio.  
  
 Envisagez de l’image suivante de Visual Studio, qui contient plusieurs fenêtres d’outil.  
  
 ![Capture d’écran](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Certaines fenêtres Outil sont ancrées ensemble sur un seul volet qui affiche la fenêtre outil de l’Explorateur de solutions et masque les autres fenêtres Outil, mais les rend disponibles en cliquant sur les onglets. L’illustration montre deux autres fenêtres d’outils, le **liste d’erreurs** et **sortie** fenêtre, ancrée ensemble sur un seul volet.  
  
 Également indiqué est le volet de document principal, qui affiche plusieurs fenêtres de l’éditeur. Bien que les fenêtres Outil disposent généralement qu’une seule instance (par exemple, vous pouvez ouvrir qu’une seule **l’Explorateur de solutions**), fenêtres d’éditeur peuvent avoir plusieurs instances, chacune d’elles permet de modifier un document distinct, mais qui sont ancrés dans le même volet. L’illustration montre un volet de document qui a deux fenêtres de l’éditeur, une fenêtre de concepteur d’écran et une fenêtre de navigateur qui affiche la Page de démarrage. Toutes les fenêtres dans le volet de document sont disponibles en cliquant sur les onglets, mais la fenêtre d’éditeur qui contient le fichier de EditorPane.cs est visible et actif.  
  
 Lors de l’extension Visual Studio, vous pouvez créer outil windows qui permettent aux utilisateurs de Visual Studio interagissent avec votre extension. Vous pouvez également créer vos propres éditeurs qui permettent aux utilisateurs de Visual Studio à modifier des documents. Étant donné que vos fenêtres Outil et les éditeurs seront intégrées à Visual Studio, vous est inutile de les programmer pour ancrer ou s’affichent correctement sur un onglet. Lorsqu’ils sont inscrits correctement dans Visual Studio, ils auront automatiquement les fonctionnalités standards de fenêtres Outil et fenêtres de document dans Visual Studio. Pour plus d’informations, consultez [extension et la personnalisation des fenêtres Outil](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Fenêtres de document  
 Une fenêtre de document est une fenêtre enfant encadré d’une fenêtre de l’interface multidocument (MDI). Fenêtres de document sont généralement utilisés pour héberger les éditeurs de texte, des éditeurs de formulaire (également appelé concepteurs) ou des contrôles d’édition, mais qu’ils peuvent également héberger des autres types fonctionnelles. Le **nouveau fichier** boîte de dialogue inclut des exemples de fenêtres de document qui fournit de Visual Studio.  
  
 La plupart des éditeurs sont spécifiques à un langage de programmation ou à un type de fichier, telles que des pages HTML, des jeux de frames, des fichiers C++ ou des fichiers d’en-tête. En sélectionnant un modèle dans le **nouveau fichier** boîte de dialogue, un utilisateur crée dynamiquement une fenêtre de document de l’éditeur pour le type de fichier qui est associé au modèle. Une fenêtre de document est également créée lorsqu’un utilisateur ouvre un fichier existant.  
  
 Fenêtres de document sont limitées à la zone cliente MDI. Chaque fenêtre de document comporte un onglet en haut, et l’ordre de tabulation est lié à d’autres fenêtres qui peuvent être ouverts dans la zone MDI. Clic droit sur l’onglet d’une fenêtre de document affiche un menu contextuel qui inclut des options pour fractionner la zone MDI en plusieurs groupes de l’onglet horizontal ou vertical. Fractionnement de la zone MDI permet à plusieurs fichiers à afficher en même temps. Pour plus d’informations, consultez [les fenêtres de Document](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Éditeurs  
 L’éditeur Visual Studio vous permet de personnaliser et son utilisation pour votre propre type de contenu au moyen de Managed Extensibility Framework (MEF). Dans de nombreux cas, vous devrez pas créer un VSPackage pour étendre l’éditeur, si vous souhaitez inclure des fonctionnalités à partir de l’interpréteur de commandes (par exemple, une commande de menu ou une touche de raccourci), vous pouvez associer une extension de MEF avec un VSPackage.  
  
 Vous pouvez également créer un éditeur personnalisé, par exemple si vous souhaitez lire et écrire dans une base de données, ou si vous souhaitez utiliser un concepteur. Vous pouvez également utiliser un éditeur externe, tel que le bloc-notes ou WordPad de Microsoft. Pour plus d’informations, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Services de langage  
 Si vous souhaitez que l’éditeur de Visual Studio pour prendre en charge les nouveaux mots clés de programmation ou même un nouveau langage de programmation, vous créez un service de langage. Chaque service de langage peut implémenter certaines fonctionnalités de l’éditeur entièrement, partiellement ou pas du tout. Selon la façon dont il est configuré, le service de langage peut fournir la mise en surbrillance de syntaxe, la correspondance des accolades, prise en charge IntelliSense et d’autres fonctionnalités dans l’éditeur.  
  
 Au cœur d’un service de langage sont un analyseur et un analyseur. Un analyseur (ou l’analyseur lexical) divise un fichier source dans les éléments qui sont appelées des jetons et un analyseur établit les relations entre ces jetons. Lorsque vous créez un service de langage, vous devez implémenter l’analyseur et l’analyseur pour que Visual Studio puisse comprendre les jetons et la grammaire du langage. Vous pouvez créer des services de langage managé ou non managé. Pour plus d’informations, consultez [extensibilité de Service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projets  
 Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser et générer le code source et autres ressources. Permettent d’organiser, générer, déboguer et déployer le code source des projets, des références aux services Web et bases de données et d’autres ressources. Les VSPackages peuvent étendre le système de projet Visual Studio en fournissant des types de projets, les sous-types de projet et des outils personnalisés.  
  
 Les projets peuvent également être collectées dans une solution, qui est un regroupement d’un ou plusieurs projets qui travaillent conjointement pour créer une application. Informations de projet et d’état relative à la solution sont stockées dans deux fichiers de solution, le fichier textuel solution (.sln) et le fichier solution binaire des options (.suo) utilisateur. Ces fichiers sont similaires aux fichiers de groupe (.vbg) qui ont été utilisés dans les versions antérieures de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], ainsi que l’espace de travail (.dsw) et l’utilisateur d’options (.opt) les fichiers qui ont été utilisés dans les versions antérieures de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Pour plus d’informations, consultez [projets](../../extensibility/internals/projects.md) et [Solutions](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Modèles de projet et d’élément  
 Visual Studio inclut des modèles de projet prédéfinis et des modèles d’élément de projet. Vous pouvez également rendre vos propres modèles ou obtenir des modèles à partir de la Communauté et puis de les intégrer à Visual Studio. Le [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) est incontournable pour les modèles et les extensions.  
  
 Les modèles contiennent la structure de projet et les fichiers de base qui sont requises pour générer un type particulier d’application, de contrôle, de bibliothèque ou de classe. Lorsque vous souhaitez développer des logiciels qui ressemble à un des modèles, créez un projet qui est basé sur le modèle, puis modifiez les fichiers dans le projet.  
  
> [!NOTE]
>  Cette architecture de modèle n’est pas pris en charge pour [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projets. Pour plus d’informations sur la création [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modèles de projet, consultez [conception d’un Assistant](/cpp/ide/designing-a-wizard).  
  
 Pour plus d’informations, consultez [Ajout d’un projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Propriétés et les Options  
 Le **propriétés** fenêtre affiche les propriétés d’un ou plusieurs éléments sélectionnés : [étendre les propriétés](../../extensibility/internals/extending-properties.md) pages Options contiennent des ensembles d’options qui se rapportent à un composant particulier, comme un un VSPackage ou langage de programmation : [Options et les Pages d’Options](../../extensibility/internals/options-and-options-pages.md). Les paramètres sont généralement liées de l’interface utilisateur des fonctionnalités qui peuvent être importées et exportées : [prise en charge pour les paramètres utilisateur](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Services de Visual Studio  
 Un service fournit un ensemble spécifique d’interfaces pour les composants à consommer. Visual Studio fournit un ensemble de services qui peut être utilisé par tous les composants, y compris les extensions. Par exemple, les services de Visual Studio permettent des fenêtres Outil pour être affiché ou masqué de manière dynamique, permettent d’accéder à l’aide, barre d’état ou d’événements d’interface utilisateur. L’éditeur Visual Studio fournit également des services qui peuvent être importés par les extensions de l’éditeur. Pour plus d’informations, consultez [à l’aide et fourniture de Services](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Débogueur  
 Le débogueur est l’interface utilisateur pour les composants de débogage spécifiques à une langue. Si vous avez créé un nouveau service de langage, vous devrez créer un moteur de débogage spécifiques pour raccorder au débogueur. Pour plus d’informations, consultez [d’extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Contrôle de code source  
 Pour plus d’informations sur l’implémentation d’un plug-in de contrôle de code source ou d’un VSPackage, consultez [contrôle de code Source](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Assistants  
 Vous pouvez créer un Assistant conjointement avec un nouveau type de projet, afin que l’Assistant peut aider vos utilisateurs prendre les bonnes décisions lorsqu’ils créent un nouveau projet de ce type. Pour plus d’informations, consultez [Assistants](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Outils personnalisés  
 Des outils personnalisés vous permettent d’associer un outil avec un élément dans un projet et d’exécuter cet outil chaque fois que le fichier est enregistré. Pour plus d’informations, consultez [outils personnalisés](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Utilitaires d’extensibilité Visual Studio  
 L’extensibilité de Visual Studio inclut un ensemble d’utilitaires dont vous avez besoin pour travailler avec les différents aspects des VSPackages. Pour plus d’informations, consultez [utilitaires d’extensibilité Visual Studio](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>À l’aide du programme d’installation de Windows  
 Dans certains cas, vous devrez peut-être utiliser le programme d’installation de Windows, plutôt que le programme d’installation VSIX : par exemple, vous devez écrire dans le Registre. Pour plus d’informations sur l’utilisation de Windows Installer avec vos extensions, consultez [l’installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Visionneuse d'aide  
 Vous pouvez intégrer votre propre aide et les pages de la touche F1 dans la visionneuse d’aide. Pour plus d’informations, consultez [Kit de développement logiciel de Microsoft aide visionneuse](../../extensibility/internals/microsoft-help-viewer-sdk.md).