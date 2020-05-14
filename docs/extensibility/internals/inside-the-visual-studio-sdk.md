---
title: À l’intérieur du Studio Visuel SDK (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707575"
---
# <a name="inside-the-visual-studio-sdk"></a>Dans le kit SDK Visual Studio

Cette section fournit des informations approfondies sur les extensions Visual Studio, y compris l’architecture Visual Studio, composants, services, schémas, utilitaires, etc.

## <a name="extensibility-architecture"></a>Architecture d’extésensabilité
 L’illustration suivante montre l’architecture d’extéabilité Visual Studio. VSPackages fournit des fonctionnalités d’application, qui est partagée à travers l’IDE comme services. L’IDE standard offre également une large <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>gamme de services, tels que , qui donnent accès à la fonctionnalité de fenêtre IDE.

 ![Graphique de l’architecture de l’environnement](../../extensibility/internals/media/environment.gif "Environnement") Vue généralisée de l’architecture Visual Studio

## <a name="vspackages"></a>VSPackages
 Les VSPackages sont des modules logiciels qui constituent et étendent Visual Studio avec des éléments, des services, des projets, des éditeurs et des concepteurs d’interfaces utilisateur. VSPackages est l’unité architecturale centrale de Visual Studio. Pour plus d'informations, consultez [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 La coque Visual Studio fournit des fonctionnalités de base et supporte la communication croisée entre ses composants VSPackages et les extensions MEF. Pour plus d’informations, voir [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Conseils sur l’expérience utilisateur
 Si vous envisagez de concevoir de nouvelles fonctionnalités pour Visual Studio, vous devriez jeter un oeil à ces lignes directrices pour la conception et les conseils d’utilisabilité: [Visual Studio User Experience Guidelines](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Commandes
 Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier.

 Lorsque vous étendez Visual Studio, vous pouvez créer des commandes et les enregistrer avec la coque Visual Studio. Vous pouvez spécifier comment ces commandes apparaîtront dans l’IDE, par exemple, sur un menu ou une barre d’outils. Typiquement, une commande personnalisée apparaît sur le menu **Tools,** et une commande pour afficher une fenêtre d’outil apparaîtrait sur **l’autre** sous-mois Windows du menu **View.**

 Lorsque vous créez une commande, vous devez également créer un gestionnaire d’événements pour elle. Le gestionnaire d’événements détermine quand la commande est visible ou activée, vous permet de modifier son texte et garantit que la commande répond de manière appropriée lorsqu’elle est activée. Dans la plupart des cas, l’IDE gère les commandes en utilisant l’interface. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Les commandes en visual studio sont traitées en commençant par le contexte de commande le plus intime, basé sur la sélection locale, et de procéder au contexte le plus externe, basé sur la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts.

 Pour plus d’informations, voir [Commandes, Menus et Barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menus et barres d’outils
 Les menus et les barres d’outils permettent aux utilisateurs d’invoquer des commandes. Les menus sont des rangées ou des colonnes de commandes qui sont généralement affichées sous forme d’éléments de texte individuels en haut d’une fenêtre d’outil. Les sous-menus sont des menus secondaires qui apparaissent lorsqu’un utilisateur clique sur les commandes qui incluent une petite flèche. Les menus contextuels apparaissent lorsqu’un utilisateur clique à droite sur certains éléments de l’interface utilisateur. Certains noms de menu communs sont **Fichier**, **Edit**, **Voir**, et **fenêtre**. Pour plus d’informations, voir [Extending Menus and Commands](../../extensibility/extending-menus-and-commands.md).

 Les barres d’outils sont des rangées ou des colonnes de boutons et d’autres commandes, telles que des boîtes combo, des boîtes de liste et des boîtes de texte. Les boutons de barre d’outils ont généralement des images d’icône, comme une icône de dossier pour une commande **Open File** ou une imprimante pour une commande **d’impression.** Tous les éléments de barre d’outils sont associés aux commandes. Lorsque vous cliquez sur un bouton de barre d’outils, sa commande associée s’exécute. Dans le cas d’un contrôle d’abandon, chaque élément de la liste d’abandon est associé à une commande différente. Certains contrôles de barre d’outils, comme un contrôle de splitter, sont des hybrides. Un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui affiche plusieurs commandes quand il est cliqué.

## <a name="tool-windows"></a>Fenêtres d'outils
 Les fenêtres d’outils sont utilisées dans l’IDE pour afficher des informations. **Toolbox**, **Solution Explorer**, **Properties** window, et **Web Browser** sont des exemples de fenêtres d’outils.

 Les fenêtres d’outils offrent généralement divers contrôles avec lesquels l’utilisateur peut interagir. Par exemple, la fenêtre **Propriété** permet à l’utilisateur de définir des propriétés d’objets qui servent un but particulier. La fenêtre **Propriétés** est spécialisée en ce sens, mais aussi générale, car elle peut être utilisée dans de nombreuses situations différentes. De même, la fenêtre **Output** est spécialisée parce qu’elle fournit une sortie textuelle, mais généralement parce que de nombreux sous-systèmes de Visual Studio peuvent l’utiliser pour fournir la sortie à l’utilisateur Visual Studio.

 Considérez l’image suivante de Visual Studio, qui contient plusieurs fenêtres d’outils :

 ![Capture d’écran](../../extensibility/internals/media/t1gui.png "T1gui T1gui")

 Certaines des fenêtres d’outils sont amarrées ensemble sur un seul volet qui affiche la fenêtre de l’outil Solution Explorer et cache les autres fenêtres d’outils, mais les rend disponibles en cliquant sur des onglets. L’image montre deux autres fenêtres d’outils, la **liste d’erreurs** et la fenêtre **de sortie,** amarrées ensemble sur un seul volet.

 Le volet principal du document, qui affiche plusieurs fenêtres d’éditeur, est également indiqué. Bien que les fenêtres d’outils n’aient généralement qu’un seul exemple (par exemple, vous ne pouvez ouvrir qu’une seule **solution Explorer),** les fenêtres de l’éditeur peuvent avoir plusieurs instances, chacune d’entre elles est utilisée pour modifier un document distinct, mais qui sont tous amarrés dans la même vitre. L’image montre une vitre de document qui a deux fenêtres d’éditeur, une fenêtre de concepteur de forme. Toutes les fenêtres de la vitre du document sont disponibles en cliquant sur les onglets, mais la fenêtre de l’éditeur qui contient EditorPane.cs fichier est visible et active.

 Lorsque vous étendez Visual Studio, vous pouvez créer des fenêtres d’outils qui permettent aux utilisateurs de Visual Studio d’interagir avec votre extension. Vous pouvez également créer vos propres éditeurs qui permettent aux utilisateurs de Visual Studio d’éditer des documents. Étant donné que vos fenêtres et éditeurs d’outils seront intégrés dans Visual Studio, vous n’avez pas à les programmer pour s’amarrer ou apparaître correctement sur un onglet. Lorsqu’ils sont correctement enregistrés dans Visual Studio, ils auront automatiquement les caractéristiques typiques des fenêtres d’outils et des fenêtres de documents dans Visual Studio. Pour plus d’informations, voir [Extension et Personnaliser Tool Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Fenêtres de document
 Une fenêtre de document est une fenêtre encadrée d’enfant d’une fenêtre d’interface multi-documents (MDI). Les fenêtres de documents sont généralement utilisées pour héberger des éditeurs de texte, former des éditeurs (également connus sous le nom de concepteurs), ou modifier les contrôles, mais ils peuvent également héberger d’autres types fonctionnels. La boîte de dialogue **New File** comprend des exemples de fenêtres documentaires que Visual Studio fournit.

 La plupart des éditeurs sont spécifiques à un langage de programmation ou à un type de fichier, tels que des pages HTML, des jeux d’images, des fichiers CMD ou des fichiers d’en-tête. En sélectionnant un modèle dans la boîte de dialogue **New File,** un utilisateur crée dynamiquement une fenêtre de document pour l’éditeur pour le type de fichier qui est associé au modèle. Une fenêtre de document est également créée lorsqu’un utilisateur ouvre un fichier existant.

 Les fenêtres de documents sont limitées à la zone clientE MDI. Chaque fenêtre de document a un onglet sur le dessus, et l’ordre d’onglet est lié à d’autres fenêtres qui peuvent être ouvertes dans la zone MDI. En cliquant à droite, l’onglet d’une fenêtre de document affiche un menu raccourci qui comprend des options pour diviser la zone MDI en plusieurs groupes d’onglets horizontaux ou verticaux. Le fractionnement de la zone MDI permet de visualisant plusieurs fichiers en même temps. Pour plus d’informations, voir [Document Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Éditeurs
 L’éditeur Visual Studio vous permet de le personnaliser et de l’utiliser pour votre propre type de contenu au moyen du Cadre d’exténuabilité gérée (MEF). Dans de nombreux cas, vous n’aurez pas besoin de créer un VSPackage pour étendre l’éditeur, bien que si vous souhaitez inclure des fonctionnalités de la coque (par exemple, une commande de menu ou une clé de raccourci), vous pouvez combiner une extension MEF avec un VSPackage.

 Vous pouvez également créer un éditeur personnalisé, par exemple si vous souhaitez lire et écrire dans une base de données, ou si vous souhaitez utiliser un concepteur. Vous pouvez également utiliser un éditeur externe tel que Notepad ou Microsoft WordPad. Pour plus d’informations, voir [Extensions Editor et Language Service](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Services linguistiques
 Si vous voulez que l’éditeur de Visual Studio soutienne de nouveaux mots clés de programmation ou même un nouveau langage de programmation, vous créez un service linguistique. Chaque service linguistique peut implémenter certaines fonctionnalités de l’éditeur entièrement, partiellement ou pas du tout. Selon la façon dont il est configuré, le service linguistique peut fournir la mise en évidence syntaxe, l’appariement d’accolade, le support IntelliSense, et d’autres fonctionnalités dans l’éditeur.

 Au cœur d’un service linguistique se trouvent un analyseur et un scanner. Un scanner (ou lexer) divise un fichier source en éléments qui sont connus sous le nom de jetons, et un analyseur établit les relations entre ces jetons. Lorsque vous créez un service linguistique, vous devez implémenter le analyseur et le scanner afin que Visual Studio puisse comprendre les jetons et la grammaire de la langue. Vous pouvez créer des services linguistiques gérés ou non gérés. Pour plus d’informations, voir [Legacy Language Service Extensibility](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projets

Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser et construire le code source et d’autres ressources. Les projets vous permettent d’organiser, de construire, de déboiffer et de déployer du code source, des références aux services et bases de données Web et à d’autres ressources. VSPackages peut étendre le système de projet Visual Studio en fournissant des types de projets, des sous-types de projets et des outils personnalisés.

Les projets peuvent également être rassemblés dans le monde dans le monde dans le cas d’une *solution,* qui est un regroupement d’un ou de plusieurs projets qui travaillent ensemble pour créer une application. Les informations de projet et d’état qui se rapportent à la solution sont stockées dans deux fichiers de solution, le fichier de solution textuelle [(.sln)](solution-dot-sln-file.md) et le fichier option utilisateur de solution binaire [(.suo).](solution-user-options-dot-suo-file.md) Ces fichiers sont similaires aux fichiers de groupe (.vbg) qui ont été utilisés dans les versions antérieures de Visual Basic, et à l’espace de travail (.dsw) et aux options utilisateur (.opt) fichiers qui ont été utilisés dans les versions antérieures de C.

Pour plus d’informations, voir [Projets](../../extensibility/internals/projects.md) et [solutions](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Modèles de projet et d’élément
 Visual Studio comprend des modèles de projet prédéfinis et des modèles d’éléments de projet. Vous pouvez également faire vos propres modèles ou acquérir des modèles de la communauté, puis les intégrer dans Visual Studio. La [galerie de code MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) est l’endroit où aller pour les modèles et les extensions.

 Les modèles contiennent la structure du projet et les fichiers de base qui sont nécessaires pour construire un type particulier d’application, de contrôle, de bibliothèque ou de classe. Lorsque vous souhaitez développer un logiciel qui ressemble à l’un des modèles, créez un projet basé sur le modèle, puis modifiez les fichiers de ce projet.

> [!NOTE]
> Cette architecture de modèle [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] n’est pas prise en charge pour les projets.

 Pour plus d’informations, voir [Ajout de modèles d’éléments de projet et de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Propriétés et options
 La fenêtre **Propriétés** affiche les propriétés d’éléments uniques ou multiples sélectionnés : Les pages [Options d’extension](../../extensibility/internals/extending-properties.md) des propriétés contiennent des ensembles d’options qui se rapportent à un composant particulier, comme un langage de programmation ou un VSPackage : [Options et pages d’options.](../../extensibility/internals/options-and-options-pages.md) Les paramètres sont généralement des fonctionnalités liées à l’interface utilisateur qui peuvent être importées et exportées : [Support for User Settings](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Services de studio visuel
 Un service fournit un ensemble spécifique d’interfaces que les composants peuvent consommer. Visual Studio fournit un ensemble de services qui peuvent être utilisés par tous les composants, y compris les extensions. Par exemple, les services Visual Studio permettent de montrer ou de cacher dynamiquement les fenêtres des outils, d’accéder à l’aide, à la barre d’état ou aux événements d’interface utilisateur. L’éditeur visual Studio fournit également des services qui peuvent être importés par extensions d’éditeur. Pour plus d’informations, voir [Utilisation et Fournir des services](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Débogueur
 Le débogage est l’interface utilisateur des composants de débogage spécifiques à la langue. Si vous avez créé un nouveau service linguistique, vous devrez créer un moteur de déboçon spécifique pour s’accrocher au débbugger. Pour plus d’informations, voir [Visual Studio Debugger Extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Contrôle de la source
 Pour plus d’informations sur la mise en œuvre d’un plug-in de contrôle source ou VSPackage, voir [Contrôle source](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Assistants
 Vous pouvez créer un assistant en conjonction avec un nouveau type de projet, de sorte que l’assistant peut aider vos utilisateurs à prendre les bonnes décisions quand ils créent un nouveau projet de ce type. Pour plus d’informations, voir [Wizards](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Outils personnalisés
 Les outils personnalisés vous permettent d’associer un outil à un élément d’un projet et d’exécuter cet outil chaque fois que le fichier est enregistré. Pour plus d’informations, voir [Custom Tools](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilitaires VSSDK
 Le VSSDK comprend un ensemble d’utilitaires dont vous pourriez avoir besoin afin de travailler avec différents aspects de VSPackages. Pour plus d’informations, voir [VSSDK Utilities](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Utilisation de Windows Install
 Dans certains cas, vous devrez peut-être utiliser l’installateur Windows plutôt que l’installateur VSIX : par exemple, vous devrez peut-être écrire au registre. Pour plus d’informations sur l’utilisation de Windows Installer avec vos extensions, voir [installer VSPackages Avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Visionneuse de l’aide
 Vous pouvez intégrer votre propre aide et vos pages F1 dans le Visualiseur d’Aide. Pour plus d’informations, voir [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
