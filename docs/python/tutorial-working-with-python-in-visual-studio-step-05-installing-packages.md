---
title: Tutoriel Python dans Visual Studio - étape 5, installer des packages
titleSuffix: ''
description: Étape 5 d’une procédure pas à pas portant sur les fonctionnalités de Python dans Visual Studio qui présente les fonctionnalités de Visual Studio permettant de gérer les packages dans un environnement Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372911"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Étape 5 : Installer des packages dans votre environnement Python

**Étape précédente : [Exécuter du code dans le débogueur](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La communauté des développeurs Python a produit des milliers de packages utiles, que vous pouvez incorporer dans vos propres projets. Visual Studio fournit une interface utilisateur permettant de gérer les packages dans vos environnements Python.

## <a name="view-environments"></a>Afficher les environnements

1. Sélectionnez la **commande de** > menu View**Other Windows** > **Python Environments.** La fenêtre **Python Environments** s’ouvre en tant que pair pour **Solution Explorer** et montre les différents environnements à votre disposition. La liste montre les deux environnements que vous avez installés à l’aide de l’installateur Visual Studio et ceux que vous avez installés séparément. Cela inclut les environnements globaux, virtuels et conda. L’environnement en gras est l’environnement par défaut qui est utilisé pour les nouveaux projets. Pour plus d’informations sur le travail avec les environnements, voir [Comment créer et gérer les environnements Python dans les environnements Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Fenêtre Environnements Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Vous pouvez également ouvrir la fenêtre Python Environments en cliquant sur la fenêtre Solution Explorer et en utilisant le raccourci clavier CtrlMDK, CtrlMD. Si le raccourci ne fonctionne pas et que vous ne trouvez pas la fenêtre Python Environments dans le menu, il est possible que vous n’ayez pas installé la charge de travail Python. Découvrez [comment installer le support Python dans Visual Studio](installing-python-support-in-visual-studio.md) pour obtenir des conseils sur la façon d’installer Python.

2. L’onglet **Aperçu** de l’environnement permet un accès rapide à une fenêtre **interactive** pour cet environnement ainsi qu’au dossier d’installation et aux interprètes de l’environnement. Par exemple, sélectionnez **fenêtre interactive ouverte** et une fenêtre **interactive** pour cet environnement spécifique apparaît dans Visual Studio.

3. Maintenant, créez un nouveau projet avec **File** > **New** > **Project**, en sélectionnant le modèle **d’application Python.** Dans le fichier de code qui apparaît, coller le code suivant, qui crée une onde de cosine comme les étapes de tutoriel précédente, seulement cette fois tracé graphiquement. Alternativement, vous pouvez utiliser le projet que vous avez déjà créé et remplacer le code. 

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

4. Avec un projet Python ouvert, vous pouvez également ouvrir la fenêtre Python Environments de Solution Explorer en cliquant à droite sur Python Environments et en sélectionnant **View All Python Environments**

   ![Environnement](media/environments/environments-view-all-2019.png)

5. En regardant la fenêtre de l’éditeur, vous `numpy` `matplotlib` remarquerez que si vous planez au-dessus des déclarations et d’importation qu’ils ne sont pas résolus. C’est parce que les paquets n’ont pas été installés dans l’environnement mondial par défaut.

   ![Importation de paquets non résolues](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Installer des paquets à l’aide de la fenêtre Python Environments

1. De la fenêtre Python Environments, cliquez sur l’environnement par défaut pour les nouveaux projets Python et sélectionnez l’onglet **Paquets.** Vous verrez ensuite une liste de paquets qui sont actuellement installés dans l’environnement.

   ![Packages installés dans un environnement](media/environments/environments-installed-packages-2019.png)

2. Installez `matplotlib` en entrant son nom dans le champ de recherche, puis en sélectionnant la **commande Run : installer l’option matplotlib.** Cela permettra `matplotlib`d’installer, ainsi que tous les paquets, il dépend (dans ce cas qui comprend `numpy`).

   ![Installation de matplotlib dans l’environnement](media/environments/environments-add-matplotlib-2019.png)

5. Acceptez l’élévation si vous y êtes invité.

6. Une fois l’emballage installé, il apparaît dans la fenêtre **Python Environments.** La marque **X** à droite du package permet de le désinstaller.

   ![Fin de l’installation de matplotlib dans l’environnement](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Une petite barre de progression peut apparaître sous l’environnement pour indiquer que Visual Studio est la construction de sa base de données IntelliSense pour le paquet nouvellement installé. L’onglet **IntelliSense** affiche également des informations plus détaillées. Sachez que jusqu’à ce que cette base de données soit terminée, les fonctionnalités d’IntelliSense comme l’auto-achèvement et la vérification syntaxique ne seront pas actives dans l’éditeur pour ce paquet.
   > 
   > Visual Studio 2017 version 15.6 et utilise plus tard une méthode différente et plus rapide pour travailler avec IntelliSense, et affiche un message à cet effet sur l’onglet **IntelliSense.**

## <a name="run-the-program"></a>Exécuter le programme

1. Maintenant que [matplotlib](https://matplotlib.org/) est installé, exécuter le programme avec (**F5**) ou sans le débbugger (**Ctrl**+**F5**) pour voir la sortie:

   ![Sortie de l’exemple matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Travailler avec Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Approfondir la question

- [Environnements Python](managing-python-environments-in-visual-studio.md)
- [En savoir plus sur Django dans Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [En savoir plus sur Flask dans Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
