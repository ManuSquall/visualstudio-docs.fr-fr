---
title: Éditeur de code XAML
description: Visite guidée de l’éditeur de code XAML dans Visual Studio
ms.date: 06/16/2020
ms.topic: overview
f1_keywords:
- VS.XamlEditor
monikerRange: vs-2019
ms.custom: contperf-fy21q4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 672bfa6b28e364351f262cb2a2c6e2258ecd9746
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879393"
---
# <a name="xaml-code-editor"></a>Éditeur de code XAML

L’éditeur de code XAML dans l' [IDE de Visual Studio](../get-started/visual-studio-ide.md) comprend tous les outils dont vous avez besoin pour créer des applications WPF et UWP pour la plate-forme Windows, et pour [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). Cet article présente le rôle joué par l’éditeur de code lorsque vous développez des applications basées sur XAML, ainsi que les fonctionnalités qui sont uniques à l’éditeur de code XAML dans Visual Studio 2019.

Pour commencer, jetons un coup d’œil à l’IDE (environnement de développement intégré) avec un projet WPF ouvert. L’illustration suivante montre plusieurs des principaux outils de l’IDE que vous allez utiliser avec l’éditeur de code XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="L’IDE de Visual Studio 2019 avec un projet Open WPF en XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

En bas à gauche de l’image, les outils de l’IDE sont les suivants :

- La fenêtre de l' **[éditeur de code XAML](#xaml-code-editor-ui)** &mdash; objet de cet article &mdash; dans lequel vous créez et modifiez votre code.
- La fenêtre **[Concepteur XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** , où vous concevez votre interface utilisateur.
- Fenêtre Ancrable **[boîte à outils](../ide/reference/toolbox.md)** , dans laquelle vous ajoutez des contrôles à votre interface utilisateur.
- Le bouton **[Déboguer](../debugger/debugger-feature-tour.md)** , dans lequel vous exécutez votre code et déboguez-le. <br>(Vous pouvez également modifier votre code en temps réel pendant que vous déboguez avec le [rechargement à chaud XAML](xaml-hot-reload.md).)
- La fenêtre **[Explorateur de solutions](../ide/solutions-and-projects-in-visual-studio.md)** , dans laquelle vous gérez vos fichiers, projets et solutions.
- La fenêtre **[Propriétés](../ide/reference/properties-window.md)** , dans laquelle vous pouvez modifier l’apparence de l’interface utilisateur et la façon dont les contrôles d’interface utilisateur fonctionnent.

Pour continuer, nous allons en savoir plus sur l’éditeur de code XAML.

## <a name="xaml-code-editor-ui"></a>Interface utilisateur de l’éditeur de code XAML

Tandis que la fenêtre de l’éditeur de code pour les applications XAML partage des éléments d’interface utilisateur (interface utilisateur) qui s’affichent également dans notre IDE standard, il comprend également quelques fonctionnalités uniques qui facilitent le développement d’applications XAML.

Voici un aperçu de la fenêtre de l’éditeur de code XAML lui-même.

![Fenêtre de l’éditeur de code XAML dans Visual Studio](media/xaml-code-editor-window.png "Capture d’écran de la fenêtre de l’éditeur de code XAML dans Visual Studio 2019")

Examinons ensuite les fonctions de chacun des éléments de l’interface utilisateur dans l’éditeur de code.

### <a name="first-row"></a>Première ligne

Dans la première ligne située en haut de la fenêtre de code XAML, sur la gauche, il existe un onglet **conception** , un bouton **permuter les volets** , un onglet **XAML** et un bouton **XAML pop** .

![La première des deux premières lignes de la fenêtre de l’éditeur de code XAML dans Visual Studio, avec la partie gauche de la première ligne mise en surbrillance](media/xaml-code-editor-top-row-left.png "Capture d’écran de la première des deux premières lignes de la fenêtre de l’éditeur de code XAML dans Visual Studio 2019, dans laquelle les éléments d’interface utilisateur de gauche sont mis en surbrillance")

Voici comment ils fonctionnent :

- L’onglet **conception** fait passer le focus de l’éditeur de code XAML à la concepteur XAML.
- Le bouton **permuter les volets** inverse l’emplacement des concepteur XAML et l’éditeur de code XAML dans l’IDE.
- L’onglet **XAML** replace le focus sur l’éditeur de code XAML.
- Le bouton **XAML de menu contextuel** crée une fenêtre d’éditeur de code XAML distincte qui se trouve en dehors de l’IDE.

En continuant à droite, il y a un bouton de **fractionnement vertical** , un bouton de **fractionnement horizontal** et un bouton **réduire les volets** .

![La première des deux premières lignes de la fenêtre de l’éditeur de code XAML dans Visual Studio, avec la partie droite de la première ligne mise en surbrillance](media/xaml-code-editor-top-row-right.png "Capture d’écran de la première des deux premières lignes de la fenêtre de l’éditeur de code XAML dans Visual Studio 2019, dans laquelle les éléments d’interface utilisateur de droite sont mis en surbrillance")

Voici comment ils fonctionnent :

- Le bouton de **fractionnement vertical** modifie l’emplacement de la concepteur XAML et l’éditeur de code XAML dans l’IDE d’un alignement horizontal à un alignement vertical.
- Le bouton de **fractionnement horizontal** modifie l’emplacement de la concepteur XAML et l’éditeur de code XAML dans l’IDE d’un alignement vertical à un alignement horizontal.
- Le bouton **réduire le volet** vous permet de réduire ce qui se trouve dans le volet inférieur, qu’il s’agisse de l’éditeur de code ou du concepteur. (Pour restaurer le volet inférieur, cliquez à nouveau sur le même bouton, qui est maintenant appelé le bouton **développer le volet** .)

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Deuxième ligne

Dans la deuxième ligne située en haut de la fenêtre de code XAML, il existe deux listes déroulantes de fenêtres. Toutefois, si vous affichez l’info-bulle pour ces éléments d’interface utilisateur, ils les identifient plus en tant que « Element : Window » et « member : Window ».

![Deuxième des deux premières lignes de la fenêtre de l’éditeur de code XAML dans Visual Studio, où les deux listes déroulantes de la fenêtre sont visibles](media/xaml-code-editor-top-row-windows.png "Capture d’écran de la deuxième des deux premières lignes de la fenêtre de l’éditeur de code XAML dans Visual Studio 2019, dans laquelle les deux listes déroulantes de la fenêtre sont visibles")

Les listes déroulantes de la fenêtre ont des fonctions différentes, comme suit :

- L' **élément : Window** sur la gauche vous aide à afficher et à accéder aux éléments frères ou parents.

  Plus précisément, il vous montre un affichage de type plan qui révèle la structure de balises de votre code. Lorsque vous sélectionnez dans la liste, votre focus dans l’éditeur de code s’aligne sur la ligne de code qui comprend l’élément que vous avez sélectionné.

    ![Liste déroulante élément : fenêtre dans Visual Studio](media/xaml-element-window-dropdown.png "Capture d’écran de la liste déroulante d’éléments : Window dans Visual Studio 2019")

- La **fenêtre membre :** à droite vous aide à afficher et à accéder aux éléments d’attribut ou enfants.

    Plus précisément, il affiche une liste des propriétés dans votre code. Lorsque vous sélectionnez dans la liste, votre focus dans l’éditeur de code s’aligne sur la ligne de code qui comprend la propriété que vous avez sélectionnée.

    ![Liste déroulante membre : fenêtre dans Visual Studio](media/xaml-member-window-dropdown.png "Capture d’écran de la liste déroulante membre : fenêtre dans Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Volet central, éditeur de code

Le volet central est la partie « code » de l’éditeur de code XAML. Il comprend la plupart des fonctionnalités que vous trouverez dans l' [éditeur de code IDE](../get-started/tutorial-editor.md). Nous allons toucher à plusieurs des fonctionnalités IDE universelles qui peuvent vous aider à développer votre code XAML. Nous allons également mettre en évidence les fonctionnalités uniques de XAML dans l’IDE.

![L’éditeur de code XAML, volet central uniquement, dans Visual Studio](media/xaml-code-editor-middle.png "Capture d’écran de l’éditeur de code XAML, volet central uniquement, dans Visual Studio 2019")

#### <a name="quick-actions"></a>Actions rapides

Vous pouvez utiliser des [actions rapides](../ide/quick-actions.md) pour Refactoriser, générer ou modifier du code en une seule action.

Par exemple, une tâche utile que vous pouvez effectuer à l’aide d’actions rapides consiste à **Supprimer les using inutiles** du code C# dans l’onglet **MainWindow. Xaml. cs** .

Voici comment faire :

1. Pointez sur une instruction using, choisissez l’icône ampoule, puis choisissez **Supprimer les instructions using inutiles** dans la liste déroulante.

    ![L’option « Supprimer les using inutiles » de l’éditeur IDE dans le menu actions rapides](media/xaml-code-editor-remove-usings.png "Capture d’écran de l’option Supprimer les using inutiles de l’éditeur IDE du menu actions rapides")

1. Indiquez si vous souhaitez corriger toutes les occurrences dans le **document**, le **projet** ou la **solution**.
1. Affichez la boîte de dialogue **Aperçu** , puis choisissez **appliquer**.

Vous pouvez également accéder à cette fonctionnalité à partir de la barre de menus. Pour ce faire, choisissez **modifier**  >  **IntelliSense**  >  **supprimer et trier les using**.

Pour plus d’informations sur l’utilisation des paramètres, consultez la page trier les données [using](../ide/reference/sort-usings.md) . Pour plus d’informations sur IntelliSense, consultez la page [IntelliSense dans Visual Studio](../ide/using-intellisense.md) . Et, pour plus d’informations sur les façons courantes pour les développeurs d’utiliser des actions rapides, consultez la page [actions rapides communes](../ide/common-quick-actions.md) .

#### <a name="change-tracking"></a>Suivi des modifications

La couleur de la marge de gauche vous permet de conserver une trace des modifications effectuées dans un fichier. Voici comment les couleurs sont liées aux actions que vous effectuez :

- Les modifications que vous avez apportées depuis l’ouverture du fichier mais qui n’ont pas été enregistrées sont signalées par une barre **jaune** dans la marge de gauche (appelée marge de sélection).

    ![Éditeur de code-modifier avec la barre jaune](media/code-editor-edit-yellow.png "Capture d’écran de l’éditeur de code avec une modification marquée par une barre jaune dans la marge de sélection.")

- Une fois que vous avez enregistré les modifications (mais avant de fermer le fichier), la barre devient **verte**.

    ![Éditeur de code-modifier avec la barre verte](media/code-editor-edit-green.png "Capture d’écran de l’éditeur de code avec une modification marquée d’une barre verte dans la marge de sélection.")

Pour activer et désactiver cette fonctionnalité, modifiez l’option **Suivi des modifications** dans les paramètres **Éditeur de texte** (**Outils** > **Options** > **Éditeur de texte**).

Pour plus d’informations sur le suivi des modifications &mdash; afin d’inclure les lignes ondulées (également appelées « tildes ») qui s’affichent sous chaînes de code, &mdash; consultez la section fonctionnalités de l' **[éditeur](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** des [fonctionnalités de la page de l’éditeur de code Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md) .

#### <a name="right-click-context-menu"></a>Cliquez avec le bouton droit sur le menu contextuel

Lorsque vous modifiez votre code dans l’éditeur de code XAML, vous pouvez accéder à plusieurs fonctionnalités à l’aide du menu contextuel accessible par un clic droit. La plupart de ces fonctionnalités sont disponibles universellement dans l’IDE de Visual Studio, tandis que d’autres sont spécifiques à l’utilisation d’un éditeur de code et d’une fenêtre de conception.

![Capture d’écran du menu contextuel de l’éditeur de code XAML cliquez avec le bouton droit dans Visual Studio 2019.](media/xaml-code-editor-right-click-menu.png)

Voici ce que fait chaque fonctionnalité et comment elle est utile :

- **Afficher le code** : ouvre la fenêtre de code du langage de programmation, qui est généralement un onglet en regard de la vue par défaut qui comprend la fenêtre de conception et l’éditeur de code XAML.
- **Concepteur de vues** : ouvre la vue par défaut qui comprend la fenêtre de conception et l’éditeur de code XAML. (Si vous êtes déjà dans la vue par défaut, cela ne fait rien.)
- **Actions rapides et refactorisations** : refactorisation, génère ou modifie le code en une seule action. Quand vous pointez sur du code, une icône d’ampoule s’affiche quand une action rapide ou une refactorisation est disponible. <br>Voir aussi : [actions rapides](../ide/quick-actions.md) et [refactorisation du code](../ide/refactoring-in-visual-studio.md).
- **Renommer...** -Renomme uniquement les espaces de noms. Si vous n’avez pas d’espace de noms à renommer, vous recevrez un message d’erreur indiquant « seuls les préfixes d’espaces de noms peuvent être renommés ».
- **Supprimer et trier les espaces de noms** -supprime les espaces de noms inutilisés, puis trie les espaces de noms restants.
- **Aperçu de définition** : affiche un aperçu de la définition d’un type sans quitter votre emplacement actuel dans l’éditeur. <br>Voir aussi : [aperçu de définition](../ide/go-to-and-peek-definition.md#peek-definition) et [affichage et modification du code à l’aide de l’aperçu de définition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Atteindre la définition** -permet d’accéder à la source d’un type ou d’un membre et d’ouvrir le résultat dans un nouvel onglet. <br>Voir aussi : [atteindre la définition](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Entourer de...** -Utilisez des extraits de code entourer de, qui sont ajoutés autour d’un bloc de code sélectionné. <br>Voir aussi : [extraits d’expansion et extraits de code d’entourage](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Insérer un extrait** de code-insère un extrait de code à l’emplacement du curseur.
- **Coupe** -explicite
- **Copie** -explicite
- **Coller** -explicite
- **Mode plan** -développer et réduire des sections de code. <br>Voir aussi : [mode plan](../ide/outlining.md).
- **Contrôle** de code source-permet d’afficher l’historique des contributions de code dans un dépôt Open source.

### <a name="middle-pane-scroll-bar"></a>Volet central, barre de défilement

La barre de défilement peut faire plus que faire défiler votre code. Vous pouvez également l’utiliser pour ouvrir un autre volet de l’éditeur de code. De plus, vous pouvez utiliser la barre de défilement pour vous aider à coder plus efficacement en y ajoutant des annotations ou en utilisant différents modes d’affichage.

#### <a name="split-the-code-window"></a>Fractionner la fenêtre de code

Dans la barre de défilement de l’éditeur de code, un bouton **partagé** se trouve en haut à droite. Lorsque vous le choisissez, vous pouvez ouvrir un autre volet de l’éditeur de code. Cela est utile parce qu’ils fonctionnent indépendamment les uns des autres, ce qui vous permet de les utiliser pour travailler sur du code à différents emplacements.

![Capture d’écran montrant le volet central de l’éditeur de code XAML dans Visual Studio 2019 avec le bouton partagé mis en surbrillance en haut à droite du volet.](media/code-editor-split-window-button.png)

Pour plus d’informations sur la façon de fractionner une fenêtre de l’éditeur, consultez la page [gérer les fenêtres](../ide/how-to-manage-editor-windows.md) de l’éditeur.

#### <a name="use-annotations-or-map-mode"></a>Utiliser des annotations ou le mode carte

Vous pouvez également modifier l’apparence de la barre de défilement et les fonctionnalités supplémentaires qu’elle contient. Par exemple, de nombreuses personnes aiment inclure des *Annotations* dans la barre de défilement, qui fournissent des signaux visuels tels que les modifications du code, les points d’arrêt, les signets, les erreurs et la position du signe insertion.

D’autres apprécient l’utilisation du *mode carte*, qui affiche des lignes de code dans la miniature de la barre de défilement. Les développeurs qui ont beaucoup de code dans un fichier peuvent trouver que le mode de mappage effectue le suivi des lignes de code plus efficacement que la barre de défilement par défaut.

Pour plus d’informations sur la modification des paramètres par défaut de la barre de défilement, consultez la page  [personnaliser la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) .

## <a name="xaml-specific-features"></a>Fonctionnalités spécifiques à XAML

La plupart des fonctionnalités suivantes sont universellement disponibles dans l’IDE de Visual Studio, mais il existe des dimensions supplémentaires qui rendent le codage plus facile pour les développeurs XAML.

### <a name="xaml-code-snippets"></a>Extraits de code XAML

Les extraits de code sont de petits blocs de code réutilisables que vous pouvez insérer dans dans un fichier de code à l’aide de la commande de menu contextuel **Insérer un extrait** ou d’une combinaison de raccourcis clavier (**CTRL** + **K**, **CTRL** + **X**). Nous avons amélioré [IntelliSense](../ide/using-intellisense.md) afin qu’il prenne en charge l’utilisation d’extraits de code XAML, qui fonctionnent pour les extraits de code intégrés et pour tous les extraits de code personnalisés que vous ajoutez manuellement. Certains extraits de code XAML prêts à l’emploi incluent `#region` ,,, `Column definition` `Row definition` `Setter` et `Tag` .

![L’éditeur de code XAML avec les options d’extrait de code XAML affichées dans IntelliSense](media/xaml-code-snippets.png "Capture d’écran de l’éditeur de code XAML avec les options d’extrait de code XAML affichées dans IntelliSense")

Pour plus d’informations, consultez les pages [extraits de code](../ide/code-snippets.md) et [extraits de code C#](../ide/visual-csharp-code-snippets.md) .

### <a name="xaml-region-support"></a>Prise en charge du #region XAML

À compter de Visual Studio 2015, nous avons rendu #region prise en charge disponible pour les développeurs XAML dans WPF et UWP, et plus récemment dans [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). Dans Visual Studio 2019, nous continuons à apporter des améliorations incrémentielles à la prise en charge de #region. Par exemple, dans la [version 16,4](/visualstudio/releases/2019/release-notes-v16.4/) et les versions ultérieures, #region options s’affichent au fur et à mesure que vous commencez à taper `<!` .

![Éditeur de code XAML avec les options de #region affichées dans IntelliSense](media/code-editor-xaml-region.png "Capture d’écran de l’éditeur de code XAML avec les options de #region affichées dans IntelliSense")

Vous pouvez utiliser des régions lorsque vous souhaitez regrouper des sections de votre code que vous souhaitez également développer ou réduire.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Pour plus d’informations sur les régions, consultez la page [#region (référence C#)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) . Pour plus d’informations sur le développement et la réduction des sections de code, consultez la page [mode plan](../ide/outlining.md) .

### <a name="xaml-comments"></a>Commentaires XAML

Les développeurs préfèrent souvent documenter leur code à l’aide de commentaires. Vous pouvez ajouter des commentaires au code XAML qui se trouve sous l’onglet **MainWindow. Xaml** des manières suivantes :

- Entrez `<!--` avant un commentaire, puis ajoutez `-->` après le commentaire.
- Entrez `<!` , puis choisissez `!--` dans la liste des options.

  ![Éditeur de code XAML cliquez avec le bouton droit sur Ajouter des commentaires](media/xaml-code-editor-comments.png "Capture d’écran du menu contextuel en cliquant avec le bouton droit pour ajouter des commentaires dans l’éditeur de code XAML")

- Sélectionnez le code que vous souhaitez entourer d’un commentaire, puis choisissez le bouton **Commentaire** dans la barre d’outils de l’IDE. Pour inverser l’action, choisissez le bouton Annuler les **marques de commentaire** .

  ![Le bouton commentaire et le bouton Annuler les marques de commentaire dans la barre d’outils de l’IDE](media/comment-undo-comment-buttons.png "Capture d’écran du bouton commentaire et du bouton Annuler les marques de commentaire dans la barre d’outils de l’IDE")

- Sélectionnez le code que vous souhaitez entourer d’un commentaire, puis appuyez sur **CTRL** + **K**, **CTRL** + **C**. Pour supprimer les marques de commentaire du code sélectionné, appuyez sur **CTRL** + **K**, **CTRL** + **U**.

Pour plus d’informations sur l’utilisation de commentaires dans le code C# qui se trouve dans l’onglet **MainWindow. Xaml. cs** , consultez la page [Commentaires de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments/) .

### <a name="xaml-lightbulbs"></a>Ampoules XAML

Les icônes d’ampoule qui apparaissent dans votre code XAML font partie des [actions rapides](../ide/quick-actions.md) que vous pouvez utiliser pour Refactoriser, générer ou modifier le code.

Voici quelques exemples de la façon dont ils peuvent tirer parti de votre expérience de codage XAML :

- **Supprimez les espaces de noms inutiles**. Dans l’éditeur de code XAML, les espaces de noms inutiles apparaissent dans du texte estompé. Si vous placez votre curseur sur une utilisation inutile, une ampoule s’affiche. Lorsque vous choisissez l’option **Supprimer les espaces de noms inutiles** dans la liste déroulante, vous verrez un aperçu de ce que vous pouvez supprimer.

  ![L’option Supprimer les espaces de noms inutiles de l’éditeur de code XAML de l’ampoule actions rapides](media/xaml-code-editor-dimmed-namespaces-preview.png "Capture d’écran de l’option Supprimer les espaces de noms inutiles de l’éditeur de code XAML qui s’affiche à l’aide de l’ampoule actions rapides")

- **Renommez l’espace de noms**. Cette fonctionnalité, accessible à partir du menu contextuel de clic droit après avoir mis en surbrillance un espace de noms, facilite la modification de plusieurs instances d’un paramètre à la fois. Vous pouvez également accéder à cette fonctionnalité à l’aide de la barre de menus, **modifier**  >  **Refactoriser** le  >  **changement de nom**, ou en appuyant sur **CTRL** + **r**, puis à nouveau sur **CTRL** + **r** .

  ![L’option renommer l’espace de noms de l’éditeur de code XAML dans le menu contextuel du clic droit](media/code-editor-rename-namespace.png "Capture d’écran de l’option renommer l’espace de noms de l’éditeur de code XAML qui apparaît en utilisant le menu contextuel de clic droit")

  Pour plus d’informations, consultez la page [Renommer un symbole de code refactorisation](../ide/reference/rename.md) .

### <a name="conditional-xaml-for-uwp"></a>XAML conditionnel pour UWP

Le XAML conditionnel permet d'utiliser la méthode [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) dans le balisage XAML. Cela vous permet de définir des propriétés et d’instancier des objets sur la base de la présence d’une API sans avoir à utiliser le code-behind.

Pour plus d’informations, consultez la page [XAML conditionnel](/windows/uwp/debug-test-perf/conditional-xaml/) et la page [héberger les contrôles XAML UWP dans les applications de bureau (îlots XAML)](/windows/apps/desktop/modernize/xaml-islands/) .

### <a name="xaml-structure-visualizer"></a>Visualiseur de structure XAML

La fonctionnalité visualiseur de structure de l’éditeur de code affiche des lignes de repère de structure, qui sont des lignes verticales en pointillés qui indiquent les éléments de balise ouverts et fermés dans votre code. Ces lignes verticales permettent de voir plus facilement où les blocs logiques commencent et se terminent.

Pour plus d’informations, consultez la page de [code Navigate](../ide/navigating-code.md) .

### <a name="intellicode-for-xaml"></a>IntelliCode pour XAML

Lorsque vous ajoutez une balise XAML à votre code, vous commencez généralement par un chevron gauche `<` . Lorsque vous tapez ce crochet pointu, un menu IntelliCode qui répertorie plusieurs des balises XAML les plus populaires s’affiche. Choisissez celui que vous souhaitez ajouter rapidement à votre code.

Vous pouvez reconnaître les sélections IntelliCode, car elles apparaissent en haut de la liste et sont une étoile.

![Liste IntelliCode pour l’éditeur de texte XAML](media/xaml-intellicode-selection.png "Capture d’écran de la liste IntelliCode pour l’éditeur de texte XAML")

Pour plus d’informations, consultez la page [vue d’ensemble de IntelliCode](/visualstudio/intellicode/overview/) .

### <a name="settings"></a>Paramètres

Pour plus d’informations sur *tous* les paramètres de l’IDE de Visual Studio, consultez les [fonctionnalités de la page de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md) .

## <a name="xaml-optional-settings"></a>Paramètres facultatifs XAML

Vous pouvez utiliser la boîte de dialogue [options](../ide/reference/options-dialog-box-visual-studio.md) pour modifier les paramètres par défaut de l’éditeur de code XAML. Pour afficher les paramètres, choisissez **Outils**  >  **options**  >  **éditeur de texte**  >  **XAML**.

![Liste d’options de l’éditeur de texte XAML](media/xaml-tools-options.png "Capture d’écran de la liste d’options pour l’éditeur de texte XAML")

> [!NOTE]
> Vous pouvez également utiliser les raccourcis clavier pour accéder à la boîte de dialogue Options. Voici comment : Appuyez sur **CTRL** + **Q** pour rechercher dans l’IDE, tapez **options**, puis appuyez sur **entrée**. Appuyez ensuite sur **CTRL** + **E** pour rechercher dans la boîte de dialogue Options, tapez **éditeur de texte**, appuyez sur **entrée**, tapez **XAML**, puis appuyez sur **entrée**.
>
> Pour plus d’informations sur les raccourcis clavier, consultez la page [conseils de raccourci pour Visual Studio](../ide/productivity-shortcuts.md#code-editor) .

### <a name="universal-text-editor-options"></a>Options de l’éditeur de texte universel

Dans la boîte de dialogue [options](../ide/reference/options-text-editor-xaml-formatting.md) pour XAML, les trois premiers éléments suivants sont universels pour tous les langages de programmation pris en charge par l’IDE de Visual Studio. Consultez les informations liées dans le tableau suivant pour en savoir plus sur ces options et leur utilisation.

|Nom  |En savoir plus  |
|---------|---------|
|Général  | [Boîte de dialogue Options : éditeur de texte > tous les langages](../ide/reference/options-text-editor-all-languages.md) |
|Barres de défilement | [Options, Éditeur de texte, Tous les langages, Barres de défilement](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Tabulations  |  [Options, Éditeur de texte, Tous les langages, Tabulations](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Options de l’éditeur de texte spécifique à XAML

Le tableau suivant répertorie les paramètres de la boîte de dialogue [options](../ide/reference/options-text-editor-xaml-formatting.md) qui peuvent améliorer votre expérience de modification lorsque vous développez des applications basées sur XAML. Visitez les informations liées pour en savoir plus sur ces options et leur utilisation.

|Nom  |En savoir plus  |
|---------|---------|
|Mise en forme | [Options, Éditeur de texte, XAML, Mise en forme](../ide/reference/options-text-editor-xaml-formatting.md) |
|Divers |  [Options, Éditeur de texte, XAML, Divers](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> Le paramètre de nom de méthode de gestionnaire d’événements mettre en **majuscules** dans la section **divers** est particulièrement utile pour les développeurs XAML. Ce paramètre est *désactivé* par défaut, car il est nouveau, mais nous vous suggérons de le définir *sur activé* pour prendre en charge la casse appropriée dans votre code.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur la modification de votre code en temps réel pendant que vous exécutez votre application en mode débogage, consultez la page de [rechargement à chaud XAML](xaml-hot-reload.md) .

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML dans les applications UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML dans les applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
- [Développement d’applications mobiles Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visite guidée de Visual Studio 2019 pour Mac-IDE (Mac)](/visualstudio/mac/ide-tour/)
