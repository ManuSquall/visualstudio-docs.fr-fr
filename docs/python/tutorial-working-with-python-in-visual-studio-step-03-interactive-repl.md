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
ms.openlocfilehash: 7b2de511b0d24df9c4e156ccef37ff053005af98
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450445"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Étape 3 : Utiliser la fenêtre REPL interactive

**Étape précédente :[ Écrire et exécuter du code](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

La fenêtre **Interactive** de Visual Studio pour Python offre une expérience utilisateur REPL (read-evaluate-print-loop) intéressante, qui réduit considérablement le cycle habituel de modification-génération-débogage. La fenêtre **Interactive** fournit toutes les fonctionnalités de l’expérience utilisateur REPL de la ligne de commande Python. Elle facilite également l’échange de code avec des fichiers sources dans l’éditeur Visual Studio, qui sans cela serait fastidieux avec la ligne de commande.

> [!NOTE]
> Pour les problèmes liés à REPL, vérifiez que les packages `ipython` et `ipykernel` sont installés. Pour obtenir de l’aide sur l’installation des packages, consultez [Onglet packages, Environnements Python](https://docs.microsoft.com/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab).

1. Ouvrez la fenêtre **Interactive** en cliquant avec le bouton droit sur l’environnement Python du projet dans l’**Explorateur de solutions** (par exemple **Python 3.6 (32 bits)** , qui figure dans une illustration précédente), puis en sélectionnant **Ouvrir la fenêtre Interactive**. Vous pouvez également sélectionner **Affichage** > **Autres fenêtres** > **Fenêtres interactives Python** dans le menu principal de Visual Studio.

1. La fenêtre **Interactive** s’ouvre en dessous de l’éditeur avec l’invite de commandes REPL Python standard **>>>** . La liste déroulante **Environnement** vous permet de sélectionner un interpréteur spécifique à utiliser. Vous pouvez aussi agrandir la fenêtre **Interactive** en faisant glisser le séparateur entre les deux fenêtres :

    ![Fenêtre interactive de Python - redimensionnement par glissement](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Vous pouvez redimensionner toutes les autres fenêtres de Visual Studio en faisant glisser les séparateurs adjacents. Vous pouvez également faire glisser des fenêtres indépendamment du cadre principal de Visual Studio et les réorganiser comme vous le souhaitez dans ce cadre. Pour plus d’informations, consultez [Personnaliser les dispositions de fenêtres](../ide/customizing-window-layouts-in-visual-studio.md).

1. Entrez quelques instructions comme `print("Hello, Visual Studio")`, et des expressions comme `123/456` pour voir les résultats immédiats :

    ![Résultats immédiats de la fenêtre interactive Python](media/vs-getting-started-python-12-interactive2.png)

1. Quand vous commencez à écrire une instruction multiligne, par exemple une définition de fonction, la fenêtre **Interactive** affiche l’invite **...** de Python pour continuer les lignes, ce qui, contrairement à l’environnement en ligne de commande REPL, entraîne une mise en retrait automatique :

    ![Fenêtre interactive Python avec poursuite de l’instruction](media/vs-getting-started-python-13-interactive3.png)

1. La fenêtre **Interactive** fournit un historique complet de tout ce que vous avez entré. De plus, elle améliore l’environnement en ligne de commande REPL avec des éléments d’historique multilignes. Par exemple, vous pouvez facilement rappeler l’ensemble de la définition de la fonction `f` ci-dessus comme un tout, puis la renommer `make_double`, sans avoir à recréer la fonction ligne par ligne.

1. Visual Studio peut envoyer plusieurs lignes de code depuis la fenêtre d’un éditeur vers la fenêtre **Interactive**. Cette fonctionnalité vous permet de conserver le code dans un fichier source, et d’en envoyer facilement certaines parties vers la fenêtre **Interactive**. Vous pouvez ensuite travailler avec ces fragments de code dans l’environnement rapide REPL au lieu d’avoir à exécuter la totalité du programme. Pour voir cette fonctionnalité, remplacez d’abord la boucle `for` dans le fichier *PythonApplication1.py* par ceci :

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Sélectionnez les instructions de fonction `import`, `from` et `make_dot_string` dans le fichier *. py* , cliquez avec le bouton droit, puis sélectionnez **Envoyer vers interactive** (ou appuyez sur **CTRL**+**entrée**). Le fragment de code est immédiatement collé dans la fenêtre **Interactive**, puis exécuté. Étant donné que le code a défini une fonction, vous pouvez rapidement tester cette fonction en l’appelant plusieurs fois :

    ![Envoi de code dans la fenêtre interactive et test de ce code](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > L’utilisation de **Ctrl**+**Entrée** dans l’éditeur *sans* sélection entraîne l’exécution de la ligne de code active dans la fenêtre **Interactive** et le placement automatique du point d’insertion à la ligne suivante. Avec cette fonctionnalité, l’utilisation répétée de **Ctrl**+**Entrée** offre un moyen pratique de parcourir votre code pas à pas, ce qui n’est pas possible avec la ligne de commande Python uniquement. Elle vous permet également de parcourir votre code pas à pas sans exécuter le débogueur et sans nécessairement démarrer votre programme à partir du début.

1. Vous pouvez également copier et coller plusieurs lignes de code dans la fenêtre **Interactive** à partir de n’importe quelle source, par exemple l’extrait de code ci-dessous, ce qui est difficile à faire avec l’environnement en ligne de commande REPL de Python. Une fois le code collé, la fenêtre **Interactive** l’exécute comme si vous l’y aviez tapé :

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Collage de plusieurs lignes de code à l’aide de la commande Envoyer vers Interactive](media/vs-getting-started-python-15-interactive5.png)

1. Comme vous pouvez le voir, ce code fonctionne correctement, mais sa sortie n’est pas très intéressante. Une valeur différente pour le pas de la boucle `for` montrerait une partie plus importante de la courbe de la fonction cosinus. Heureusement, comme la totalité de la boucle `for` se trouve dans l’historique REPL comme un tout, vous pouvez facilement revenir en arrière et apporter les modifications souhaitées, puis tester à nouveau la fonction. Appuyez sur la flèche vers le haut pour d’abord rappeler la boucle `for`. Appuyez ensuite sur les flèches gauche ou droite pour parcourir le code (tant que vous le faites, les flèches haut et bas continuent de boucler dans l’historique). Accédez à la spécification `range` et changez-la en `range(0, 360, 12)`. Appuyez ensuite sur **Ctrl**+**Entrée** (n’importe où dans le code) pour réexécuter l’intégralité de l’instruction :

    ![Modification d’une instruction précédente dans la fenêtre interactive](media/vs-getting-started-python-16-interactive6.png)

1. Répétez le processus pour faire des essais avec différentes valeurs de pas jusqu’à trouver la valeur que vous préférez. Vous pouvez également faire en sorte que la courbe se répète en augmentant la plage, par exemple `range(0, 1800, 12)`.

1. Une fois que vous êtes satisfait du code que vous avez écrit dans la fenêtre **Interactive**, sélectionnez-le, cliquez avec le bouton droit de la souris, sélectionnez **Copier le code** (**Ctrl**+**Maj**+**C**), puis collez-le dans l’éditeur. Notez que cette fonctionnalité spéciale de Visual Studio ne produit aucune sortie, ni les invites `>>>` et `...`. Par exemple, l’image ci-dessous montre l’utilisation de la commande **Copier le code** sur une sélection qui inclut des invites et une sortie :

    ![La commande de copie de code de la fenêtre interactive sur une sélection avec des invites et une sortie](media/vs-getting-started-python-17-interactive7.png)

    Quand vous collez dans l’éditeur, vous obtenez seulement le code :

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Si vous souhaitez copier le contenu exact de la fenêtre **Interactive**, notamment les invites et la sortie, utilisez simplement la commande **Copier** standard.

1. Vous venez d’utiliser l’environnement REPL rapide de la fenêtre **Interactive** pour travailler sur les détails d’un petit bout de code, puis vous avez ajouté ce code au fichier source de votre projet. Désormais, quand vous réexécutez le code avec **Ctrl**+**F5** (ou **Déboguer** > **Exécuter sans débogage**), vous voyez exactement les résultats souhaités.

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Exécuter du code dans le débogueur](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Approfondir la question

- [Utiliser la fenêtre Interactive](python-interactive-repl-in-visual-studio.md)
- [Utiliser l’environnement REPL d’IPython](interactive-repl-ipython.md)
