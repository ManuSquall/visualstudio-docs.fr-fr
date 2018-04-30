---
title: 'Utilisation de Python - Étape 3 : Fenêtre REPL interactive'
description: Étape 3 d’un didacticiel de base sur l’utilisation de Python dans Visual Studio, présentant la fenêtre REPL interactive de Python.
ms.date: 01/16/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 0a0cbe766f1b31166185275989bfa0678ed50690
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="step-3-using-the-interactive-repl-window"></a>Étape 3 : Utilisation de la fenêtre REPL interactive

**Étape précédente : [Écriture et exécution du code](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

La *fenêtre interactive* Visual Studio pour Python offre une expérience REPL (read-evaluate-print-loop) enrichie qui réduit considérablement le cycle habituel de modification-génération-débogage. La fenêtre interactive fournit toutes les fonctionnalités de l’expérience REPL de la ligne de commande Python. Elle facilite également l’échange de code avec des fichiers sources dans l’éditeur Visual Studio, qui sans cela serait fastidieux avec la ligne de commande.

1. Ouvrez la fenêtre interactive en cliquant avec le bouton droit sur l’environnement Python du projet dans l’Explorateur de solutions (comme « Python 3.6 (32 bits) », qui figure dans une illustration plus haut) et en sélectionnant **Ouvrir la fenêtre Interactive**. Vous pouvez aussi sélectionner **Affichage > Autres fenêtres > Fenêtres interactives Python** dans le menu principal de Visual Studio.

1. La fenêtre interactive s’ouvre en dessous de l’éditeur avec l’invite de commandes REPL Python standard `>>>`. La liste déroulante **Environnement** vous permet de sélectionner un interpréteur spécifique à utiliser. Vous pouvez aussi agrandir la fenêtre interactive en faisant glisser le séparateur entre les deux fenêtres :

    ![Fenêtre interactive de Python - redimensionnement par glissement](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Vous pouvez redimensionner toutes les autres fenêtres de Visual Studio en faisant glisser les séparateurs adjacents. Vous pouvez également faire glisser des fenêtres indépendamment du cadre principal de Visual Studio et les réorganiser comme vous le souhaitez dans ce cadre. Pour plus d’informations, consultez [Personnalisation des dispositions de fenêtres](../ide/customizing-window-layouts-in-visual-studio.md).

1. Entrez quelques instructions comme `print("Hello, Visual Studio")`, et des expressions comme `123/456` pour voir les résultats immédiats :

    ![Résultats immédiats de la fenêtre interactive Python](media/vs-getting-started-python-12-interactive2.png)

1. Quand vous commencez à écrire une instruction multiligne, comme une définition de fonction, la fenêtre interactive affiche l’invite `...` de Python pour continuer les lignes, qui, contrairement à REPL en ligne de commande, fournit une indentation automatique :

    ![Fenêtre interactive Python avec poursuite de l’instruction](media/vs-getting-started-python-13-interactive3.png)

1. La fenêtre interactive fournit un historique complet de tout ce que vous avez saisi et améliore la boucle REPL de ligne de commande avec des éléments d’historique multilignes. Par exemple, vous pouvez facilement rappeler l’ensemble de la définition de la fonction `f` ci-dessus comme un tout, puis la renommer `make_double`, sans avoir à recréer la fonction ligne par ligne.

1. Visual Studio peut envoyer plusieurs lignes de code depuis la fenêtre d’un éditeur vers la fenêtre interactive. Cette fonctionnalité vous permet de conserver le code dans un fichier source et d’envoyer facilement sélectionner des parties de celui-ci vers la fenêtre interactive. Vous pouvez ensuite travailler avec ces fragments de code dans l’environnement rapide REPL au lieu d’avoir à exécuter la totalité du programme. Pour voir cette fonctionnalité, remplacez d’abord la boucle `for` dans le fichier `PythonApplication1.py` par ceci :

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Sélectionnez seulement les instructions `import` et `from` dans le fichier `.py`, cliquez avec le bouton droit et sélectionnez **Envoyer vers Interactive** (ou appuyez sur Ctrl+Entrée). Le fragment de code est immédiatement collé dans la fenêtre interactive et exécuté. Sélectionnez maintenant la fonction `make_dot_string` et répétez la même commande, qui réexécute ce fragment de code. Étant donné que le code définit une fonction, vous pouvez rapidement tester cette fonction en l’appelant à plusieurs reprises :

    ![Envoi de code dans la fenêtre interactive et test de ce code](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > L’utilisation de Ctrl+Entrée dans l’éditeur *sans* sélection exécute la ligne de code active dans la fenêtre interactive et place automatiquement le point d’insertion sur la ligne suivante. Avec cette fonctionnalité, l’utilisation répétée de Ctrl+Entrée offre un moyen pratique de parcourir votre code pas à pas, ce qui n’est pas possible avec seulement la ligne de commande Python. Elle vous permet également de parcourir votre code pas à pas sans exécuter le débogueur et sans nécessairement démarrer votre programme à partir du début.

1. Vous pouvez également copier et coller plusieurs lignes de code dans la fenêtre interactive à partir de n’importe quelle source, comme l’extrait de code ci-dessous, ce qui est difficile à faire avec REPL en ligne de commande de Python. Une fois le code collé, la fenêtre interactive l’exécute comme si vous l’y aviez tapé :

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Collage de plusieurs lignes de code à l’aide de la commande Envoyer vers Interactive](media/vs-getting-started-python-15-interactive5.png)

1. Comme vous pouvez le voir, ce code fonctionne correctement, mais sa sortie n’est pas très intéressante. Une valeur différente pour le pas de la boucle `for` montrerait une partie plus importante de la courbe de la fonction cosinus. Heureusement, comme la totalité de la boucle `for` se trouve dans l’historique REPL comme un tout, vous pouvez facilement revenir en arrière et apporter les modifications souhaitées, puis tester à nouveau la fonction. Appuyez sur la flèche vers le haut pour d’abord rappeler la boucle `for`. Appuyez ensuite sur les flèches gauche ou droite pour parcourir le code (tant que vous le faites, les flèches haut et bas continuent de boucler dans l’historique). Accédez à la spécification `range` et changez-la en `range(0, 360, 12)`. Appuyez ensuite sur Ctrl+Entrée (n’importe où dans le code) pour réexécuter toute l’instruction :

    ![Modification d’une instruction précédente dans la fenêtre interactive](media/vs-getting-started-python-16-interactive6.png)

1. Répétez le processus pour faire des essais avec différentes valeurs de pas jusqu’à trouver la valeur que vous préférez. Vous pouvez également faire en sorte que la courbe se répète en augmentant la plage, par exemple `range(0, 1800, 12)`.
 
1. Quand le code que vous avez écrit dans la fenêtre interactive vous satisfait, sélectionnez-le, cliquez avec le bouton droit et sélectionnez **Copier le code** (Ctrl+Maj+C), puis collez-le dans l’éditeur. Notez que cette fonctionnalité spéciale de Visual Studio ne produit aucune sortie, ni les invites `>>>` et `...`. Par exemple, l’image ci-dessous montre l’utilisation de la commande **Copier le code** sur une sélection qui inclut des invites et une sortie :

    ![La commande de copie de code de la fenêtre interactive sur une sélection avec des invites et une sortie](media/vs-getting-started-python-17-interactive7.png)

    Quand vous collez dans l’éditeur, vous obtenez seulement le code :

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Si vous voulez copier le contenu exact de la fenêtre interactive, y compris les invites et la sortie, utilisez simplement la commande **Copier** standard.

1. Vous venez d’utiliser l’environnement REPL rapide de la fenêtre interactive pour travailler sur les détails d’un petit morceau de code, puis vous avez ajouté ce code au fichier source de votre projet. Maintenant, quand vous réexécutez le code avec Ctrl+F5 (ou **Déboguer > Démarrer sans débogage**), vous voyez exactement les résultats souhaités.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Exécution de code dans le débogueur](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="going-deeper"></a>Pour aller plus loin

- [Utilisation de la fenêtre interactive](python-interactive-repl-in-visual-studio.md)
- [Utilisation d’IPython REPL](interactive-repl-ipython.md)
