---
title: "Utilisation de Python dans Visual Studio, étape 2 - écriture et exécution du code | Microsoft Docs"
description: "Étape 2 d’un didacticiel de base sur l’utilisation de Python dans Visual Studio, décrivant comment modifier et exécuter un programme Hello World simple, suivie d’un code plus intéressant illustrant les fonctionnalités IntelliSense et d’édition de Visual Studio."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 4616b8df91ce87b8f886deb9143fa1ff55a976d7
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2018
---
# <a name="step-2-writing-and-running-code"></a>Étape 2 : Écriture et exécution du code

**Étape précédente : [Création d’un projet Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Si l’Explorateur de solutions soit l’endroit où vous gérez les fichiers des projets, la fenêtre *Éditeur* est généralement l’endroit où vous travaillez avec le *contenu* des fichiers, comme le code source. L’éditeur fonctionne contextuellement selon le type de fichier que vous éditez, notamment le langage de programmation (sur la base de l’extension de fichier) et offre des fonctionnalités appropriées à ce langage, comme la coloration syntaxique et la saisie semi-automatique avec IntelliSense.

1. Une fois que vous avez créé un nouveau projet « Application Python », un fichier vide nommé `PythonApplication1.py` par défaut s’ouvre dans l’éditeur Visual Studio.

1. Dans l’éditeur, commencez à taper `print("Hello, Visual Studio")` et observez la manière dont Visual Studio IntelliSense affiche les options de saisie semi-automatique au cours de la frappe. L’option indiquée dans la liste déroulante correspond au mode de saisie semi-automatique par défaut qui est utilisé lorsque vous appuyez sur la touche de tabulation. Les saisies semi-automatiques sont le plus utiles dans le cas d’instructions ou d’identificateurs plus longs.

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
    > L’environnement de développement de quelqu’un étant une affaire très personnelle, Visual Studio vous donne un contrôle complet sur son apparence et son comportement. Sélectionnez la commande de menu **Outils > Options** et explorez les paramètres sous les onglets **Environnement** et **Éditeur de texte**. Par défaut, vous voyez seulement un nombre limité d’options. Pour afficher toutes les options pour chaque langage de programmation, sélectionnez **Afficher tous les paramètres** dans le bas de la boîte de dialogue. 

1. Exécutez le code que vous avez écrit à ce stade en appuyant sur Ctrl+F5 ou en sélectionnant l’élément de menu **Déboguer > Démarrer sans débogage**. Visual Studio vous avertit si votre code contient encore des erreurs.

1. Quand vous exécutez le programme, une fenêtre de console affiche les résultats, comme si vous exécutiez un interpréteur Python avec `PythonApplication1.py` à partir de la ligne de commande. Appuyez sur une touche pour fermer la fenêtre et revenir à l’éditeur Visual Studio.

    ![Sortie pour la première exécution du programme](media/vs-getting-started-python-07-output.png)

1. En plus des instructions et des fonctions, IntelliSense fournit aussi la saisie semi-automatique pour les instructions Python `import` et `from`. Ces saisies semi-automatiques vous permettent de découvrir facilement les modules qui sont disponibles dans votre environnement, ainsi que les membres de ces modules. Dans l’éditeur, supprimez la ligne `print` et commencez à taper `import `. Une liste des modules apparaît quand vous tapez l’espace :

    ![Affichage des modules disponibles pour une instruction import dans IntelliSense](media/vs-getting-started-python-08-import1.png)

1. Complétez la ligne en tapant ou en sélectionnant `sys`.

1. Sur la ligne suivante, tapez `from` pour afficher de nouveau la liste des modules :

    ![Affichage des modules disponibles pour une instruction from dans IntelliSense](media/vs-getting-started-python-09-import2.png)

1. Sélectionnez ou tapez `math`, puis continuez avec un espace et `import`, pour afficher les membres du module :

    ![Affichage des membres du module dans IntelliSense](media/vs-getting-started-python-10-import3.png)

1. Terminez en important les membres `sin`, `cos` et `radians`, en notant pour chacun d’eux les modes de saisie automatique disponibles. Lorsque vous avez terminé, votre code doit apparaître comme suit :

    ```python
    import sys
    from math import sin, cos, radians
    ```

    > [!Tip]
    > La saisie semi-automatique fonctionne avec des sous-chaînes au fil de la saisie, en faisant correspondre des parties de mots, des lettres en début de mots et même des caractères ignorés. Pour plus d’informations, consultez la page [Modification du code - Saisie semi-automatique](code-editing.md#completions).

1. Ajoutez un peu plus de code pour afficher les valeurs du cosinus pour 360 degrés :

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Relancez le programme avec Ctrl+F5 ou **Déboguer > Démarrer sans débogage**. Fermez la fenêtre de sortie quand vous avez terminé.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utilisation de la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="going-deeper"></a>Pour aller plus loin

- [Modification du code](code-editing.md)
- [Mise en forme du code](code-formatting.md)
- [Refactorisation du code](code-refactoring.md)
- [Utilisation de PyLint](code-pylint.md)
