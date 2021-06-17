---
title: 'Tutoriel : Python dans Visual Studio, étape 4, débogage'
titleSuffix: ''
description: Étape 4 d’une procédure pas à pas portant sur les fonctionnalités de Python dans Visual Studio qui explique comment exécuter le code Python dans le débogueur.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 13080f69de9a8bfc6b1da35a7126f1f0c89a64c7
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254860"
---
# <a name="step-4-run-code-in-the-debugger"></a>Étape 4 : Exécuter du code dans le débogueur

**Étape précédente : [Utiliser la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

En plus de ses fonctionnalités de gestion de projets, de son expérience utilisateur très riche au niveau de l’édition et de sa fenêtre **Interactive**, Visual Studio offre des fonctionnalités complètes de débogage pour le code Python. Dans le débogueur, vous pouvez exécuter votre code pas à pas, notamment chaque itération d’une boucle. Vous pouvez également interrompre le programme chaque fois que certaines conditions sont remplies. À tout moment, quand le programme est en pause dans le débogueur, vous pouvez examiner l’état de l’ensemble du programme et changer la valeur des variables. Ces actions sont essentielles pour le suivi des bogues du programme et fournissent également des aides très utiles pour suivre avec précision le flux exact du programme.

1. Remplacez le code du fichier *PythonApplication1.py* par ce qui suit. Cette variation du code se développe `make_dot_string`, ce qui vous permet d’examiner ses étapes discrètes dans le débogueur. Il place également la boucle `for` dans une fonction `main` et l’exécute explicitement en appelant cette fonction :

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(rad) + 20)          # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Vérifiez que le code fonctionne correctement en appuyant sur **F5** ou en sélectionnant la commande de menu **Déboguer** > **Démarrer le débogage**. Cette commande exécute le code dans le débogueur mais, comme vous n’avez rien fait pour interrompre le programme pendant son exécution, il affiche simplement un motif de vague pour quelques itérations. Appuyez sur une touche pour fermer la fenêtre de sortie.

    > [!Tip]
    > Pour fermer automatiquement la fenêtre sortie une fois le programme terminé, sélectionnez la commande de menu **Outils**  >  **options** , développez le nœud **python** , sélectionnez **débogage**, puis désactivez l’option **attendre l’entrée quand le processus s’arrête normalement**:
    >
    > ![Option de débogage Python permettant de fermer la fenêtre Sortie quand l’utilisateur quitte le programme normalement](media/vs-getting-started-python-22-debugging5.png)
    >
    > Pour plus d’informations sur le débogage, y compris les tâches telles que la définition des arguments de script et d’interpréteur, consultez [déboguer votre code python](debugging-python-in-visual-studio.md).

1. Définissez un point d’arrêt sur l' `for` instruction en cliquant une fois dans la marge grise en fonction de cette ligne, ou en plaçant le signe insertion dans cette ligne et en utilisant la commande **Déboguer**  >  **basculer le point d’arrêt** (**F9**). Un point rouge apparaît dans la marge grise pour indiquer le point d’arrêt (comme indiqué par la flèche) :

    ![Définition d'un point d'arrêt](media/vs-getting-started-python-18-debugging1.png)

1. Redémarrez le débogueur (**F5**). Vous voyez à présent que l’exécution du code s’arrête sur la ligne où ce point d’arrêt est défini. Vous pouvez examiner ici la pile des appels et les variables locales. Les variables qui sont dans l’étendue apparaissent dans la fenêtre **Automatique** quand elles sont définies ; vous pouvez également basculer vers la vue **Variables locales** dans le bas de cette fenêtre pour afficher toutes les variables trouvées par Visual Studio dans l’étendue active (notamment les fonctions), même avant qu’elles soient définies :

    ![Expérience de l’interface utilisateur des points d’arrêt pour Python](media/vs-getting-started-python-19-debugging2b.png)

1. Observez la barre d’outils de débogage (affichée ci-dessous) en haut de la fenêtre Visual Studio. Cette barre d’outils fournit un accès rapide aux commandes de débogage les plus courantes (qui sont également accessibles sur le menu **Débogage**) :

    ![Boutons principaux de la barre d’outils de débogage](media/vs-getting-started-python-20-debugging3.png)

    Les boutons sont les suivants, de gauche à droite :
    - **Continuer** (**F5**) exécute le programme jusqu’au point d’arrêt suivant ou jusqu’à la fin du programme.
    - **Interrompre tout** (**Ctrl**+**Alt**+**Pause**) interrompt un programme dont l’exécution est longue.
    - **Arrêter le débogage** (**Maj**+**F5**) arrête le programme où qu’il en soit, puis quitte le débogueur.
    - **Redémarrer** (**Ctrl**+**Maj**+**F5**) arrête le programme où qu’il en soit, puis le redémarre à partir du début dans le débogueur.
    - **Afficher l’instruction suivante** (**ALT** + **num** **&#42;**) bascule sur la ligne de code suivante à exécuter. Ceci est spécialement utile quand vous naviguez au sein de votre code pendant une session de débogage et que vous voulez retourner rapidement au point où le débogueur est en suspens.
    - **Pas à pas détaillé** (**F11**) exécute la ligne de code suivante, en entrant dans les fonctions appelées.
    - **Pas à pas principal** (**F10**) exécute la ligne de code suivante sans entrer dans les fonctions appelées.
    - **Pas à pas sortant** (**Shift** + **F11**) exécute le reste de la fonction active et s’interrompt dans le code appelant.

1. Faites un pas à pas principal de l’instruction `for` en utilisant **Pas à pas principal**. *L’exécution pas à pas* signifie que le débogueur exécute la ligne de code active, y compris tous les appels de fonction, puis s’interrompt à nouveau immédiatement. Notez comment la variable `i` est maintenant définie dans les fenêtres **Variables locales** et **Automatique**.

1. Faites un pas à pas principal de la ligne de code suivante, qui appelle `make_dot_string` et s’interrompt. La **procédure pas à pas principal** signifie spécifiquement que le débogueur exécute l’ensemble de `make_dot_string` et s’interrompt lorsqu’il retourne. Le débogueur ne s’arrête pas à l’intérieur de cette fonction, sauf si un point d’arrêt distinct s’y trouve.

1. Continuez à demander un certain nombre de fois l’exécution en pas à pas principal du code, et observez comment les valeurs changent dans les fenêtres **Variables locales** ou **Automatique**.

1. Dans la fenêtre **Variables locales** ou **Automatique**, double-cliquez dans la colonne **Valeur** pour la variable `i` ou `s` et changez la valeur. Appuyez sur **entrée** ou cliquez sur une zone en dehors de cette valeur pour appliquer les modifications.

1. Continuez à parcourir le code pas à pas en utilisant **Pas à pas détaillé**. **Pas à pas détaillé** signifie que le débogueur entre dans un appel de fonction pour lequel il contient des informations de débogage, telles que `make_dot_string` . Une fois à l’intérieur de `make_dot_string`, vous pouvez examiner ses variables locales et exécuter son code spécifiquement.

1. Continuez l’exécution pas à **pas avec pas à pas** détaillé et remarquez que lorsque vous atteignez la fin de la `make_dot_string` , l’étape suivante retourne à la `for` boucle avec la nouvelle valeur de retour dans la `s` variable. Au fur et à mesure que vous avancerez dans l' `print` instruction, Notez que pas à **pas détaillé** `print` n’entre dans cette fonction. La raison en est que `print` n’est pas écrit en Python, mais qu’il s’agit de code natif au sein du runtime Python.

1. Continuez à utiliser le **pas à pas** détaillé jusqu’à ce que vous soyez à nouveau inséré `make_dot_string` . Utilisez ensuite **Pas à pas sortant** et notez que vous revenez alors à la boucle `for`. Avec **pas à pas sortant**, le débogueur exécute le reste de la fonction, puis s’interrompt automatiquement dans le code appelant. Ceci est très utile quand vous avez exécuté pas à pas une partie d’une fonction longue que vous souhaitez déboguer, mais que vous n’avez pas besoin d’en parcourir le reste pas à pas et que vous ne voulez pas définir un point d’arrêt explicite dans le code appelant.

1. Pour continuer l’exécution du programme jusqu’à ce que le point d’arrêt suivant soit atteint, utilisez **Continuer** (**F5**). Étant donné que vous avez défini un point d’arrêt dans la boucle `for`, vous vous arrêtez sur l’itération suivante.

1. Parcourir pas à pas des centaines d’itérations d’une boucle peut être fastidieux : Visual Studio vous permet donc d’ajouter une *condition* à un point d’arrêt. Le débogueur interrompt alors le programme au point d’arrêt seulement quand la condition est remplie. Par exemple, vous pouvez utiliser une condition avec le point d’arrêt sur l’instruction `for` pour qu’elle s’interrompe seulement quand la valeur de `i` dépasse 1 600. Pour définir cette condition, cliquez avec le bouton droit sur le point rouge représentant le point d’arrêt, puis sélectionnez **Conditions** (**Alt**+**F9** > **C**). Dans la fenêtre contextuelle **Paramètres de point d’arrêt** qui s’affiche, entrez `i > 1600` comme expression et sélectionnez **Fermer**. Appuyez sur **F5** pour continuer et observez que le programme exécute de nombreuses itérations avant l’arrêt suivant.

    ![Définition d’une condition de point d’arrêt](media/vs-getting-started-python-21-debugging4.png)

1. Pour exécuter le programme jusqu’à la fin, désactivez le point d’arrêt en cliquant avec le bouton droit sur le point dans la marge et en sélectionnant **désactiver le point d’arrêt** (**CTRL** + **F9**). Sélectionnez ensuite **Continuer** (ou appuyez sur **F5**) pour exécuter le programme. Quand le programme se termine, Visual Studio arrête sa session de débogage et retourne au mode Édition. Notez que vous pouvez également supprimer le point d’arrêt en sélectionnant son point ou en cliquant avec le bouton droit sur le point et en sélectionnant **supprimer le point d’arrêt**, mais cela supprime également toutes les conditions que vous avez définies.

> [!Tip]
> Dans certaines situations, par exemple en cas d’échec du lancement de l’interpréteur Python lui-même, la fenêtre Sortie peut apparaître seulement brièvement, puis se fermer automatiquement sans vous donner la possibilité de visualiser les messages d’erreurs. Dans ce cas, cliquez avec le bouton droit sur le projet dans **Explorateur de solutions**, sélectionnez **Propriétés**, sélectionnez l’onglet **Déboguer** , puis ajoutez `-i` au champ arguments de l' **interpréteur** . Cet argument fait en sorte que l’interpréteur passe en mode interactif à la fin d’un programme, ce qui maintient la fenêtre ouverte jusqu’à ce que vous entriez **CTRL** + **Z**  >  **entrée** pour quitter.

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Installer des packages dans votre environnement Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Approfondir la question

- [Débogage](debugging-python-in-visual-studio.md)
- [Débogage dans Visual Studio](../debugger/debugger-feature-tour.md) fournit une documentation complète sur les fonctionnalités de débogage de Visual Studio.
