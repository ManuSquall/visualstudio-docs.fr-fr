---
title: "Utilisation de Python dans Visual Studio, Étape 4 | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 90f22c2f7626b09f230c497c54c8a37511ea1b0b
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-4-running-code-in-the-debugger"></a>Étape 4 : Exécution du code dans le débogueur

**Étape précédente : [Utilisation de la fenêtre REPL interactive](vs-tutorial-01-03.md)**

En plus de ses fonctions de gestion de projets, de son expérience d’édition enrichie et de sa fenêtre interactive, Visual Studio offre des fonctionnalités complètes de débogage pour le code Python. Dans le débogueur, vous pouvez exécuter votre code pas à pas, notamment chaque itération d’une boucle. Vous pouvez également interrompre le programme chaque fois que certaines conditions sont remplies. À tout moment, quand le programme est en pause dans le débogueur, vous pouvez examiner l’état de l’ensemble du programme et changer la valeur des variables. Ces actions sont essentielles pour le suivi des bogues du programme et fournissent également des aides très utiles pour suivre avec précision le flux exact du programme.

1. Remplacez le code du fichier `PythonApplication1.py` par ceci. Cette variation du code se développe `make_dot_string`, ce qui vous permet d’examiner ses étapes discrètes dans le débogueur. Il place également la boucle `for` dans une fonction `main` et l’exécute explicitement en appelant cette fonction :

    ```python  
    import sys  
    from math import sin, cos, radians    
    
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        str = ' ' * numspaces + 'o'                  # place 'o' after the spaces
        return str
    
    def main():  
        for i in range(0, 1800, 12):
            s = make_dot_string(i)  
            print(s)  
            
    main()
    ```  

1. Vérifiez que le code fonctionne correctement en appuyant sur F5 ou en sélectionnant la commande de menu **Déboguer > Démarrer le débogage**. Cette commande exécute le code dans le débogueur mais, comme vous n’avez rien fait pour interrompre le programme pendant son exécution, il affiche simplement un motif de vague pour quelques itérations. Une touche enfoncée pour la fenêtre Sortie.

    > [!Tip]
    > Pour fermer automatiquement la fenêtre de sortie à la fin du programme, remplacez l’appel `main()` par le code suivant :
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```    

1. Définissez un point d’arrêt sur la première instruction `for` en cliquant une fois dans la marge grise à gauche en regard de cette ligne, ou en plaçant le signe insertion dans cette ligne et en utilisant la commande **Déboguer > Basculer le point d’arrêt** (F9). Un point rouge apparaît dans la marge grise pour indiquer le point d’arrêt (comme indiqué par la flèche) :

    ![Définition d'un point d'arrêt](media/vs-getting-started-python-18-debugging1.png)

1. Redémarrez le débogueur (F5) ; vous voyez maintenant que l’exécution du code s’arrête sur la ligne où ce point d’arrêt est défini. Vous pouvez examiner ici la pile des appels et les variables locales. Les variables qui sont dans l’étendue apparaissent dans la fenêtre **Automatique** quand elles sont définies ; vous pouvez également basculer vers la vue **Variables locales** dans le bas de cette fenêtre pour afficher toutes les variables trouvées par Visual Studio dans l’étendue active (notamment les fonctions), même avant qu’elles soient définies :

    ![Expérience de l’interface utilisateur des points d’arrêt pour Python](media/vs-getting-started-python-19-debugging2b.png)

1. Observez la barre d’outils de débogage (voir ci-dessous) en haut de la fenêtre Visual Studio. Cette barre d’outils fournit un accès rapide aux commandes de débogage les plus courantes (qui sont également accessibles sur le menu **Débogage**) :

    ![Boutons principaux de la barre d’outils de débogage](media/vs-getting-started-python-20-debugging3.png)

    Les boutons sont les suivants, de gauche à droite :
    - **Continuer** (F5) exécute le programme jusqu’au point d’arrêt suivant ou jusqu’à la fin du programme.
    - **Interrompre tout** (Ctrl+Alt+Pause) interrompt un programme dont l’exécution est longue.
    - **Arrêter le débogage** (Maj+F5) arrête le programme où qu’il en soit et quitte le débogueur.
    - **Redémarrer** (Ctrl+Maj+F5) arrête le programme où qu’il en soit et le redémarre à partir du début dans le débogueur.
    - **Afficher l’instruction suivante** (Alt+Num *) passe à la ligne de code suivante à exécuter. Ceci est spécialement utile quand vous naviguez au sein de votre code pendant une session de débogage et que vous voulez retourner rapidement au point où le débogueur est en suspens.
    - **Pas à pas détaillé** (F11) exécute la ligne de code suivante, en entrant dans les fonctions appelées.
    - **Pas à pas principal** (F10) exécute la ligne de code suivante, sans entrer dans les fonctions appelées.
    - **Pas à pas sortant** (Maj+F11) exécute le reste de la fonction en cours et s’interrompt dans le code appelant.

1. Faites un pas à pas principal de l’instruction `for` en utilisant **Pas à pas principal**. *L’exécution pas à pas* signifie que le débogueur exécute la ligne de code active, y compris tous les appels de fonction, puis s’interrompt à nouveau immédiatement. Notez comment la variable `i` est maintenant définie dans les fenêtres **Variables locales** et **Automatique**.
 
1. Faites un pas à pas principal de la ligne de code suivante, qui appelle `make_dot_string` et s’interrompt. « Pas à pas principal » signifie ici spécifiquement que le débogueur exécute la totalité de `make_dot_string` et s’interrompt quand elle retourne. Le débogueur ne s’arrête pas à l’intérieur de cette fonction, sauf si un point d’arrêt distinct s’y trouve.

1. Continuez à demander un certain nombre de fois l’exécution en pas à pas principal du code, et observez comment les valeurs changent dans les fenêtres **Variables locales** ou **Automatique**.

1. Dans la fenêtre **Variables locales** ou **Automatique**, double-cliquez dans la colonne **Valeur** pour la variable `i` ou `s` et changez la valeur. Appuyez sur Entrée ou cliquez en dehors de cette valeur pour appliquer les modifications.

1. Continuez à parcourir le code pas à pas en utilisant **Pas à pas détaillé**. « Pas à pas détaillé » signifie que le débogueur entre à l’intérieur des appels de fonction pour lesquels il a des informations, de débogage, comme `make_dot_string`. Une fois à l’intérieur de `make_dot_string`, vous pouvez examiner ses variables locales et exécuter son code spécifiquement.
 
1. Continuez l’exécution pas à pas avec le pas à pas détaillé et notez que, quand vous atteignez la fin de `make_dot_string`, le pas suivant retourne à la boucle `for` avec la nouvelle valeur de retour dans la variable `s`. Quand vous revenez à l’instruction `print`, notez que Pas à pas détaillé sur `print` n’entre pas dans cette fonction. La raison en est que `print` n’est pas écrit en Python, mais qu’il s’agit de code natif au sein du runtime Python.

1. Continuez à utiliser Pas à pas détaillé jusqu’à revenir à mi-chemin dans `make_dot_string`. Utilisez ensuite **Pas à pas sortant** et notez que vous revenez alors à la boucle `for`. Avec le Pas à pas sortant, le débogueur exécute le reste de la fonction, puis s’interrompt automatiquement dans le code appelant. Ceci est très utile quand vous avez exécuté pas à pas une partie d’une fonction longue que vous souhaitez déboguer, mais que vous n’avez pas besoin d’en parcourir le reste pas à pas et que vous ne voulez pas définir un point d’arrêt explicite dans le code appelant.

1. Pour continuer l’exécution du programme jusqu’à atteindre le point d’arrêt suivant, utilisez **Continuer** (F5). Étant donné que vous avez défini un point d’arrêt dans la boucle `for`, vous allez vous arrêter sur l’itération suivante.

1. Parcourir pas à pas des centaines d’itérations d’une boucle peut être fastidieux : Visual Studio vous permet donc d’ajouter une *condition* à un point d’arrêt. Le débogueur interrompt alors le programme au point d’arrêt seulement quand la condition est remplie. Par exemple, vous pouvez utiliser une condition avec le point d’arrêt sur l’instruction `for` pour qu’elle s’interrompe seulement quand la valeur de `i` dépasse 1 600. Pour définir cette condition, cliquez avec le bouton droit sur le point rouge représentant le point d’arrêt et sélectionnez **Conditions...** (Alt+F9,C). Dans la fenêtre contextuelle **Paramètres de point d’arrêt** qui s’affiche, entrez `i > 1600` comme expression et sélectionnez **Fermer**. Appuyez sur F5 pour continuer et notez que le programme exécute de nombreuses itérations avant l’arrêt suivant. 

    ![Définition d’une condition de point d’arrêt](media/vs-getting-started-python-21-debugging4.png)

1. Pour exécuter le programme jusqu’à son terme, désactivez le point d’arrêt en cliquant avec le bouton droit et en sélectionnant **Désactiver le point d’arrêt** (Ctrl+F9). Sélectionnez ensuite **Continuer** (ou appuyez sur F5) pour exécuter le programme. Quand le programme se termine, Visual Studio arrête sa session de débogage et retourne au mode Édition. Notez que vous pouvez également supprimer le point d’arrêt en cliquant sur le point qui y correspond, mais ceci supprime également toutes les conditions que vous avez définies.

> [!Tip]    
> Dans certaines situations, par exemple en cas d’échec du lancement de l’interpréteur Python lui-même, la fenêtre Sortie peut apparaître seulement brièvement, puis se fermer automatiquement sans vous donner la possibilité de visualiser les messages d’erreurs. Si cela se produit, cliquez avec le bouton dans l’Explorateur de solutions, sélectionnez **Propriétés**, sélectionnez l’onglet **Déboguer**, puis ajoutez `-i` au champ **Arguments de l’interpréteur**. Avec cet argument, l’interpréteur passe en mode interactif à la fin d’un programme, maintenant ainsi la fenêtre ouverte jusqu’à ce que vous entriez Ctrl+Z, Entrée pour quitter.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Installation de packages dans votre environnement Python](vs-tutorial-01-05.md)

### <a name="going-deeper"></a>Pour aller plus loin
- [Débogage](debugging.md).
- [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md) fournit une documentation complète sur les fonctionnalités de débogage de Visual Studio.
