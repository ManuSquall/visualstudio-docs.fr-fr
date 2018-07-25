---
title: 'Utilisation du didacticiel Python - Étape 5 : Installation de packages'
description: Étape 5 d’une procédure pas à pas portant sur les fonctionnalités de Python dans Visual Studio qui présente les fonctionnalités de Visual Studio permettant de gérer les packages dans un environnement Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: d67ec84271534de84de588cd29376e2cdb437294
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37055979"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Étape 5 : Installer des packages dans votre environnement Python

**Étape précédente : [Exécution du code dans le débogueur](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La communauté des développeurs Python a produit des milliers de packages utiles, que vous pouvez incorporer dans vos propres projets. Visual Studio fournit une interface utilisateur permettant de gérer les packages dans vos environnements Python.

1. Sélectionnez la commande de menu **Affichage > Other Windows (Autres fenêtres) > Environnements Python**. La fenêtre **Environnements Python** s’ouvre de façon similaire à l’Explorateur de solutions et montre les différents environnements disponibles. La liste inclut les environnements que vous avez installés avec le programme d’installation de Visual Studio et ceux que vous avez installés séparément. L’environnement en gras est l’environnement par défaut qui est utilisé pour les nouveaux projets.

  ![Fenêtre Environnements Python](media/environments-default-view-blue.png)

1. L’onglet **Vue d’ensemble** de l’environnement fournit un accès rapide à une fenêtre interactive pour cet environnement, ainsi qu’au dossier d’installation et aux interpréteurs de l’environnement. Par exemple, sélectionnez **Ouvrir une fenêtre interactive** : une fenêtre interactive pour cet environnement spécifique apparaît alors dans Visual Studio.

1. Sélectionnez l’onglet **Packages** : vous voyez une liste des packages qui sont actuellement installés dans l’environnement.

  ![Packages installés dans un environnement](media/environments-installed-packages-blue.png)

1. Installez `matplotlib` en entrant son nom dans le champ de recherche, puis sélectionnez `pip install`

  ![Installation de matplotlib dans l’environnement](media/environments-add-matplotlib1.png)

1. Acceptez l’élévation si vous y êtes invité.

1. Une fois que le package est installé, il apparaît dans la fenêtre Environnements Python. La marque **X** à droite du package permet de le désinstaller.

  ![Fin de l’installation de matplotlib dans l’environnement](media/environments-add-matplotlib2.png)

  Une petite barre de progression peut apparaître sous l’environnement pour indiquer que Visual Studio crée sa base de données IntelliSense pour le package nouvellement installé. L’onglet **IntelliSense** affiche également des informations plus détaillées. Notez que tant que cette base de données n’est pas terminée, les fonctionnalités IntelliSense, comme la saisie semi-automatique et la vérification de la syntaxe, ne sont pas actives dans l’éditeur pour ce package.

  Notez que **Visual Studio 2017 versions 15.6** et ultérieures utilise une méthode différente et plus rapide pour travailler avec IntelliSense, et affiche un message à cet effet sous l’onglet **IntelliSense**.

1. Créez un projet avec **Fichier > Nouveau > Projet** en sélectionnant le modèle « Application Python ». Dans le fichier de code qui s’affiche, collez le code suivant, qui crée une courbe de la fonction cosinus comme dans les étapes du didacticiel précédent, mais cette fois avec seulement une représentation graphique :

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Exécutez le programme avec (F5) ou sans (Ctrl+F5) le débogueur pour voir la sortie :

  ![Sortie de l’exemple matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Utilisation de Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="go-deeper"></a>Approfondir la question

- [Environnements Python](managing-python-environments-in-visual-studio.md)
