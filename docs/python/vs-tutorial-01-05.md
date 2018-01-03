---
title: "Utilisation de Python dans Visual Studio, Étape 5 | Microsoft Docs"
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
ms.workload: python
ms.openlocfilehash: 2acd8aebda03d7d9809563a6c1959c8dd69bf96e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>Étape 5 : Installation de packages dans votre environnement Python

**Étape précédente : [Exécution du code dans le débogueur](vs-tutorial-01-04.md)**

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

  La petite barre de progression sous l’environnement indique que Visual Studio crée sa base de données IntelliSense pour le package nouvellement installé. L’onglet **IntelliSense** affiche également des informations plus détaillées. Notez que tant que cette base de données n’est pas terminée, les fonctionnalités IntelliSense, comme la saisie semi-automatique et la vérification de la syntaxe, ne sont pas actives dans l’éditeur pour ce package.

1. Créez un projet avec **Fichier > Nouveau > Projet** en sélectionnant le modèle « Application Python ». Dans le fichier de code qui s’affiche, collez le code suivant, qui crée une courbe de la fonction cosinus comme dans les étapes du didacticiel précédent, mais cette fois avec seulement une représentation graphique :

    ```python
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt
    from math import radians

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Exécutez le programme avec (F5) ou sans (Ctrl+F5) le débogueur pour voir la sortie :

  ![Sortie de l’exemple matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utilisation de Git](vs-tutorial-01-06.md)

### <a name="going-deeper"></a>Pour aller plus loin

- [Environnements Python](python-environments.md)
