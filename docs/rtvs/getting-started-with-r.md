---
title: Didacticiel Bien démarrer avec R
description: Procédure pas à pas d’utilisation de R dans Visual Studio, y compris la création du projet, la fenêtre interactive, la modification du code et le débogage.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 83a4f4ea1add79ce0317ff5823066a0070a407c1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024095"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Bien démarrer avec Outils R pour Visual Studio

Après avoir installé Outils R pour Visual Studio (RTVS) (voir [Installation](installing-r-tools-for-visual-studio.md)), vous pouvez rapidement vous faire une idée de ce que ces outils ont à offrir.

## <a name="create-an-r-project"></a>Créer un projet R

1. Démarrez Visual Studio.
1. Choisissez **Fichier** > **Nouveau** > **Projet** (**Ctrl**+**Maj**+**N**)
1. Sélectionnez « Projet R » sous **Modèles** > **R**, donnez au projet un nom et un emplacement, puis sélectionnez **OK** :

   ![Boîte de dialogue Nouveau projet pour R dans Visual Studio (RTVS dans VS2017)](media/getting-started-01-new-project.png)

1. Une fois le projet créé, les fenêtres suivantes sont visibles :

    - L’Explorateur de solutions Visual Studio, situé à droite, comprend une *solution* qui contient votre projet. (Les solutions peuvent contenir un nombre quelconque de projets de types différents ; pour plus d’informations, consultez [Projets](r-projects-in-visual-studio.md)).
    - Un nouveau fichier R (`script.R`), situé en haut à gauche, vous permet de modifier le code source avec toutes les fonctionnalités d’édition de Visual Studio.
    - La fenêtre **R Interactive**, située en bas à gauche, vous permet de développer et de tester votre code de manière interactive.

> [!Note]
> Vous pouvez utiliser la fenêtre **R Interactive** si aucun projet n’est ouvert (et même si un type de projet différent est chargé). À tout moment, sélectionnez **Outils R** > **Fenêtres** > **R Interactive**.

## <a name="explore-the-interactive-window-and-intellisense"></a>Explorer la fenêtre interactive et IntelliSense

1. Pour vérifier que la fenêtre interactive fonctionne, tapez `3 + 4` et appuyez sur **Entrée** pour afficher le résultat :

    ![Fenêtre R Interactive dans Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Entrez une commande un peu plus compliquée, par exemple `ds <- c(1.5, 6.7, 8.9) * 1:12`, puis entrez `ds` pour afficher le résultat :

    ![Autre exemple interactif pour R dans Visual Studio](media/getting-started-03-interactive2.png)

1. Tapez `mean(ds)`. Notez que, dès que vous tapez `m` ou `me`, la fonctionnalité IntelliSense de Visual Studio propose des options de saisie semi-automatique. Après avoir sélectionné la saisie semi-automatique désirée dans la liste, appuyez sur **Tab** pour l’insérer. Vous pouvez changer de sélection à l’aide de la souris ou des touches de direction.

    ![Apparition d’IntelliSense quand vous entrez du code](media/getting-started-04-intellisense1.png)

1. Une fois la saisie de `mean` terminée, tapez la parenthèse ouvrante `(` et notez l’aide en ligne que vous propose IntelliSense pour la fonction :

    ![IntelliSense affichant de l’aide pour une fonction](media/getting-started-05-intellisense2.png)

1. Terminez la saisie de la ligne `mean(ds)` et appuyez sur Entrée pour afficher le résultat (`[1] 39.51667`).

1. La fenêtre interactive est intégrée à l’aide. Par exemple, entrez `?mean` pour afficher de l’aide pour cette fonction dans la fenêtre **Aide R** de Visual Studio. Pour plus d’informations, consultez [Aide dans les outils R pour Visual Studio](getting-started-help.md).

    ![Fenêtre d’aide R dans Visual Studio](media/getting-started-06-help.png)

1. Certaines commandes, telles que `plot(1:100)`, ouvrent une nouvelle fenêtre dans Visual Studio quand la sortie ne peut pas être affichée directement dans la fenêtre interactive :

    ![Affichage d’un tracé dans Visual Studio](media/getting-started-07-plot-window.png)

La fenêtre interactive vous permet également de passer en revue votre historique, de charger et d’enregistrer des espaces de travail, d’attacher un débogueur et d’interagir avec des fichiers de code source au lieu d’effectuer des opérations de copier-coller. Pour plus d’informations, consultez [Utilisation de la fenêtre interactive R](interactive-repl-for-r-in-visual-studio.md).

## <a name="experience-code-editing-features"></a>Découvrir les fonctionnalités de modification du code

En utilisant brièvement la fenêtre interactive, vous avez pu découvrir des fonctionnalités de modification de base, comme IntelliSense, qui fonctionnent aussi dans l’éditeur de code. Si vous entrez le même code que précédemment, les invites de saisie semi-automatique et IntelliSense affichées sont les mêmes, mais la sortie n’est pas visible.

Le fait d’écrire du code dans un fichier *.R* vous permet de voir tout votre code à la fois, ce qui facilite l’apport de modifications mineures et l’affichage rapide des résultats en exécutant le code dans la fenêtre interactive. Notez aussi qu’un projet peut contenir autant de fichiers que vous le souhaitez. Quand le code se trouve dans un fichier, vous pouvez également l’exécuter pas à pas dans le débogueur (comme nous le verrons plus tard dans cet article). Ces fonctionnalités s’avèrent utiles quand vous développez des algorithmes de calcul et que vous écrivez du code pour manipuler un ou plusieurs datasets, surtout quand vous souhaitez examiner tous les résultats intermédiaires.

Par exemple, les étapes suivantes créent un petit extrait de code pour explorer le [théorème central limite](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipédia). (Cet exemple est tiré du livre *R Cookbook* de Paul Teetor.)

1. Dans l’éditeur `script.R`, entrez le code suivant :

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Pour afficher rapidement les résultats, sélectionnez tout le code (**Ctrl**+**A**), puis appuyez sur **Ctrl**+**Entrée** ou cliquez avec le bouton droit et sélectionnez **Exécuter en mode interactif**. Tout le code sélectionné est exécuté dans la fenêtre interactive comme si vous l’aviez tapé directement. Le résultat s’affiche dans une fenêtre de tracés :

    ![Affichage d’un tracé dans Visual Studio](media/getting-started-08-plot1.png)

1. Pour une ligne unique, appuyez simplement sur **Ctrl**+**Entrée** à tout moment pour l’exécuter dans la fenêtre interactive.

> [!Tip]
> Nous vous recommandons d’apporter des modifications et d’appuyer sur **Ctrl**+**Entrée** pour exécuter rapidement le code. Vous pouvez aussi sélectionner tout votre code avec **Ctrl**+**A**, puis appuyer sur **Ctrl**+**Entrée**. Sur des opérations identiques, vous obtiendrez de meilleurs résultats qu’avec la souris.
>
> Par ailleurs, vous pouvez faire glisser et déplacer la fenêtre de tracés à l’extérieur du cadre de Visual Studio et placer tout autre élément désiré sur votre écran. Vous pouvez ensuite redimensionner la fenêtre de tracés à la taille souhaitée, puis l’enregistrer dans un fichier image ou PDF.

1. Ajoutez quelques lignes de code pour inclure un second tracé :

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Appuyez une nouvelle fois sur **Ctrl**+**A** et **Ctrl**+**Entrée** pour exécuter le code, et obtenir le résultat suivant :

    ![Tracé double mis à jour dans Visual Studio](media/getting-started-09-plot2.png)

1. Le problème, c’est que le premier tracé détermine l’échelle verticale et qu’il ne reste pas assez de place pour le second (avec `lines`). Pour corriger ce problème, nous devons définir le paramètre `ylim` sur l’appel `plot`. Cependant, pour bien faire, nous devons ajouter du code pour calculer la valeur verticale maximale. Le fait de procéder ligne par ligne dans la fenêtre interactive est peu pratique, car nous devons réorganiser le code pour utiliser `samp.means` avant d’appeler `plot`. Cependant, dans un fichier de code, nous pouvons apporter facilement les modifications appropriées :

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. Appuyez sur **Ctrl**+**A** et **Ctrl**+**Entrée** une nouvelle fois pour afficher le résultat :

    ![Tracé double mis à jour dans Visual Studio, mis à l’échelle correctement](media/getting-started-10-plot3.png)

L’éditeur offre bien d’autres fonctionnalités. Pour plus d’informations, consultez [Modifier le code R](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md) et [Extraits de code](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Déboguer votre code

L’un des atouts de Visual Studio est son interface utilisateur de débogage. Reposant sur cette fondation solide, RTVS ajoute des éléments d’interface utilisateur novateurs comme [l’explorateur de variables](variable-explorer.md). Ici, nous allons examiner succinctement le débogage.

1. Pour commencer, utilisez la commande de menu **Outils R** > **Session** > **Réinitialiser** pour réinitialiser l’espace de travail actuel et effacer tout ce que vous avez fait jusqu’à présent. Par défaut, toutes les actions que vous réalisez dans la fenêtre interactive sont ajoutées à la session active, celle-ci étant ensuite utilisée par le débogueur. La réinitialisation de la session vous permet de démarrer la session de débogage sans données préexistantes. Toutefois, la commande **Réinitialiser** n’affecte pas votre fichier source *script.R*, car celui-ci est géré et enregistré en dehors de l’espace de travail.

1. Dans le fichier *script.R* créé dans la section précédente, définissez un point d’arrêt sur la ligne qui commence par `pop <-`. Pour cela, placez le signe insertion sur cette ligne et appuyez sur **F9**, ou sélectionnez la commande de menu **Déboguer** > **Point d’arrêt**. Sinon, cliquez simplement dans la marge de gauche (ou gouttière) de cette ligne où se trouve le point d’arrêt rouge :

    ![Définition d’un point d’arrêt dans l’éditeur](media/getting-started-11-debug1.png)

1. Lancez le débogueur avec le code dans *script.R.* Pour cela, trois options s’offrent à vous : sélectionnez le bouton **Fichier de démarrage source** dans la barre d’outils, sélectionnez l’élément de menu **Déboguer** > **Fichier de démarrage source** ou appuyez sur **F5**. Visual Studio entre en mode débogage et démarre l’exécution du code. Toutefois, il s’arrête sur la ligne où vous avez défini le point d’arrêt :

    ![Arrêt sur un point d’arrêt dans le débogueur Visual Studio](media/getting-started-12-debug2.png)

1. Durant le débogage, Visual Studio vous permet d’avancer dans votre code ligne par ligne. Vous pouvez aussi effectuer un pas à pas détaillé dans les fonctions, effectuer un pas à pas principal sur celles-ci ou encore effectuer un pas à pas sortant pour accéder au contexte d’appel. Ces fonctionnalités, ainsi que d’autres, sont disponibles dans le menu **Déboguer**, le menu contextuel dans l’éditeur et la barre d’outils de débogage :

    ![Barre d’outils de débogage dans Visual Studio](media/getting-started-13-debug3.png)

1. Quand l’exécution est arrêtée au niveau d’un point d’arrêt, vous pouvez examiner les valeurs des variables. Recherchez la fenêtre **Automatique** dans Visual Studio et sélectionnez l’onglet dans la partie inférieure nommé **Variables locales**. La fenêtre **Variables locales** affiche les variables locales au niveau du point actif dans le programme. Si vous êtes arrêté sur le point d’arrêt défini précédemment, vous pouvez constater que la variable `pop` n’est pas encore définie. Utilisez maintenant la commande **Déboguer** > **Pas à pas principal** (**F10**) pour afficher la valeur de `pop` :

    ![Fenêtre Variables locales dans Visual Studio](media/getting-started-14-debug4.png)

1. Pour examiner des variables dans des portées différentes, notamment la portée globale et les portées de package, utilisez l’[Explorateur de variables](variable-explorer.md). L’Explorateur de variables vous permet également de passer à une vue tabulaire composée de colonnes pouvant être triées et d’exporter les données dans un fichier CSV.

    ![Vue développée de l’Explorateur de variables](media/variable-explorer-expanded-results.png)

1. Vous pouvez soit continuer à exécuter pas à pas le programme, soit sélectionner **Continuer** (**F5**) pour l’exécuter jusqu’à sa complétion (ou jusqu’au point d’arrêt suivant).

Pour aller plus loin, consultez [Débogage](debugging-r-in-visual-studio.md) et [Explorateur de variables](variable-explorer.md).

## <a name="next-steps"></a>Étapes suivantes

Dans cette procédure pas à pas, vous avez pu découvrir les bases des projets R. Vous avez aussi appris à utiliser la fenêtre interactive, à modifier du code et à déboguer dans Visual Studio. Pour explorer d’autres fonctionnalités, consultez les articles suivants, ainsi que ceux figurant dans la table des matières :

- [Exemples de projet](getting-started-samples.md)
- [Modification du code](editing-r-code-in-visual-studio.md)
- [Débogage](debugging-r-in-visual-studio.md)
- [Espaces de travail](r-workspaces-in-visual-studio.md)
- [Visualisation des données](visualizing-data-with-r-in-visual-studio.md)
