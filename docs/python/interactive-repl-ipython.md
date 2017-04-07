---
title: "Fonctionnalité REPL IPython dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
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
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>Utilisation de Python dans la fenêtre interactive

La fenêtre interactive Visual Studio en mode IPython est un environnement de développement interactif convivial qui comporte des fonctionnalités de calcul parallèles interactives. Dans cette rubrique, nous allons voir en détail comment utiliser IPython dans la fenêtre interactive Visual Studio. Pour cela, vous devez avoir installé l’environnement [Anaconda](https://www.continuum.io), qui inclut IPython ainsi que les bibliothèques nécessaires.

> [!Note]
> IronPython ne prend pas en charge IPython, bien qu’il soit possible de le sélectionner dans le formulaire des options interactives. Vous pouvez voter pour la [demande de fonctionnalité](https://github.com/Microsoft/PTVS/issues/84) ou l’implémenter si vous le souhaitez.

1. Assurez-vous que le package IPython est correctement installé en accédant à votre répertoire d’installation Python et en démarrant IPython en mode Pylab :

  ```bash
  ipython --pylab
  ```

1. Entrez les informations suivantes :

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. Si tout est correctement configuré, vous devriez obtenir quelque chose de similaire à ce qui suit :

    ![Sortie de la configuration IPython ](media/ipython-repl-01.png)

1. Ouvrez Visual Studio, basculez vers la fenêtre des environnements Python (**View > Other Windows > Python Environments** [Affichage > Autres fenêtres > Environnements Python]), puis sélectionnez votre environnement Python.
1. Examinez l’onglet **pip** et vérifiez que `IPython` et `matplotlib` sont répertoriés. Si ce n’est pas le cas, installez-les ici.
1. Dans l’onglet **Vue d’ensemble**, sélectionnez **Configure interactive options** (Configurer les options interactives), définissez **Mode interactif** sur IPython, puis cliquez sur **OK** :

    ![Définition du mode interactif sur IPython](media/ipython-repl-02.png)

1. Sélectionnez **Open interactive window** (Ouvrir une fenêtre interactive) pour afficher la fenêtre interactive en mode IPython avec PyLab. Vous devrez peut-être réinitialiser la fenêtre si vous venez de modifier le mode interactif :

    ![Fenêtre interactive en mode IPython](media/ipython-repl-03.png)

1. Entrez le code suivant :

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Après avoir entré la dernière ligne, vous devriez voir un graphique inline (que vous pouvez redimensionner en faisant glisser le coin inférieur droit, si vous le souhaitez).

    ![Graphique inline dans la fenêtre interactive](media/ipython-repl-04.png)

1. Au lieu d’effectuer une saisie dans la boucle REPL, vous pouvez écrire du code dans l’éditeur, le sélectionner, cliquer dessus avec le bouton droit et sélectionner la commande **Envoyer vers Interactive** (Ctrl-E,E). Essayez de coller le code ci-dessous dans l’éditeur, de le sélectionner à l’aide des touches Ctrl + A, puis de l’envoyer dans la fenêtre interactive. (Notez que lorsque Visual Studio envoie du code dans la fenêtre interactive, il l’envoie en une seule unité pour éviter de vous donner des graphiques intermédiaires ou partiels.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![Envoi de code de l’éditeur vers la fenêtre interactive](media/ipython-repl-05.png)

1. Pour afficher les graphiques en dehors de la fenêtre interactive, exécutez le code en utilisant cette fois la commande **Debug > Start without Debugging** (Déboguer > Démarrer sans débogage).
    
1. IPython comporte de nombreuses fonctions utiles, par exemple des fonctions de sortie vers l’interpréteur de commandes système, de substitution de variables, de capture de sortie, etc. Pour plus d’informations, reportez-vous au guide de référence IPython :

    ![Sortie vers l’interpréteur de commandes système](media/ipython-repl-06.png)

1. Vous pouvez également utiliser IPython en mode « bloc-notes » pour pouvoir utiliser n’importe quel navigateur sur n’importe quel système d’exploitation comme zone de dessin. Le moteur IPython principal peut résider en local sur votre ordinateur, ou bien distant. Azure prend en charge l’exécution [d’IPython sur une machine virtuelle Windows ou Linux](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook). Consultez également les [notebooks Azure en version préliminaire](https://notebooks.azure.com) pour accéder gratuitement à des blocs-notes Jupyter disponibles en tant que service sur Azure :

    ![IPython en mode bloc-notes](media/ipython-repl-07.png)

