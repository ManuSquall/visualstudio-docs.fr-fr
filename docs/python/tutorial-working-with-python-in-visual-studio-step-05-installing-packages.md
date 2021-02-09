---
title: Tutoriel Python dans Visual Studio - étape 5, installer des packages
titleSuffix: ''
description: Étape 5 d’une procédure pas à pas portant sur les fonctionnalités de Python dans Visual Studio qui présente les fonctionnalités de Visual Studio permettant de gérer les packages dans un environnement Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c47eacf0c9977e7342bfda17e03ea53728ee9215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901153"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Étape 5 : Installer des packages dans votre environnement Python

**Étape précédente : [Exécuter du code dans le débogueur](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La communauté des développeurs Python a produit des milliers de packages utiles, que vous pouvez incorporer dans vos propres projets. Visual Studio fournit une interface utilisateur permettant de gérer les packages dans vos environnements Python.

## <a name="view-environments"></a>Afficher les environnements

1. Sélectionnez la commande de menu **Afficher** d'  >  **autres**  >  **environnements Windows python** . La fenêtre **environnements python** s’ouvre en tant qu’homologue à **Explorateur de solutions** et affiche les différents environnements disponibles. La liste affiche les deux environnements que vous avez installés à l’aide du programme d’installation de Visual Studio et de ceux que vous avez installés séparément. Cela comprend les environnements globaux, virtuels et Conda. L’environnement en gras est l’environnement par défaut qui est utilisé pour les nouveaux projets. Pour plus d’informations sur l’utilisation des environnements, consultez [comment créer et gérer des environnements python dans des environnements Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Fenêtre Environnements Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Vous pouvez également ouvrir la fenêtre environnements Python en sélectionnant la fenêtre de Explorateur de solutions et en utilisant le raccourci clavier **CTRL + K, Ctrl + '** . Si le raccourci ne fonctionne pas et que vous ne trouvez pas la fenêtre environnements python dans le menu, vous n’avez peut-être pas installé la charge de travail Python. Pour plus d’informations sur l’installation de Python [, consultez Comment installer la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md) .

2. L’onglet **vue d’ensemble** de l’environnement fournit un accès rapide à une fenêtre **interactive** pour cet environnement, ainsi que le dossier d’installation et les interpréteurs de l’environnement. Par exemple, sélectionnez **ouvrir une fenêtre interactive** et une fenêtre **interactive** pour cet environnement spécifique s’affiche dans Visual Studio.

3. À présent, créez un nouveau projet avec **fichier**  >  **nouveau**  >  **projet**, en sélectionnant le modèle **application python** . Dans le fichier de code qui s’affiche, collez le code suivant, qui crée une onde cosinus comme pour les étapes précédentes du didacticiel, uniquement cette fois tracée graphiquement. Vous pouvez également utiliser le projet que vous avez créé précédemment et remplacer le code.

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

4. Quand un projet Python est ouvert, vous pouvez également ouvrir la fenêtre environnements Python à partir de Explorateur de solutions en cliquant avec le bouton droit sur **environnements python** et en sélectionnant **Afficher tous les environnements python** .

   ![Environnement](media/environments/environments-view-all-2019.png)

5. Si vous examinez la fenêtre de l’éditeur, vous remarquerez que si vous pointez sur les `numpy` `matplotlib` instructions et importez celles-ci, elles ne sont pas résolues. Cela est dû au fait que les packages n’ont pas été installés dans l’environnement global par défaut.

   ![Importation de package non résolue](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Installer des packages à l’aide de la fenêtre environnements python

1. Dans la fenêtre environnements Python, sélectionnez l’environnement par défaut pour les nouveaux projets Python, puis choisissez l’onglet **packages** . La liste des packages actuellement installés dans l’environnement s’affiche.

   ![Packages installés dans un environnement](media/environments/environments-installed-packages-2019.png)

2. Installez `matplotlib` en entrant son nom dans le champ de recherche, puis en sélectionnant l’option **exécuter la commande : PIP install matplotlib** . Cela installera `matplotlib` , ainsi que tous les packages dont il dépend (dans le cas présent, il s’agit de `numpy` ).

   ![Installation de matplotlib dans l’environnement](media/environments/environments-add-matplotlib-2019.png)

5. Acceptez l’élévation si vous y êtes invité.

6. Une fois le package installé, il apparaît dans la fenêtre **environnements python** . La marque **X** à droite du package permet de le désinstaller.

   ![Fin de l’installation de matplotlib dans l’environnement](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Une petite barre de progression peut apparaître sous l’environnement pour indiquer que Visual Studio crée sa base de données IntelliSense pour le package nouvellement installé. L’onglet **IntelliSense** affiche également des informations plus détaillées. Sachez que jusqu’à ce que cette base de données soit terminée, les fonctionnalités IntelliSense telles que la saisie semi-automatique et la vérification de la syntaxe ne seront pas actives dans l’éditeur de ce package.
   >
   > Visual Studio 2017 version 15,6 et les versions ultérieures utilisent une méthode différente et plus rapide pour travailler avec IntelliSense, et affiche un message à cet effet sous l’onglet **IntelliSense** .

## <a name="run-the-program"></a>Exécuter le programme

1. Maintenant que [matplotlib](https://matplotlib.org/) est installé, exécutez le programme avec (**F5**) ou sans le débogueur (**CTRL** + **F5**) pour afficher la sortie :

   ![Sortie de l’exemple matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Utiliser Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Approfondir la question

- [Environnements Python](managing-python-environments-in-visual-studio.md)
- [En savoir plus sur Django dans Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [En savoir plus sur Flask dans Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
