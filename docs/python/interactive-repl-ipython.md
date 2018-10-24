---
title: IPython REPL (fenêtre interactive)
description: Utilisation de la fenêtre interactive Visual Studio en mode IPython pour un environnement de développement interactif convivial avec des fonctionnalités de calcul parallèles interactives.
ms.date: 06/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 28fb0bdb181b1f4f2c08112e40d6236db22b7a08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918920"
---
# <a name="use-ipython-in-the-interactive-window"></a>Utiliser IPython dans la fenêtre interactive

La **fenêtre interactive** Visual Studio en mode IPython est un environnement de développement interactif avancé, mais convivial, qui comporte des fonctionnalités de calcul parallèles interactives. Cet article vous guide tout au long de l’utilisation d’IPython dans la **fenêtre interactive** Visual Studio, dans laquelle toutes les fonctionnalités de la [fenêtre interactive](python-interactive-repl-in-visual-studio.md) standard sont également disponibles.

Pour cette procédure pas à pas, vous devez avoir installé l’environnement [Anaconda](https://www.continuum.io), qui inclut IPython ainsi que les bibliothèques nécessaires.

> [!Note]
> IronPython ne prend pas en charge IPython, bien qu’il soit possible de le sélectionner dans le formulaire des **options interactives**. Pour plus d’informations, consultez la [demande de fonctionnalité](https://github.com/Microsoft/PTVS/issues/84).

1. Ouvrez Visual Studio, basculez vers la fenêtre **Environnements Python** (**Affichage** > **Autres fenêtres** > **Environnements Python**), puis sélectionnez un environnement Anaconda.

2. Examinez l’onglet **Packages (Conda)** (qui peut être intitulé **pip** ou **Packages**) pour cet environnement afin de vérifier que `ipython` et `matplotlib` sont répertoriés. Si ce n’est pas le cas, installez-les ici. (Consultez [Fenêtre Environnements Python - Onglet Packages](python-environments-window-tab-reference.md).)

3. Sélectionnez l’onglet **Vue d’ensemble** et **Utiliser le mode interactif IPython**. (Dans Visual Studio 2015, sélectionnez **Configure interactive options** (Configurer les options interactives) pour ouvrir la boîte de dialogue **Options**, affectez à **Mode interactif** la valeur **IPython**, puis sélectionnez **OK**).

4. Sélectionnez **Ouvrir une fenêtre interactive** pour afficher la **fenêtre interactive** en mode IPython. Vous devrez peut-être réinitialiser la fenêtre si vous venez de changer le mode interactif. Vous devrez peut-être aussi appuyer sur **Entrée** si seule une invite >>> s’affiche pour obtenir une invite similaire à  **[2]**.

    ![Fenêtre interactive en mode IPython](media/ipython-repl-03.png)

5. Entrez le code suivant :

   ```python
   import matplotlib.pyplot as plt
   import numpy as np
  
   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Après avoir entré la dernière ligne, vous devriez voir un graphique inline (que vous pouvez redimensionner en faisant glisser le coin inférieur droit, si vous le souhaitez).

    ![Graphique inline dans la fenêtre interactive](media/ipython-repl-04.png)

7. Au lieu d’effectuer une saisie dans la boucle REPL, vous pouvez écrire du code dans l’éditeur, le sélectionner, cliquer dessus avec le bouton droit et sélectionner la commande **Envoyer vers Interactive** (ou appuyer sur **Ctrl**+**Entrée**). Essayez de coller le code ci-dessous dans un nouveau fichier dans l’éditeur, de le sélectionner à l’aide des touches **Ctrl**+**A**, puis de l’envoyer dans la **fenêtre interactive**. (Visual Studio envoie le code en une seule unité pour éviter de vous donner des graphes intermédiaires ou partiels. Si vous n’avez pas un projet Python ouvert avec un autre environnement sélectionné, Visual Studio ouvre une **fenêtre interactive** pour n’importe quel environnement sélectionné par défaut dans la fenêtre **Environnements Python**.)

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
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Envoi de code de l’éditeur vers la fenêtre interactive](media/ipython-repl-05.png)

8. Pour afficher les graphiques en dehors de la **fenêtre interactive**, exécutez le code en utilisant cette fois la commande **Déboguer** > **Démarrer sans débogage**.

IPython comporte de nombreuses autres fonctions utiles, par exemple des fonctions de sortie vers l’interpréteur de commandes système, de substitution de variables, de capture de sortie, etc. Pour plus d’informations, consultez la [documentation IPython](http://ipython.org/documentation.html).

### <a name="see-also"></a>Voir aussi

- Pour utiliser Jupyter facilement et sans installation, essayez gratuitement le [service hébergé Azure Notebooks](https://notebooks.azure.com/) qui vous permet de conserver et partager vos blocs-notes avec d’autres.

- [Azure Data Science Virtual Machine](/azure/machine-learning/data-science-virtual-machine/overview) est également préconfiguré pour exécuter les blocs-notes Jupyter avec un large éventail d’autres outils de science des données.
