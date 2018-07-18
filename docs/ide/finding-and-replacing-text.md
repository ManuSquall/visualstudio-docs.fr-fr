---
title: Rechercher et remplacer du texte
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
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
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7051b90dde45965b76e8a9e08b33b5326ff2848c
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106750"
---
# <a name="find-and-replace-text"></a>Rechercher et remplacer du texte

Vous pouvez rechercher et remplacer du texte dans l’éditeur Visual Studio avec [Rechercher et remplacer](#find-and-replace-control) ou [Rechercher/remplacer dans les fichiers](#find-in-files-and-replace-in-files).

> [!TIP]
> Si vous renommez des symboles du code comme des variables et des méthodes, il est préférable de les *[refactoriser](../ide/reference/rename.md)* au lieu d’utiliser Rechercher et remplacer. La refactorisation fonctionne de façon intelligente et comprend la notion d’étendue, alors que Rechercher et remplacer remplace aveuglément toutes les instances.

La fonctionnalité Rechercher et remplacer est disponible dans l’éditeur, dans certaines autres fenêtres de texte, comme **Résultats de la recherche**, dans des fenêtres de concepteur, comme le concepteur XAML et le concepteur Windows Forms, et dans des fenêtres d’outils.

Vous pouvez limiter les recherches au document actif, à la solution actuelle ou à un ensemble de dossiers personnalisé. Vous pouvez également spécifier un ensemble d’extensions de nom de fichier pour les recherches multifichiers. Personnalisez la syntaxe de recherche avec des [expressions régulières](../ide/using-regular-expressions-in-visual-studio.md) .NET.

> [!TIP]
> La zone [Rechercher/Commande](../ide/find-command-box.md) est disponible en tant que contrôle de barre d’outils, mais par défaut, elle n’est pas visible. Pour afficher la zone **Rechercher/Commande**, sélectionnez **Ajouter ou supprimer des boutons** dans la barre d’outils **Standard**, puis sélectionnez **Rechercher**.

## <a name="find-and-replace-control"></a>Contrôle Rechercher et remplacer

Le contrôle **Rechercher et remplacer** s’affiche dans le coin supérieur droit de la fenêtre de l’éditeur de code. Le contrôle **Rechercher et remplacer** met immédiatement en surbrillance chaque occurrence de la chaîne de recherche donnée dans le document actif. Vous pouvez passer d’une occurrence à une autre en choisissant le bouton **Suivant** ou **Précédent** sur le contrôle de recherche.

![Contrôle Rechercher et remplacer](media/find-and-replace-box.png)

Vous pouvez accéder aux options de remplacement en choisissant le bouton en regard de la zone de texte **Rechercher**. Pour effectuer un remplacement à la fois, choisissez le bouton **Suivant** en regard de la zone de texte **Remplacer**. Pour remplacer toutes les occurrences en une seule fois, choisissez le bouton **Remplacer tout**.

Pour modifier la couleur de surbrillance des correspondances, choisissez le menu **Outils**, sélectionnez **Options**, puis choisissez **Environnement** et sélectionnez **Polices et couleurs**. Dans la liste **Afficher les paramètres de**, sélectionnez **Éditeur de texte**, puis, dans la liste **Éléments d’affichage**, sélectionnez **Rechercher un surlignage (extension)**.

### <a name="search-tool-windows"></a>Fenêtres des outils de recherche

Vous pouvez utiliser la commande **Rechercher** dans les fenêtres de code ou de texte, comme les fenêtres **Sortie** et les fenêtres **Résultats de la recherche**, en sélectionnant **Edition** > **Rechercher et remplacer** ou en appuyant sur **Ctrl+F**.

Une version de la commande **Rechercher** est également disponible dans certaines fenêtres d’outils. Par exemple, vous pouvez filtrer la liste des contrôles dans la fenêtre **Boîte à outils** en entrant du texte dans la zone de recherche. **L’Explorateur de solutions**, la fenêtre **Propriétés** et **Team Explorer** sont d’autres fenêtres d’outils qui vous permettent de faire des recherches dans leur contenu.

## <a name="find-in-files-and-replace-in-files"></a>Rechercher dans les fichiers et remplacer dans les fichiers

L’option **Rechercher/Remplacer dans les fichiers** fonctionne comme le contrôle **Rechercher et remplacer**, à ceci près que vous pouvez définir une étendue de recherche. Vous pouvez non seulement rechercher dans le fichier actif ouvert dans l’éditeur, mais aussi rechercher dans tous les documents ouverts, dans la solution complète, dans le projet actif et dans des jeux de dossiers sélectionnés. Vous pouvez également effectuer une recherche basée sur une extension de nom de fichier. Pour accéder à la boîte de dialogue **Rechercher/Remplacer dans les fichiers**, sélectionnez **Rechercher et remplacer** dans le menu **Edition** ou appuyez sur **Ctrl+Maj+F**.

![Rechercher dans les fichiers (boîte de dialogue)](media/find-in-files-box.png)

### <a name="find-results"></a>Résultats de la recherche

Lorsque vous choisissez **Rechercher tout**, une fenêtre **Résultats de la recherche** s’ouvre et répertorie les résultats de la recherche. Si vous sélectionnez un résultat dans la liste, le fichier associé est affiché et la correspondance est mise en surbrillance. Si le fichier n’est pas encore ouvert pour modification, il est ouvert dans un onglet d’aperçu dans la partie droite de la zone de configuration des onglets. Vous pouvez utiliser le contrôle **Rechercher** pour effectuer des recherches dans la liste **Résultats de la recherche**.

### <a name="create-custom-search-folder-sets"></a>Créer des jeux de dossiers de recherche personnalisés

Vous pouvez définir une étendue de recherche en choisissant le bouton **Choisir des dossiers de recherche** (il ressemble à **...**) en regard de la zone **Regarder dans**. Dans la boîte de dialogue **Choisir des dossiers de recherche**, vous pouvez spécifier un jeu de dossiers où effectuer la recherche, et vous pouvez enregistrer la spécification pour pouvoir la réutiliser plus tard.

> [!TIP]
> Si vous avez mappé le lecteur d’un ordinateur distant à votre ordinateur local, vous pouvez spécifier les dossiers pour la recherche sur l’ordinateur distant.

### <a name="create-custom-component-sets"></a>Créer des jeux de composants personnalisés

Vous pouvez définir des jeux de composants comme étendue de recherche en choisissant le bouton **Modifier un jeu de composants personnalisés** en regard de la zone **Regarder dans**. Vous pouvez spécifier des composants .NET ou COM installés, des projets Visual Studio inclus dans votre solution ou toute bibliothèque d’assemblys ou de types (*.dll*, *.tlb*, *.olb*, *.exe* ou *.ocx*). Pour rechercher des références, cochez la case **Regarder dans les références**.

## <a name="see-also"></a>Voir aussi

- [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refactoriser le code dans Visual Studio](../ide/refactoring-in-visual-studio.md)