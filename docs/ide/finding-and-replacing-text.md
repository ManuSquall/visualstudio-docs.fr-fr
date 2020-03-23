---
title: Rechercher et remplacer du texte, et sélection avec signes insertion multiples
ms.date: 08/14/2018
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc31a0d0e2b6878b5dd5173a35ce4f538e135be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590343"
---
# <a name="find-and-replace-text"></a>Rechercher et remplacer du texte

Vous pouvez rechercher et remplacer du texte dans l’éditeur Visual Studio avec [Rechercher et remplacer](#find-and-replace-control) (**Ctrl**+**F** ou **Ctrl**+**H**) ou [Rechercher/remplacer dans les fichiers](#find-in-files-and-replace-in-files) (**Ctrl**+**Maj**+**F** ou **Ctrl**+**Maj**+**H**). Vous pouvez également rechercher et remplacer uniquement *certaines* instances d’un modèle à l’aide de la *[sélection avec signes insertion multiples](#multi-caret-selection)*.

> [!TIP]
> Si vous renommez des symboles du code comme des variables et des méthodes, il est préférable de les *[refactoriser](../ide/reference/rename.md)* au lieu d’utiliser Rechercher et remplacer. La refactorisation fonctionne de façon intelligente et comprend la notion d’étendue, alors que Rechercher et remplacer remplace aveuglément toutes les instances.

La fonctionnalité Rechercher et remplacer est disponible dans l’éditeur, dans certaines autres fenêtres de texte, comme **Résultats de la recherche**, dans des fenêtres de concepteur, comme le concepteur XAML et le concepteur Windows Forms, et dans des fenêtres d’outils.

Vous pouvez limiter les recherches au document actif, à la solution actuelle ou à un ensemble de dossiers personnalisé. Vous pouvez également spécifier un ensemble d’extensions de nom de fichier pour les recherches multifichiers. Personnalisez la syntaxe de recherche avec des [expressions régulières](../ide/using-regular-expressions-in-visual-studio.md) .NET.

> [!TIP]
> La zone [Rechercher/Commande](../ide/find-command-box.md) est disponible en tant que contrôle de barre d’outils, mais par défaut, elle n’est pas visible. Pour afficher la zone **Rechercher/Commande**, sélectionnez **Ajouter ou supprimer des boutons** dans la barre d’outils **Standard**, puis sélectionnez **Rechercher**.

## <a name="find-and-replace-control"></a>Contrôle Rechercher et remplacer

- Appuyez sur **Ctrl**+**F** comme un raccourci pour *trouver* une corde dans le fichier actuel.
- Appuyez sur **Ctrl**+**H** comme un raccourci pour trouver *et remplacer* une chaîne dans le fichier actuel.

Le contrôle **Rechercher et remplacer** s’affiche dans le coin supérieur droit de la fenêtre de l’éditeur de code. Il met immédiatement en surbrillance chaque occurrence de la chaîne de recherche donnée dans le document actif. Vous pouvez passer d’une occurrence à une autre en choisissant le bouton **Suivant** ou **Précédent** sur le contrôle de recherche.

![Rechercher et remplacer dans Visual Studio](media/find-and-replace-box.png)

Vous pouvez accéder aux options de remplacement en choisissant le bouton en regard de la zone de texte **Rechercher**. Pour effectuer un remplacement à la fois, choisissez le bouton **Suivant** en regard de la zone de texte **Remplacer**. Pour remplacer tous les matchs, choisissez le bouton **Remplacer tous.**

Pour modifier la couleur de surbrillance des correspondances, choisissez le menu **Outils**, sélectionnez **Options**, puis choisissez **Environnement** et sélectionnez **Polices et couleurs**. Dans la liste **Afficher les paramètres de**, sélectionnez **Éditeur de texte**, puis, dans la liste **Éléments d’affichage**, sélectionnez **Rechercher un surlignage (extension)**.

### <a name="search-tool-windows"></a>Fenêtres des outils de recherche

Vous pouvez utiliser la commande **Rechercher** dans les fenêtres de code ou de texte, comme les fenêtres **Sortie** et les fenêtres **Résultats de la recherche**, en sélectionnant **Edition** > **Rechercher et remplacer** ou en appuyant sur **Ctrl+F**.

Une version du contrôle **Trouver** est également disponible dans certaines fenêtres d’outils. Par exemple, vous pouvez filtrer la liste des contrôles dans la fenêtre **Boîte à outils** en entrant du texte dans la zone de recherche. **L’Explorateur de solutions**, la fenêtre **Propriétés** et **Team Explorer** sont d’autres fenêtres d’outils qui vous permettent de faire des recherches dans leur contenu.

## <a name="find-in-files-and-replace-in-files"></a>Rechercher dans les fichiers et remplacer dans les fichiers

- Appuyez sur **Ctrl**+**Shift**+**F** comme un raccourci pour *trouver* une chaîne dans plusieurs fichiers.
- Appuyez sur **Ctrl**+**Shift**+**H** comme un raccourci pour trouver *et remplacer* une chaîne dans plusieurs fichiers.

L’option **Rechercher/Remplacer dans les fichiers** fonctionne comme le contrôle **Rechercher et remplacer**, à ceci près que vous pouvez définir une étendue de recherche. Vous pouvez non seulement rechercher dans le fichier actif ouvert dans l’éditeur, mais aussi rechercher dans tous les documents ouverts, dans la solution complète, dans le projet actif et dans des jeux de dossiers sélectionnés. Vous pouvez également effectuer une recherche basée sur une extension de nom de fichier. Pour accéder à la boîte de dialogue **Rechercher/Remplacer dans les fichiers**, sélectionnez **Rechercher et remplacer** dans le menu **Edition** (ou appuyez sur **Ctrl**+**Maj**+**F**).

![Rechercher dans des fichiers dans Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Résultats de la recherche

Lorsque vous choisissez **Rechercher tout**, une fenêtre **Résultats de la recherche** s’ouvre et répertorie les résultats de la recherche. Si vous sélectionnez un résultat dans la liste, le fichier associé est affiché et la correspondance est mise en surbrillance. Si le fichier n’est pas encore ouvert pour modification, il est ouvert dans un onglet d’aperçu dans la partie droite de la zone de configuration des onglets. Vous pouvez utiliser le contrôle **Rechercher** pour effectuer des recherches dans la liste **Résultats de la recherche**.

### <a name="create-custom-search-folder-sets"></a>Créer des jeux de dossiers de recherche personnalisés

Vous pouvez définir une portée de recherche en choisissant le bouton **Choisissez les dossiers de recherche** (il ressemble à **...**) à côté de la **look dans** la boîte. Dans la boîte de dialogue **Choisir des dossiers de recherche**, vous pouvez spécifier un jeu de dossiers où effectuer la recherche, et vous pouvez enregistrer la spécification pour pouvoir la réutiliser plus tard.

> [!TIP]
> Si vous avez mappé le lecteur d’un ordinateur distant à votre ordinateur local, vous pouvez spécifier les dossiers pour la recherche sur l’ordinateur distant.

### <a name="create-custom-component-sets"></a>Créer des jeux de composants personnalisés

Vous pouvez définir des jeux de composants comme étendue de recherche en choisissant le bouton **Modifier un jeu de composants personnalisés** en regard de la zone **Regarder dans**. Vous pouvez spécifier des composants .NET ou COM installés, des projets Visual Studio inclus dans votre solution ou toute bibliothèque d’assemblys ou de types (*.dll*, *.tlb*, *.olb*, *.exe* ou *.ocx*). Pour rechercher des références, cochez la case **Regarder dans les références**.

## <a name="multi-caret-selection"></a>Sélection avec signes insertion multiples

> [!NOTE]
> Cette section s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Sélection de bloc](/visualstudio/mac/block-selection).

**Introduite dans Visual Studio 2017 version 15.8**

Utilisez la *sélection avec signes insertion multiples* pour effectuer la même modification à plusieurs endroits à la fois. Par exemple, vous pouvez insérer le même texte ou modifier du texte existant à plusieurs emplacements en même temps.

Dans la capture d’écran suivante, `-0000` est sélectionné à trois emplacements. Si l’utilisateur appuie sur **Supprimer**, les trois sélections sont supprimées :

![Sélection avec signes insertion multiples dans un fichier XML au sein de Visual Studio](media/multi-caret-selection.png)

Pour sélectionner plusieurs points d’insertion, cliquez ou effectuez votre première sélection de texte comme d’habitude, puis appuyez sur **Alt** tout en cliquant ou en sélectionnant du texte dans chaque emplacement supplémentaire. Vous pouvez également ajouter automatiquement le texte correspondant sous forme de sélections supplémentaires, ou sélectionner une zone de texte à modifier de manière identique sur chaque ligne.

> [!TIP]
> Si vous avez sélectionné **Alt** comme touche de modification pour la fonctionnalité Atteindre la définition avec un clic de souris dans **Outils** > **Options**, la sélection avec signes insertion multiples est désactivée.

### <a name="commands"></a>Commandes

Utilisez les touches et actions suivantes pour les comportements de la sélection avec signes insertion multiples :

|Raccourci|Action|
|-|-|
|**Ctrl**+**Alt** - cliquez sur|Ajouter un point d’insertion secondaire|
|**Ctrl**+**Alt** - double-clic|Ajouter une sélection de mot secondaire|
|**Ctrl**+**Alt** - cliquez sur ' glisser|Ajouter une sélection secondaire|
|**Shift**+**Alt**+**.**|Ajouter le prochain texte correspondant en tant que sélection|
|**Ctrl**+**Shift**+**Alt**+**,**|Ajouter tout le texte correspondant en tant que sélections|
|**Shift**+**Alt**+**,**|Supprimer la dernière occurrence sélectionnée|
|**Ctrl**+**Shift**+**Alt**+**.**|Ignorer la prochaine occurrence correspondante|
|**Alt** + clic|Ajouter une sélection de zone|
|**Échap** ou clic|Effacer toutes les sélections|

Certaines des commandes sont également disponibles dans le menu **Edition**, sous **Signes insertion multiples** :

![Menu volant Signes insertion multiples dans Visual Studio](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Voir aussi

- [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refactoriser le code dans Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Sélection de bloc (Visual Studio pour Mac)](/visualstudio/mac/block-selection)
