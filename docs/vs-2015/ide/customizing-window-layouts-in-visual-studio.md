---
title: Personnalisation des dispositions de fenêtres
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a0f6b087f512750ae729d52c0855e3d4981d330
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "53934373"
---
# <a name="customizing-window-layouts-in-visual-studio"></a>Personnalisation des dispositions de fenêtres dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez personnaliser la position, la taille et le comportement des fenêtres pour créer des dispositions de fenêtres optimisées pour différents flux de travail de développement. Quand vous personnalisez la disposition, l'IDE mémorise vos paramètres. Ainsi, si vous modifiez l'emplacement d'ancrage de l' **Explorateur de solutions** et que vous fermez Visual Studio, l' **Explorateur de solutions** sera ancré au même emplacement au prochain démarrage, même si vous travaillez sur un autre ordinateur. Vous pouvez également nommer et enregistrer une disposition personnalisée, et basculer d’une disposition à une autre avec une seule commande. Vous pouvez par exemple créer une disposition pour la modification et une autre pour le débogage, et basculer de l’une à l’autre avec la commande de menu **Fenêtre &#124; Appliquer la disposition de fenêtre**.

## <a name="kinds-of-windows"></a>Types de fenêtres

### <a name="tool-and-document-windows"></a>Fenêtres Outil et Document
 L'IDE comprend deux types de fenêtres de base : les *fenêtres Outil* et les *fenêtres de document*. Les fenêtres Outil comprennent l'Explorateur de solutions, l'Explorateur de serveurs, la fenêtre Sortie, la liste d'erreurs, les concepteurs, les fenêtres du débogueur, etc. Les fenêtres de document contiennent les fichiers de code source, les fichiers de texte arbitraire, les fichiers de configuration, etc. Utilisez la barre de titre des fenêtres Outil pour les redimensionner et les déplacer. Utilisez l'onglet des fenêtres de document pour les déplacer. Cliquez avec le bouton droit sur l'onglet ou la barre de titre pour définir d'autres options dans la fenêtre.

 Le menu **Fenêtre** affiche les options d'ancrage, de flottement et de masquage des fenêtres dans l'IDE. Cliquez avec le bouton droit sur l'onglet ou la barre de titre d'une fenêtre pour afficher des options supplémentaires pour cette fenêtre spécifique. Vous pouvez afficher plusieurs instances d'une même fenêtre Outil à la fois. Par exemple, vous pouvez afficher plusieurs fenêtres du navigateur web, et vous pouvez créer des instances supplémentaires de certaines fenêtres Outil en choisissant **Nouvelle fenêtre** dans le menu **Fenêtre** .

### <a name="preview-tab-document-windows"></a>Onglet Aperçu (fenêtres de document)
 L'onglet Aperçu vous permet d'afficher les fichiers dans l'éditeur sans les ouvrir. Vous pouvez afficher un aperçu des fichiers en les sélectionnant dans l' **Explorateur de solutions**, pendant le débogage lorsque vous effectuez un pas à pas détaillé des fichiers, avec Atteindre la définition et quand vous parcourez les résultats d'une recherche. Les fichiers d'aperçu apparaissent aussi sous un onglet à droite de l'onglet de document. Le fichier s'ouvre pour modification si vous le modifiez ou si vous choisissez **Ouvrir**.

### <a name="tab-groups"></a>Groupes d'onglets
 Les groupes d'onglets vous permettent de mieux gérer l'espace de travail limité quand vous travaillez avec deux documents ouverts ou plus dans l'IDE. Vous pouvez organiser plusieurs fenêtres Outil et fenêtres de document en groupes d'onglets verticaux ou horizontaux et lire de façon aléatoire les documents d'un groupe d'onglets à un autre.

### <a name="split-windows"></a>Fenêtres fractionnées
 Quand vous devez afficher ou modifier deux emplacements à la fois dans un document, vous pouvez fractionner les fenêtres. Pour diviser votre document en deux sections qui défilent indépendamment, cliquez sur **Fractionner** dans le menu **Fenêtre** . Cliquez sur **Supprimer le fractionnement** dans le menu **Fenêtre** pour revenir à la vue unique.

### <a name="toolbars"></a>Barres d'outils
 Vous pouvez organiser les barres d'outils en les faisant glisser ou en utilisant la boîte de dialogue **Personnaliser** . Pour plus d’informations sur la façon de positionner et de personnaliser les barres d’outils, consultez [Guide pratique pour personnaliser les menus et les barres d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arranging-and-docking-windows"></a>Organisation et ancrage de fenêtres
 Vous pouvez *ancrer*les fenêtres de document et les fenêtres pour définir leur position et leur taille dans le cadre de la fenêtre IDE, ou les faire flotter sous forme de fenêtres distinctes indépendantes de l'IDE. Les fenêtres Outil peuvent être ancrées n'importe où dans le cadre de l'IDE ; certaines fenêtres Outil peuvent être ancrées sous forme de fenêtres à onglets dans le cadre de l'éditeur. Les fenêtres de document peuvent être ancrées dans le cadre de l'éditeur, et elles peuvent être épinglées à leur position actuelle dans l'ordre de tabulation. Vous pouvez ancrer plusieurs fenêtres pour les faire flotter ensemble dans un « rafting » par-dessus l'IDE ou en dehors de celui-ci. Il est aussi possible de masquer ou de minimiser les fenêtres.

 Vous pouvez organiser les fenêtres comme suit :

- épingler les fenêtres de document à gauche de la zone de configuration des onglets ;

- ancrer les fenêtres au cadre de modification sous forme d'onglets ;

- ancrer les fenêtres Outil au bord d'un cadre dans l'IDE ;

- faire flotter des fenêtres de document ou Outil par dessus l'IDE ou en dehors de celui-ci ;

- masquer les fenêtres Outil le long du bord de l'IDE ;

- afficher les fenêtres sur plusieurs écrans ;

- rétablir la position de la fenêtre selon la disposition par défaut ou une disposition personnalisée enregistrée.

  Pour réorganiser les fenêtres Outil et les fenêtres de document, vous pouvez les faire glisser, utiliser les commandes du menu **Fenêtre** ou encore cliquer avec le bouton droit sur la barre de titre de la fenêtre à réorganiser.

> [!NOTE]
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="docking-windows"></a>Ancrage des fenêtres
 Quand vous cliquez sur la barre de titre d'une fenêtre outil ou sur l'onglet de la fenêtre de document et que vous le faites glisser, un repère en forme de losange apparaît. Au cours de l'opération de glissement, quand le curseur de la souris se trouve sur l'une des flèches dans le losange, une zone grisée apparaît pour vous montrer où la fenêtre sera ancrée si vous relâchez le bouton de la souris à ce moment-là.

 Pour déplacer une fenêtre ancrable sans l'emboîter, appuyez sur la touche Ctrl pendant que vous faites glisser la fenêtre.

 Pour faire revenir une fenêtre Outil ou une fenêtre de document à son emplacement d'ancrage plus récent, appuyez sur **Ctrl** pendant que vous double-cliquez sur la barre de titre ou sur l'onglet de la fenêtre.

 L'illustration suivante montre le repère en forme de losange pour les fenêtres de document, celles-ci pouvant uniquement être ancrées dans le cadre de modification :

 ![Repère en forme de losange de la fenêtre de document](../ide/media/documentwindowguidediamonds.png "Documentwindowguidediamonds")

 Les fenêtres Outil peuvent être ancrées à un côté d'un cadre dans l'IDE ou dans le cadre de modification. Quand vous faites glisser une fenêtre Outil vers un autre emplacement, un repère en forme de losange apparaît pour vous aider à la réancrer facilement.

 Repère en forme de losange pour les fenêtres Outil

 ![Repère en forme de losange de la fenêtre d’outils](../ide/media/vs10guidediamond.png "VS10GuideDiamond")

 L'illustration suivante montre l'ancrage de l'Explorateur de solutions dans un nouvel emplacement indiqué par la zone ombrée bleue :

 ![Ancrage de l’Explorateur de solutions dans une nouvelle position](../ide/media/vs2015-dock-diamond.png "VS2015_Dock_diamond")

### <a name="closing-and-auto-hiding-tool-windows"></a>Fermeture et masquage automatique des fenêtres Outil
 Vous pouvez fermer une fenêtre Outil en cliquant sur le X dans le coin supérieur droit de la barre de titre. Pour rouvrir la fenêtre, utilisez le raccourci clavier correspondant ou la commande de menu. Les fenêtres Outil prennent en charge une fonctionnalité nommée Masquer automatiquement qui permet de faire disparaître une fenêtre quand vous utilisez une autre fenêtre. Quand une fenêtre est automatiquement masquée, son nom s'affiche sous un onglet au bord de l'IDE. Pour réutiliser la fenêtre, pointez sur l'onglet pour que la fenêtre soit de nouveau visible.

 ![Masquer automatiquement](../ide/media/vs2015-auto-hide.png "vs2015_auto_hide")

> [!NOTE]
>  Pour indiquer si la fonctionnalité Masquer automatiquement agit sur chaque fenêtre Outil ou sur des groupes de fenêtres ancrées, sélectionnez ou désélectionnez **Le bouton Masquer automatiquement n'affecte que la fenêtre Outil active** dans la boîte de dialogue **Options** . Pour plus d'informations, consultez [General, Environment, Options Dialog Box](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
>  Les fenêtres Outil automatiquement masquées peuvent s'afficher temporairement quand la fenêtre a le focus. Pour masquer à nouveau la fenêtre, sélectionnez un élément qui se trouve en dehors de la fenêtre active. Quand la fenêtre perd le focus, elle disparaît à nouveau.

### <a name="specifying-a-monitor"></a>Spécification d'un écran
 Si vous possédez un deuxième écran et que votre système d'exploitation le prend en charge, vous pouvez choisir celui qui affiche une fenêtre. Vous pouvez même regrouper plusieurs fenêtres en « raftings » sur d'autres écrans.

> [!TIP]
>  Vous pouvez créer plusieurs instances de l' **Explorateur de solutions** et les déplacer dans un autre écran. Cliquez avec le bouton droit sur la fenêtre et choisissez **Nouvelle vue Explorateur de solutions**. Vous pouvez faire revenir toutes les fenêtres sur l'écran d'origine en effectuant un double-clic tout en appuyant sur la touche Ctrl.

### <a name="reset-name-and-switch-between-window-layouts"></a>Rétablir les dispositions de fenêtres, changement de nom et basculement
 Vous pouvez faire revenir l'IDE à la disposition d'origine des fenêtres pour votre collection de paramètres à l'aide de la commande **Rétablir la disposition de fenêtre** . Quand vous exécutez cette commande, les actions suivantes se produisent :

-   Toutes les fenêtres sont déplacées vers leurs positions par défaut.

-   Les fenêtres qui sont fermées dans la disposition de fenêtre par défaut sont fermées.

-   Les fenêtres qui sont ouvertes dans la disposition de fenêtre par défaut sont ouvertes.

### <a name="create-and-save-custom-layouts"></a>Créer et enregistrer des dispositions personnalisées
 Avec Visual Studio 2015, vous pouvez enregistrer jusqu'à 10 dispositions de fenêtres personnalisées et passer rapidement de l'une à l'autre. Les étapes suivantes montrent comment créer, enregistrer, appeler et gérer des dispositions personnalisées qui tirent parti de plusieurs écrans avec des fenêtres d’outils ancrées et flottantes.

 Commencez par créer une solution de test qui comporte deux projets, chacun avec une disposition optimale différente.

##### <a name="create-a-ui-project-and-customize-the-layout"></a>Créer un projet d'interface utilisateur et personnaliser la disposition

1.  Dans la boîte de dialogue **Nouveau projet** , créez une application de bureau WPF Visual C# et donnez-lui un nom quelconque. Supposons que vous deviez travailler sur l'interface utilisateur de ce projet. Vous voulez donc maximiser l'espace de la fenêtre du concepteur et pousser les autres fenêtres d'outils à l'écart.

2.  Si vous avez plusieurs écrans, déplacez les fenêtres **Explorateur de solutions** et **Propriétés** sur votre deuxième écran. Dans un système à un seul écran, essayez de fermer toutes les fenêtres à l'exception de celle du concepteur.

3.  Appuyez sur **Ctrl + Alt + X** pour afficher la boîte à outils. Si la fenêtre est ancrée, faites-la glisser pour la faire flotter où vous le souhaitez sur l'un des deux écrans.

4.  Appuyez sur F5 pour configurer Visual Studio en mode débogage. Ajustez librement la position des fenêtres de débogage Auto, Pile des appels et Sortie. La disposition que vous allez créer s'applique à la fois au mode d'édition et au mode débogage.

5.  Quand vous êtes satisfait de vos dispositions dans les modes d’édition et débogage, accédez au menu principal et choisissez **Fenêtre > Enregistrer la disposition de fenêtre**. Appelez cette disposition « Concepteur ».

     Notez que le prochain raccourci clavier disponible dans la liste réservée (Ctrl + Alt + 1...0) est attribué à votre nouvelle disposition.

##### <a name="create-a-database-project-and-layout"></a>Créer un projet de base de données et une disposition

1.  Ajoutez un nouveau projet **Base de données SQL Server** à la solution.

2.  Cliquez avec le bouton droit sur le nouveau projet dans l'Explorateur de solutions et choisissez **Afficher dans l'Explorateur d'objets**. Dans la fenêtre **Explorateur d'objets SQL Server** qui s'affiche, vous pouvez accéder aux tables, vues et autres objets dans votre base de données. Vous pouvez soit faire flotter cette fenêtre ou la laisser ancrée. Ajustez librement les autres fenêtres d'outils. Pour plus de réalisme, vous pouvez ajouter une vraie base de données, mais cette étape n'est pas obligatoire dans cette procédure pas à pas.

3.  Quand vous êtes satisfait de votre disposition, accédez au menu principal et choisissez **Fenêtre > Enregistrer la disposition de fenêtre**. Nommez cette disposition « Projet BD ». (Nous n’allons pas nous ennuyer à créer une disposition pour le mode débogage dans ce projet.)

##### <a name="switch-between-the-layouts"></a>Basculer entre les dispositions

1.  Pour basculer entre les dispositions, utilisez les raccourcis clavier ou, dans le menu principal, choisissez **Fenêtre > Appliquer la disposition de fenêtre**.

     ![Menu appliquer la fenêtre disposition](../ide/media/vs2015-applywindowlayout.png "VS2015_ApplyWindowLayout")

     Une fois la disposition de l'interface utilisateur appliquée, notez qu'elle est préservée à la fois dans les modes d'édition et débogage.

     Si vous utilisez une configuration à plusieurs écrans au bureau et un ordinateur portable à un seul écran à la maison, vous pouvez créer des dispositions optimisées pour chaque ordinateur.

     Remarque : si vous appliquez une disposition à plusieurs écrans à un système à un seul écran, les fenêtres flottantes que vous avez placées sur le second écran sont alors masquées derrière la fenêtre Visual Studio. Pour faire passer ces fenêtres au premier plan, appuyez sur Alt + Tab. Si vous ouvrez par la suite Visual Studio avec plusieurs écrans, vous pouvez restaurer les positions spécifiées des fenêtres en réappliquant la disposition.

##### <a name="manage-and-roam-your-layouts"></a>Gérer vos dispositions et les rendre itinérantes

1.  Vous pouvez supprimer, renommer ou réorganiser votre disposition personnalisée en choisissant **Fenêtre > Gérer les dispositions de fenêtres**. Si vous déplacez une disposition, la combinaison de touches est automatiquement ajustée afin de refléter la nouvelle position dans la liste. Les combinaisons ne pouvant pas être modifiées autrement, vous ne pouvez stocker que 10 dispositions à la fois.

     ![Gérer les dispositions de fenêtres](../ide/media/managewindowlayouts.png "ManageWindowLayouts")

     Pour vous souvenir du raccourci clavier attribué à une disposition, choisissez **Fenêtre > Appliquer la disposition de fenêtre**.

     Ces dispositions sont automatiquement itinérantes entre les éditions de Visual Studio, entre les instances de Blend sur des ordinateurs distincts, mais aussi entre une édition Express quelconque et n'importe quelle autre organisation Express. Cependant, les dispositions ne sont pas itinérantes entre Visual Studio, Blend et Express.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Types de fenêtres](../misc/kinds-of-windows.md)|Discute les différences entre fenêtres Outil et les fenêtres de document dans l'IDE.|
|[Guide pratique pour Organiser et ancrer des fenêtres](../misc/how-to-arrange-and-dock-windows.md)|Explique comment ancrer les fenêtres, les masquer automatiquement et les disposer en mosaïque et également comment réinitialiser leur disposition.|
|[Guide pratique pour se déplacer dans l’IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)|Explique comment passer d'une fenêtre active à l'autre dans l'IDE, par ordre d'utilisation. Explique également comment passer à des documents spécifiques.|
|[Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)|Contient des informations sur les combinaisons de paramètres et sur l'utilisation de ces paramètres pour la disposition des fenêtres, les raccourcis clavier et autres éléments de l'IDE.|
