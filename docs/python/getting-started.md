---
title: Prise en main de Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 0b87d25195b8e288252e6c53279897d1edff93bd
ms.lasthandoff: 03/10/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Bien démarrer avec Python dans Visual Studio

Dès lors que vous avez installé Visual Studio avec la charge de travail Python (Visual Studio 2017), ou avec Python Tools pour Visual Studio (Visual Studio 2015 et versions antérieures), vous pouvez commencer à explorer l’expérience du développement Python.

Dans cette procédure pas à pas, vous allez créer une application Python vide, choisir un environnement de travail Python, puis commencer à écrire du code pour découvrir la fonctionnalité IntelliSense en action. Vous allez ensuite utiliser brièvement la fenêtre REPL interactive pour créer davantage de code, puis terminer le programme et l’exécuter de lui-même et dans le débogueur.

> [!Note]
> Cette procédure pas à pas explore l’expérience Python dans Visual Studio 2017 ; les autres versions fonctionnent de façon similaire mais peuvent présenter quelques différences.

## <a name="create-a-new-python-project"></a>Création d’un nouveau projet Python

La prise en charge de Python dans Visual Studio comprend un certain nombre de [modèles de projet](python-projects.md) pour vous aider à démarrer avec différents types de projets, notamment des applications web utilisant les infrastructures Bottle, Flask et Django, ainsi que des services Azure Cloud Services. Dans le cadre de cette procédure pas à pas, nous allons cependant commencer avec un projet vide.

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet** pour afficher la boîte de dialogue **Nouveau projet**. Vous pouvez ici rechercher et sélectionner un modèle, puis spécifier le dossier dans lequel créer le projet.

1. Les modèles Python se trouvent sous le menu **Templates > Other Languages > Python** (Modèles > Autres langages > Python) à gauche. Vous pouvez également y accéder en effectuant une simple recherche sur « Python » :

    ![Boîte de dialogue Nouveau projet avec les projets Python](media/getting-started-new-project.png)

1. Sélectionnez le modèle « Python Application » (Application Python), spécifiez un dossier pour le projet, puis cliquez sur **OK**. (Si vous souhaitez créer directement un référentiel local pour votre projet, vous devez également sélectionner l’option **Ajouter au contrôle de code source**).

    > [!Tip]
    > Le modèle « From exiting Python Code » (À partir de la sortie du code Python) vous permet de créer rapidement un projet Visual Studio à partir d’un dossier qui contient déjà le code Python, sans avoir à créer un projet vide et à y importer du code existant.

1. Après quelques instants, le projet s’ouvre dans la fenêtre Explorateur de solutions de Visual Studio. Vous pouvez ici parcourir les fichiers et les dossiers de votre projet, ainsi que gérer vos environnements.

    ![Explorateur de solutions avec un projet Python](media/getting-started-solution-explorer-1.png)

1. Si vous développez le nœud **Python Environments** (Environnements Python), vous voyez que l’interpréteur Python est défini par défaut pour ce projet. Si vous développez également ce nœud de l’interpréteur, vous obtenez une liste des bibliothèques disponibles dans cet environnement :

    ![Explorateur de solutions présentant l’environnement Python](media/getting-started-solution-explorer-2.png)

1. Si vous utilisez Visual Studio 2015 ou une version antérieure, l’interpréteur Python n’est pas installé par défaut. Reportez-vous à [Selecting and installing a Python interpreter](python-environments.md#selecting-and-installing-python-interpreters) (Sélection et installation d’un interpréteur Python).

### <a name="going-deeper"></a>Pour aller plus loin

- [Projets Python dans Visual Studio](python-projects.md)
- [Modèles de projets web](template-web.md)
- [Modèle de projet web Django](template-django.md)
- [Modèle de service cloud Azure](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>Écriture et exécution du code

1. Une fois que vous avez créé un nouveau projet « Application Python », un fichier vide nommé `PythonApplication1.py` par défaut s’ouvre dans l’éditeur Visual Studio. Pour le renommer, cliquez avec le bouton droit sur le fichier dans l’Explorateur de solutions, sélectionnez l’option **Renommer** et remplacez son nom par `hello.py`.

1. Commencez à saisir `print("Hello world")` et observez la manière dont Visual Studio IntelliSense affiche les options de saisie semi-automatique au cours du processus. L’option indiquée dans la liste déroulante correspond au mode de saisie semi-automatique par défaut qui est utilisé lorsque vous appuyez sur la touche de tabulation. Elle peut être très utile dans le cas d’instructions ou d’identificateurs plus longs.

    ![Menu contextuel de la saisie semi-automatique IntelliSense](media/getting-started-coding-1.png)

1. IntelliSense affiche différentes informations selon l’instruction que vous utilisez, la fonction que vous appelez, et ainsi de suite. Avec la fonction `print`, tapez le caractère `(` pour que l’appel affiche des informations d’utilisation complètes sur cette fonction et indique même en gras l’argument actuel que vous devez fournir (**value** comme indiqué ici) :

    ![Menu contextuel de la saisie semi-automatique IntelliSense pour une fonction](media/getting-started-coding-2.png)

1. Complétez l’instruction afin qu’elle corresponde à ce qui suit :

  ```python
  print("Hello world")
  ```

1. Pour exécuter le code, sélectionnez le bouton **Démarrer** de la barre d’outils ci-dessous, appuyez sur F5 ou sélectionnez l’élément de menu **Debug > Start Debugging** (Déboguer > Démarrer le débogage).

    ![Bouton Démarrer dans la barre d’outils de débogage](media/getting-started-coding-3.png)

    > [!Note]
    > Si, dans Visual Studio 2015 ou une version antérieure, vous obtenez un message vous signalant l’absence d’interpréteurs, consultez la section [Selecting and installing a Python interpreter](python-environments.md#selecting-and-installing-python-interpreters) (Sélection et installation d’un interpréteur Python) car aucun interpréteur n’est installé par défaut.

1. Visual Studio exécute le code à l’aide de l’environnement par défaut dans le projet et affiche les résultats dans une fenêtre de commande. Appuyez sur une touche pour fermer cette fenêtre et mettre fin à la session de débogage.

    ![Bouton Démarrer dans la barre d’outils de débogage](media/getting-started-coding-4.png)

1. Outre les instructions et fonctions, la fonctionnalité IntelliSense fournit une saisie semi-automatique pour les instructions `import`. Cela vous permet de détecter facilement les modules qui sont disponibles dans votre environnement, de même que les membres disponibles dans ce module. Dans l’éditeur, supprimez la ligne `print` et commencez à taper `import`. Vous obtenez une liste de modules :

    ![Affichage des modules disponibles pour une instruction import dans IntelliSense](media/getting-started-coding-5.png)

1. Complétez la ligne en tapant ou en sélectionnant `sys`.

1. Sur la ligne suivante, tapez `from` pour afficher de nouveau la liste des modules :

    ![Affichage des modules disponibles pour une instruction from dans IntelliSense](media/getting-started-coding-6.png)

1. Sélectionnez ou tapez `math`, puis continuez avec un espace et `import`, pour afficher les membres du module :

    ![Affichage des membres du module dans IntelliSense](media/getting-started-coding-7.png)

1. Terminez en important les membres `sin`, `cos` et `radians`, en notant pour chacun d’eux les modes de saisie automatique disponibles. Lorsque vous avez terminé, votre code doit apparaître comme suit :

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> La saisie semi-automatique fonctionne avec des sous-chaînes au fil de la saisie, en faisant correspondre des parties de mots, des lettres en début de mots et même des caractères ignorés. Pour plus d’informations, consultez la page [Editing Code - Completions](code-editing.md#completions) (Modification du code - Saisie semi-automatique).

Dans l’étape suivante, nous allons utiliser la fenêtre REPL interactive pour écrire du code que nous allons pouvoir tester immédiatement sans exécuter le débogueur.

### <a name="going-deeper"></a>Pour aller plus loin

- [Modification du code](code-editing.md)
- [Mise en forme du code](code-formatting.md)
- [Refactorisation du code](code-refactoring.md)
- [Utilisation de PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>Utilisation de la fenêtre REPL interactive

La fenêtre interactive Visual Studio pour Python offre une puissante boucle de lecture-évaluation-impression (REPL) qui réduit considérablement le cycle habituel de modification-génération-débogage. Elle est similaire à l’expérience REPL de la ligne de commande Python, mais fournit quelques fonctionnalités supplémentaires, comme vous le verrez ici.

1. Ouvrez la fenêtre interactive en sélectionnant **View > Other Windows > Python Interactive Windows** (Affichage > Autres fenêtres > Fenêtres interactives Python) dans le menu principal de Visual Studio. La fenêtre s’ouvre avec l’invite de commande >>> habituelle de la boucle REPL Python. Notez que vous pouvez utiliser le menu déroulant dans la barre d’outils pour modifier l’environnement à tout moment :

    ![Fenêtre interactive Python](media/getting-started-interactive-1.png)

1. Entrez quelques instructions (comme `print("hello")`) et des expressions (comme `123/567`) pour voir les résultats immédiats :

    ![Résultats immédiats de la fenêtre interactive Python](media/getting-started-interactive-2.png)

1. Lorsque vous commencez à écrire une instruction multiligne, comme une définition de fonction, la fenêtre interactive affiche l’invite ... pour poursuivre les lignes, qui, contrairement à la boucle REPL de ligne de commande, fournit une mise en retrait automatique :

    ![Fenêtre interactive Python avec poursuite de l’instruction](media/getting-started-interactive-3.png)

1. La fenêtre interactive fournit un historique complet de tout ce que vous avez saisi et améliore la boucle REPL de ligne de commande avec des éléments d’historique multilignes. Par exemple, vous pouvez facilement rappeler l’ensemble de la définition de la fonction `f` ci-dessus sous la forme d’une unité unique, puis la renommer simplement `make_double`, sans avoir à créer de nouveau la fonction ligne par ligne.

1. Autre fonctionnalité très utile : la possibilité d’envoyer rapidement plusieurs lignes de code d’une fenêtre d’éditeur vers la fenêtre interactive, dans laquelle vous pouvez l’utiliser dans l’environnement REPL rapide plutôt que d’avoir à écrire un autre code à exécuter dans le débogueur. Pour voir cette fonctionnalité, commencez par ajouter le code suivant à votre fichier hello.py ouvert dans l’éditeur :

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. Sélectionnez tout le code contenu dans le fichier hello.py (y compris les instructions `import`), cliquez dessus avec le bouton droit, puis sélectionnez **Envoyer vers Interactive** (Ctrl + Entrée). Le code est immédiatement collé dans la fenêtre interactive et exécuté. Étant donné que le code définit une fonction, vous pouvez rapidement tester cette fonction en l’appelant à plusieurs reprises :

    ![Envoi de code dans la fenêtre interactive](media/getting-started-interactive-4.png)

1. La commande **Envoyer vers Interactive** vous permet de coller plusieurs lignes de code (par exemple, quelque chose que vous recherchez en ligne) dans la fenêtre interactive, ce que vous ne pouvez pas faire directement. Par exemple, copiez le code ci-dessous et essayez de le coller (Ctrl + V) dans la fenêtre interactive. Vous verrez que rien ne se produit. Mais vous pouvez le coller dans l’éditeur, le sélectionner et utiliser la commande **Envoyer vers Interactive** pour le voir s’exécuter.

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![Collage de plusieurs lignes de code à l’aide de la commande Envoyer vers Interactive](media/getting-started-interactive-5.png)

1. Étant donné que la définition de fonction se trouve à nouveau dans l’historique REPL en tant qu’unité unique, vous pouvez facilement revenir en arrière et apporter les modifications souhaitées, puis tester à nouveau la fonction.

1. Lorsque vous êtes satisfait du code que vous avez écrit, vous pouvez le sélectionner dans la fenêtre interactive, cliquer dessus avec le bouton droit et sélectionner **Copier le code**, puis le coller dans l’éditeur. La commande **Copier le code** a la particularité d’omettre automatiquement toute sortie ainsi que les textes d’invité >>> et .... Par exemple, si vous utilisez la commande avec la sélection ci-dessous :

  ![Commande Copier le code dans la fenêtre interactive](media/getting-started-interactive-6.png)

  vous allez coller uniquement ce qui suit :

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. Enfin, la fenêtre interactive fournit un certain nombre de métacommandes qui vous permettent de charger des fichiers, de réinitialiser l’environnement sans perdre l’historique et d’insérer des commentaires à mesure que vous écrivez du code. Pour plus d’informations, consultez la page [Fenêtres interactives - Métacommandes](interactive-repl.md#meta-commands).

### <a name="going-deeper"></a>Pour aller plus loin

- [Utilisation de la fenêtre interactive](interactive-repl.md)
- [Utilisation d’IPython REPL](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>Exécution du code dans le débogueur

Au-delà de ses fonctions de gestion de projets, de son expérience de modification et de sa fenêtre interactive, Visual Studio offre une prise en charge complète du débogage pour le code Python.

1. Modifiez le code dans votre fichier hello.py pour correspondre à ce qui suit :

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. Vérifiez que le code fonctionne correctement en sélectionnant **Démarrer** dans la barre d’outils, en appuyant sur F5 ou en sélectionnant la commande de menu **Debug > Start Debugging** (Déboguer > Démarrer le débogage). Cette commande exécute le code dans le débogueur, mais étant donné que nous n’avons pas défini les points d’arrêt, vous verrez qu’elle imprime simplement un modèle wave pour quelques itérations. Appuyez sur n’importe quelle touche pour fermer la fenêtre de sortie à ce stade.

    > [!Tip]
    > Pour fermer automatiquement la fenêtre de sortie à la fin du programme, remplacez l’appel `main()` par le code suivant :
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```

1. Définissez un point d’arrêt sur la première ligne de la fonction `main` en cliquant dans la marge grise à gauche en regard de cette ligne, ou en plaçant le signe insertion dans cette ligne et en utilisant la commande *Déboguer > Basculer le point d’arrêt** (F9). Un point rouge apparaît dans la marge grise pour indiquer le point d’arrêt (comme indiqué par la flèche bleue ci-dessous) :

    ![Définition d'un point d'arrêt](media/getting-started-debugging-1.png)

1. Redémarrez le débogueur ; vous voyez maintenant que le code s’arrête sur la ligne sur laquelle est défini ce point d’arrêt. Vous pouvez ici voir la pile des appels et examiner les variables locales dans la fenêtre Variables locales :

    ![Expérience de l’interface utilisateur des points d’arrêt pour Python](media/getting-started-debugging-2.png)

1. Parcourez quelques itérations de la boucle `for` ligne par ligne à l’aide de la touche F10, de la commande **Déboguer > Pas à pas principal** ou du bouton de la barre d’outils Pas à pas principal. Cela signifie que le débogueur exécute chaque appel à `make_dot_string`, mais qu’il ne va pas s’arrêter à l’intérieur de cette fonction (sauf si vous définissez un point d’arrêt).

1. Dans la barre d’outils, les trois boutons d’exécution pas à pas ci-dessous sont, de gauche à droite : Pas à pas détaillé, Pas à pas principal et Pas à pas sortant :

    ![Boutons de la barre d’outils Pas à pas](media/getting-started-debugging-3.png)

1. Exécutez maintenant `make_dot_string` à l’aide de la commande Pas à pas détaillé (F11). Vous verrez que vous allez passer de la boucle `for` à cette fonction. Si vous utilisez de nouveau la fonction pas à pas, vous revenez à la boucle `for`, mais s’il existe des lignes supplémentaires dans la fonction, vous devez les parcourir une à une. Si vous êtes dans une fonction et que vous souhaitez exécuter le reste de ses lignes et retourner au code appelant, utilisez la fonction Pas à pas sortant (MAJ + F11).

1. Pour poursuivre l’exécution du code jusqu’au prochain point d’arrêt (ou jusqu’à la fin du programme), appuyez de nouveau sur F5 ou sélectionnez le bouton de la barre d’outils **Continuer** ou la commande **Déboguer > Continuer**. Étant donné que vous avez défini un point d’arrêt dans la boucle `for`, vous allez vous arrêter sur l’itération suivante.

1. Il peut être assez fastidieux de parcourir des centaines d’itérations d’une boucle. Aussi, vous avez la possibilité d’ajouter une condition au point d’arrêt défini précédemment pour que le code s’arrête uniquement lorsque la valeur de `i` dépasse une certaine valeur, par exemple 1600. Pour ce faire, cliquez sur le point rouge représentant le point d’arrêt et sélectionnez **Condition...**. Dans la fenêtre Paramètres de point d’arrêt qui s’affiche, entrez `i > 1600` comme expression et sélectionnez **Fermer**. Appuyez maintenant sur F5 pour continuer. Vous remarquerez que le programme s’exécute pendant un certain temps avant de s’arrêter de nouveau. 

    ![Définition d’une condition de point d’arrêt](media/getting-started-debugging-4.png)

1. Pour exécuter le programme, vous pouvez basculer de nouveau le point d’arrêt et appuyez sur F5. Visual Studio repasse en mode d’édition une fois le débogage terminé.

### <a name="going-deeper"></a>Pour aller plus loin

- [Débogage](debugging.md).
- Consultez également l’article [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md) (Débogage dans Visual Studio) pour accéder à une documentation complète sur les fonctionnalités de débogage de Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

Outre les liens « Pour aller plus loin » fournis précédemment, les rubriques suivantes décrivent des fonctionnalités supplémentaires de l’expérience Python dans Visual Studio :

- Pour voir comment Visual Studio se connecte à une instance Azure App Service, voir [Publishing a Python web application to Azure](publishing-to-azure.md) (Publication d’une application Web Python dans Azure).
- Pour découvrir comment gérer différents environnements aussi bien globalement que pour des projets individuels, y compris des environnements virtuels, voir [Python Environments](python-environments.md) (Environnements Python).
- Visual Studio offre la possibilité de déboguer votre application sur des serveurs distants, comme décrit dans les articles [Cross-platform Remote Debugging](debugging-cross-platform-remote.md) (Débogage à distance inter-plateforme) et [Azure Remote Debugging](debugging-azure-remote.md) (Débogage à distance dans Azure).
- Vous pouvez évaluer les performances de votre code Python à l’aide d’un [profilage Visual Studio](profiling.md).
- Les tests unitaires écrits en Python s’intègrent directement avec l’Explorateur de tests Visual Studio, comme indiqué dans l’article relatif aux [tests unitaires](unit-testing.md).

