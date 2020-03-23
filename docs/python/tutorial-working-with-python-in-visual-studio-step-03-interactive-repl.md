---
title: Tutoriel Python dans Visual Studio - étape 3, REPL interactif
titleSuffix: ''
description: Étape 3 d’une procédure pas à pas portant sur les fonctionnalités de Python dans Visual Studio qui présente la fenêtre REPL interactive de Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 51723d22cd72de8333fca9b83c1643117a7413e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72986227"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Étape 3 : Utiliser la fenêtre REPL interactive

**Étape précédente :[ Écrire et exécuter du code](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

La fenêtre Visual Studio **Interactive** pour Python offre une riche expérience de lecture-évaluation-impression-boucle (REPL) qui raccourcit considérablement le cycle habituel de montage-build-debug. La fenêtre **Interactive** offre toutes les capacités de l’expérience REPL de la ligne de commande Python. Elle facilite également l’échange de code avec des fichiers sources dans l’éditeur Visual Studio, qui sans cela serait fastidieux avec la ligne de commande.

> [!NOTE]
> Pour les problèmes liés à REPL, vérifiez que les packages `ipython` et `ipykernel` sont installés. Pour obtenir de l’aide sur l’installation des packages, consultez [Onglet packages, Environnements Python](/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab).

1. Ouvrez la fenêtre **Interactive** en cliquant à droite sur l’environnement Python du projet dans **Solution Explorer** (comme **Python 3.6 (32 bits)** montré dans un graphique antérieur) et en sélectionnant **Open Interactive Window**. Vous pouvez sélectionner alternativement **View** > **Other Windows** > **Python Interactive Windows** à partir du menu principal Visual Studio.

1. La fenêtre **Interactive** s’ouvre **>>>** en dessous de l’éditeur avec l’invite Python REPL standard. La liste déroulante **Environnement** vous permet de sélectionner un interpréteur spécifique à utiliser. Souvent, vous voulez également rendre la fenêtre **interactive** plus grande, ce que vous pouvez faire en faisant glisser le séparateur entre les deux fenêtres:

    ![Fenêtre interactive de Python - redimensionnement par glissement](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Vous pouvez redimensionner toutes les autres fenêtres de Visual Studio en faisant glisser les séparateurs adjacents. Vous pouvez également faire glisser des fenêtres indépendamment du cadre principal de Visual Studio et les réorganiser comme vous le souhaitez dans ce cadre. Pour plus d’informations, consultez [Personnaliser les dispositions de fenêtres](../ide/customizing-window-layouts-in-visual-studio.md).

1. Entrez quelques instructions comme `print("Hello, Visual Studio")`, et des expressions comme `123/456` pour voir les résultats immédiats :

    ![Résultats immédiats de la fenêtre interactive Python](media/vs-getting-started-python-12-interactive2.png)

1. Quand vous commencez à écrire une instruction multiligne, par exemple une définition de fonction, la fenêtre **Interactive** affiche l’invite **...** de Python pour continuer les lignes, ce qui, contrairement à l’environnement en ligne de commande REPL, entraîne une mise en retrait automatique :

    ![Fenêtre interactive Python avec poursuite de l’instruction](media/vs-getting-started-python-13-interactive3.png)

1. La fenêtre **Interactive** fournit une histoire complète de tout ce que vous avez inscrit, et améliore la ligne de commande REPL avec des éléments d’historique multilingorifaux. Par exemple, vous pouvez facilement rappeler l’ensemble de la définition de la fonction `f` ci-dessus comme un tout, puis la renommer `make_double`, sans avoir à recréer la fonction ligne par ligne.

1. Visual Studio peut envoyer plusieurs lignes de code d’une fenêtre d’éditeur à la fenêtre **Interactive.** Cette capacité vous permet de maintenir le code dans un fichier source et d’envoyer facilement certaines parties de celui-ci à la fenêtre **Interactive.** Vous pouvez ensuite travailler avec ces fragments de code dans l’environnement rapide REPL au lieu d’avoir à exécuter la totalité du programme. Pour voir cette fonctionnalité, remplacez d’abord la boucle `for` dans le fichier *PythonApplication1.py* par ceci :

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Sélectionnez `import` `from`les `make_dot_string` relevés , et fonction dans le fichier *.py,* clic droit, et sélectionnez **Envoyer à Interactive** (ou appuyez sur **Ctrl**+**Enter**). Le fragment de code est immédiatement collé dans la fenêtre **interactive** et exécuté. Parce que le code a défini une fonction, vous pouvez tester rapidement cette fonction en l’appelant à quelques reprises :

    ![Envoi de code dans la fenêtre interactive et test de ce code](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > L’utilisation **de Ctrl**+**Entrez** dans l’éditeur *sans* une sélection exécute la ligne de code actuelle dans la fenêtre **Interactive** et place automatiquement le caret sur la ligne suivante. Avec cette fonctionnalité, appuyer **sur Ctrl**+**Enter** fournit à plusieurs reprises un moyen pratique de passer à travers votre code qui n’est pas possible avec seulement la ligne de commande Python. Elle vous permet également de parcourir votre code pas à pas sans exécuter le débogueur et sans nécessairement démarrer votre programme à partir du début.

1. Vous pouvez également copier et coller plusieurs lignes de code dans la fenêtre **Interactive** de n’importe quelle source, comme l’extrait ci-dessous, ce qui est difficile à faire avec le Python commande-ligne REPL. Lorsqu’elle est collée, la fenêtre **Interactive** exécute ce code comme si vous l’aviez tapé dans :

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Collage de plusieurs lignes de code à l’aide de la commande Envoyer vers Interactive](media/vs-getting-started-python-15-interactive5.png)

1. Comme vous pouvez le voir, ce code fonctionne correctement, mais sa sortie n’est pas très intéressante. Une valeur différente pour le pas de la boucle `for` montrerait une partie plus importante de la courbe de la fonction cosinus. Heureusement, comme la totalité de la boucle `for` se trouve dans l’historique REPL comme un tout, vous pouvez facilement revenir en arrière et apporter les modifications souhaitées, puis tester à nouveau la fonction. Appuyez sur la flèche vers le haut pour d’abord rappeler la boucle `for`. Appuyez ensuite sur les flèches gauche ou droite pour parcourir le code (tant que vous le faites, les flèches haut et bas continuent de boucler dans l’historique). Accédez à la spécification `range` et changez-la en `range(0, 360, 12)`. Ensuite, appuyez sur **Ctrl**+**Enter** (n’importe où dans le code) pour exécuter l’ensemble de la déclaration à nouveau:

    ![Modification d’une instruction précédente dans la fenêtre interactive](media/vs-getting-started-python-16-interactive6.png)

1. Répétez le processus pour faire des essais avec différentes valeurs de pas jusqu’à trouver la valeur que vous préférez. Vous pouvez également faire en sorte que la courbe se répète en augmentant la plage, par exemple `range(0, 1800, 12)`.

1. Lorsque vous êtes satisfait du code, vous êtes écrit dans la fenêtre **Interactive,** sélectionnez-le, cliquez à droite et sélectionnez **Copy Code** (**Ctrl**+**Shift**+**C**), puis collez dans l’éditeur. Notez que cette fonctionnalité spéciale de Visual Studio ne produit aucune sortie, ni les invites `>>>` et `...`. Par exemple, l’image ci-dessous montre l’utilisation de la commande **Copier le code** sur une sélection qui inclut des invites et une sortie :

    ![La commande de copie de code de la fenêtre interactive sur une sélection avec des invites et une sortie](media/vs-getting-started-python-17-interactive7.png)

    Quand vous collez dans l’éditeur, vous obtenez seulement le code :

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Si vous souhaitez copier le contenu exact de la fenêtre **Interactive,** y compris les invites et la sortie, il suffit d’utiliser la commande **Copy** standard.

1. Ce que vous venez de faire est d’utiliser l’environnement REPL rapide de la fenêtre **Interactive** pour travailler sur les détails d’un petit morceau de code, puis vous avez commodément ajouté ce code au fichier source de votre projet. Lorsque vous exécutez maintenant le code à nouveau avec **Ctrl**+**F5** (ou **Debug** > **Start sans Debugging**), vous voyez les résultats exacts que vous vouliez.

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Exécuter du code dans le débogueur](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Approfondir la question

- [Utiliser la fenêtre Interactive](python-interactive-repl-in-visual-studio.md)
- [Utiliser l’environnement REPL IPython](interactive-repl-ipython.md)
