---
title: Tutoriel Python dans Visual Studio - étape 2, écrire et exécuter du code
titleSuffix: ''
description: Étape 2 d’une procédure pas à pas portant sur les fonctionnalités de Python dans Visual Studio qui explique comment modifier du code et exécuter un projet.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7ca28446377c2e04766f70c9146e09dc47b8f089
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882776"
---
# <a name="step-2-write-and-run-code"></a>Étape 2 : Écrire et exécuter du code

**Étape précédente : [Créer un projet Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Même si **Explorateur de solutions** est l’emplacement où vous gérez les fichiers projet, la fenêtre de l' *éditeur* est généralement l’endroit où vous travaillez avec le *contenu* des fichiers, comme le code source. L’éditeur fonctionne contextuellement selon le type de fichier que vous éditez, notamment le langage de programmation (sur la base de l’extension de fichier) et offre des fonctionnalités appropriées à ce langage, comme la coloration syntaxique et la saisie semi-automatique avec IntelliSense.

1. Une fois que vous avez créé un projet « Application Python », un fichier vide par défaut nommé *PythonApplication1.py* s’ouvre dans l’éditeur Visual Studio.

1. Dans l’éditeur, commencez à taper `print("Hello, Visual Studio")` et observez la manière dont Visual Studio IntelliSense affiche les options de saisie semi-automatique au cours de la frappe. L’option indiquée dans la liste déroulante est la saisie semi-automatique par défaut qui est utilisée lorsque vous appuyez sur la touche **Tab** . Les saisies semi-automatiques sont le plus utiles dans le cas d’instructions ou d’identificateurs plus longs.

    ![Menu contextuel de la saisie semi-automatique IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense affiche différentes informations selon l’instruction que vous utilisez, la fonction que vous appelez, et ainsi de suite. Avec la fonction `print`, le fait de taper `(` après `print` pour indiquer un appel de fonction affiche des informations complètes sur l’utilisation de cette fonction. La fenêtre contextuelle IntelliSense montre également l’argument actif en caractères gras (**value**, comme illustré ici) :

    ![Menu contextuel de la saisie semi-automatique IntelliSense pour une fonction](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Complétez l’instruction afin qu’elle corresponde à ce qui suit :

    ```python
    print("Hello, Visual Studio")
    ```

1. Notez la coloration syntaxique, qui différencie l’instruction `print` de l’argument `"Hello Visual Studio"`. De même, supprimez temporairement le dernier `"` sur la chaîne et notez la façon dont Visual Studio affiche un trait de soulignement rouge pour le code qui contient des erreurs de syntaxe. Remplacez ensuite le `"` pour corriger le code.

    ![Coloration syntaxique et mise en évidence des erreurs par IntelliSense](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > L’environnement de développement de quelqu’un étant une affaire très personnelle, Visual Studio vous donne un contrôle complet sur son apparence et son comportement. Sélectionnez la commande de menu **Outils**  >  **options** et explorez les paramètres sous les onglets **environnement** et **éditeur de texte** . Par défaut, vous voyez seulement un nombre limité d’options. Pour afficher toutes les options pour chaque langage de programmation, sélectionnez **Afficher tous les paramètres** en bas de la boîte de dialogue.

1. Exécutez le code que vous avez écrit à ce stade en appuyant sur **CTRL** + **F5** ou en sélectionnant l’élément de menu **Déboguer**  >  **Démarrer sans débogage** . Visual Studio vous avertit si votre code contient encore des erreurs.

1. Quand vous exécutez le programme, une fenêtre de console affiche les résultats, comme si vous exécutiez un interpréteur Python avec *PythonApplication1.py* à partir de la ligne de commande. Appuyez sur une touche pour fermer la fenêtre et revenir à l’éditeur Visual Studio.

    ![Sortie pour la première exécution du programme](media/vs-getting-started-python-07-output.png)

1. En plus des instructions et des fonctions, IntelliSense fournit aussi la saisie semi-automatique pour les instructions Python `import` et `from`. Ces saisies semi-automatiques vous permettent de découvrir facilement les modules qui sont disponibles dans votre environnement, ainsi que les membres de ces modules. Dans l’éditeur, supprimez la ligne `print` et commencez à taper `import`. Une liste des modules apparaît quand vous tapez l’espace :

    ![Affichage des modules disponibles pour une instruction import dans IntelliSense](media/vs-getting-started-python-08-import1.png)

1. Complétez la ligne en tapant ou en sélectionnant `sys`.

1. Sur la ligne suivante, tapez `from` pour afficher de nouveau la liste des modules :

    ![Affichage des modules disponibles pour une instruction from dans IntelliSense](media/vs-getting-started-python-09-import2.png)

1. Sélectionnez ou tapez `math`, puis continuez avec un espace et `import`, pour afficher les membres du module :

    ![Affichage des membres du module dans IntelliSense](media/vs-getting-started-python-10-import3.png)

1. Terminez en important les membres `sin`, `cos` et `radians`, en notant pour chacun d’eux les modes de saisie automatique disponibles. Lorsque vous avez terminé, votre code doit apparaître comme suit :

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > La saisie semi-automatique fonctionne avec des sous-chaînes au fil de la saisie, en faisant correspondre des parties de mots, des lettres en début de mots et même des caractères ignorés. Pour plus d’informations, consultez [Modifier le code - Complétions](editing-python-code-in-visual-studio.md#completions).

1. Ajoutez un peu plus de code pour afficher les valeurs du cosinus pour 360 degrés :

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Exécutez de nouveau le programme en **appuyant sur CTRL** + **F5** ou **Déboguer** exécuter  >  **sans débogage**. Fermez la fenêtre de sortie quand vous avez terminé.

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Utiliser la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Approfondir la question

- [Modifier le code](editing-python-code-in-visual-studio.md)
- [Code du format](formatting-python-code.md)
- [Refactoriser du code](refactoring-python-code.md)
- [Utiliser PyLint](linting-python-code.md)
