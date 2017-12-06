---
title: "Fonctionnalité REPL IPython dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 856e8b3f13c5938dd6bd7ec1465bda9715636875
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-ipython-in-the-interactive-window"></a>Utilisation d’IPython dans la fenêtre interactive

La fenêtre interactive Visual Studio en mode IPython est un environnement de développement interactif convivial qui comporte des fonctionnalités de calcul parallèles interactives. Cette rubrique vous guide tout au long de l’utilisation d’IPython dans la fenêtre interactive Visual Studio, dans laquelle toutes les fonctionnalités de la [fenêtre interactive](interactive-repl.md) standard sont également disponibles.

Pour cette procédure pas à pas, vous devez avoir installé l’environnement [Anaconda](https://www.continuum.io), qui inclut IPython ainsi que les bibliothèques nécessaires.

> [!Note]
> IronPython ne prend pas en charge IPython, bien qu’il soit possible de le sélectionner dans le formulaire des options interactives. Pour plus d’informations, consultez la [demande de fonctionnalité](https://github.com/Microsoft/PTVS/issues/84).

1. Ouvrez Visual Studio, basculez vers la fenêtre Environnements Python (**Affichage > Autres fenêtres > Environnements Python**, puis sélectionnez l’environnement Python affiché quand vous avez démarré IPython.

1. Examinez l’onglet **Packages** (ou **pip**) et vérifiez que `IPython` et `matplotlib` sont répertoriés. Si ce n’est pas le cas, installez-les ici.

1. Sélectionnez l’onglet **Vue d’ensemble** et **Utiliser le mode interactif IPython**. (Dans Visual Studio 2015, sélectionnez **Configure interactive options** (Configurer les options interactives) pour ouvrir la boîte de dialogue **Options**, affectez à **Mode interactif** la valeur IPython, puis sélectionnez **OK**).    

1. Sélectionnez **Ouvrir une fenêtre interactive** pour afficher la fenêtre interactive en mode IPython. Vous devrez peut-être réinitialiser la fenêtre si vous venez de modifier le mode interactif. Vous devrez peut-être aussi appuyer sur Entrée si seule une invite >>> s’affiche.

    ![Fenêtre interactive en mode IPython](media/ipython-repl-03.png)

1. Entrez le code suivant :

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Après avoir entré la dernière ligne, vous devriez voir un graphique inline (que vous pouvez redimensionner en faisant glisser le coin inférieur droit, si vous le souhaitez).

    ![Graphique inline dans la fenêtre interactive](media/ipython-repl-04.png)

1. Au lieu d’effectuer une saisie dans la boucle REPL, vous pouvez écrire du code dans l’éditeur, le sélectionner, cliquer dessus avec le bouton droit et sélectionner la commande **Envoyer vers Interactive** (ou appuyer sur Ctrl+Entrée). Essayez de coller le code ci-dessous dans un nouveau fichier dans l’éditeur, de le sélectionner à l’aide des touches Ctrl+A, puis de l’envoyer dans la fenêtre interactive. (Notez que Visual Studio envoie le code en une seule unité pour éviter de vous donner des graphiques intermédiaires ou partiels. Notez également que, si vous n’avez pas un projet Python ouvert avec un autre environnement sélectionné, Visual Studio ouvre une fenêtre interactive pour n’importe quel environnement sélectionné par défaut dans la fenêtre **Environnements Python**.)

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
    
IPython comporte de nombreuses autres fonctions utiles, par exemple des fonctions de sortie vers l’interpréteur de commandes système, de substitution de variables, de capture de sortie, etc. Pour plus d’informations, consultez la [documentation IPython](http://ipython.org/documentation.html).

## <a name="related-topics"></a>Rubriques connexes

- Pour utiliser Jupyter facilement et sans installation, essayez gratuitement le [service hébergé Azure Notebooks](https://notebooks.azure.com/) qui vous permet de conserver et partager vos blocs-notes avec d’autres.

- Vous pouvez également exécuter Jupyter (anciennement IPython) sur votre propre machine virtuelle Windows ou Linux sur Azure. Pour plus d’informations, consultez [Création d’une machine virtuelle Azure, installation de Jupyter et exécution de Jupyter Notebook sur Azure](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).
