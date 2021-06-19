---
title: 'Tutoriel : Python dans Visual Studio, étape 1, créer un projet'
titleSuffix: ''
description: Vue d’ensemble et étape 1 d’une procédure pas à pas principale qui présente les fonctionnalités de Python dans Visual Studio, notamment les prérequis et la création d’un projet Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: 927faad404e50a4cf31579c56882bf50208bbb21
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390696"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Tutoriel : Utiliser Python dans Visual Studio

Python est un langage de programmation très apprécié, car il est fiable, souple, simple d’emploi et utilisable sur tous les systèmes d’exploitation. Il est soutenu à la fois par une solide communauté de développeurs et par de nombreuses bibliothèques gratuites. Le langage prend en charge toutes les méthodes de développement, notamment les applications Web, les services web, les applications pour poste de travail, les scripts et le calcul scientifique, et il est utilisé par une multitude d’universités, de scientifiques et de développeurs, aussi bien occasionnels que professionnels.

Visual Studio fournit une prise en charge du langage de premier ordre pour Python. Ce didacticiel vous guide tout au long des étapes suivantes :

- [Étape 0 : Installation](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Étape 1 : Créer un projet Python (cet article)](#step-1-create-a-new-python-project)
- [Étape 2 : Écrire et exécuter du code pour voir à l’œuvre Visual Studio IntelliSense](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Étape 3 : créer plus de code dans la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Étape 4 : Exécuter le programme terminé dans le débogueur Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Étape 5 : Installer des packages et gérer des environnements Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Étape 6 : Utiliser Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Étape 1 : Créer un projet Python

Un *projet* représente la façon dont Visual Studio gère tous les fichiers qui constituent ensemble une application, notamment le code source, les ressources, les configurations, etc. Un projet formalise et maintient la relation entre tous les projets fichiers du projet, ainsi que des ressources externes qui sont partagées entre plusieurs projets. Ainsi, un projet vous permet de développer beaucoup plus facilement votre application qu’en gérant simplement les relations d’un projet dans des dossiers, des scripts, des fichiers texte ad hoc, et même dans votre esprit.

Dans ce didacticiel, vous commencez avec un projet simple contenant un seul fichier de code vide.

1. Dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet** (**CTRL** + **MAJ** + **N**), qui affiche la boîte de dialogue **nouveau projet** . Ici, vous parcourez les modèles pour différents langages, puis vous en sélectionnez un pour votre projet et vous spécifiez l’emplacement où Visual Studio place les fichiers.

1. Pour afficher les modèles Python, sélectionnez l’option  >  **python** installé sur la gauche, ou recherchez « Python ». L’utilisation de la recherche est un bon moyen de trouver un modèle quand vous ne vous souvenez pas de son emplacement dans l’arborescence des langages.

    ![Boîte de dialogue Nouveau projet avec les projets Python](media/vs-getting-started-python-01-new-project.png)

    Notez que la prise en charge de Python dans Visual Studio comprend un certain nombre de modèles de projet, notamment des applications web utilisant les frameworks Bottle, Flask et Django. Dans le cadre de cette procédure pas à pas, nous allons cependant commencer avec un projet vide.

1. Sélectionnez le modèle **Application Python**, spécifiez un nom pour le projet, puis sélectionnez **OK**.

1. Après quelques instants, Visual Studio affiche la structure du projet dans la fenêtre **Explorateur de solutions** (1). Le fichier de code par défaut est ouvert dans l’éditeur (2). La fenêtre **Propriétés** (3) s’affiche également pour afficher des informations supplémentaires pour tout élément sélectionné dans **Explorateur de solutions**, y compris son emplacement exact sur le disque.

    ![Explorateur de solutions avec un projet Python](media/vs-getting-started-python-02-windows.png)

1. Prenez quelques instants pour vous familiariser avec **Explorateur de solutions**, qui vous permet de parcourir les fichiers et les dossiers de votre projet.

    ![L’Explorateur de solutions développé pour montrer différentes fonctionnalités](media/vs-getting-started-python-03-solution-explorer.png)

    (1) mis en surbrillance en gras, il s’agit de votre projet, en utilisant le nom que vous avez donné dans la boîte de dialogue **nouveau projet** . Sur le disque, ce projet est représenté par un fichier *.pyproj* au sein du dossier de projet.

    (2) Au niveau le plus élevé, vous voyez une *solution*, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier *.sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes. Par exemple, si vous écrivez une extension C++ pour votre application Python, ce projet C++ peut se trouver dans la même solution. La solution peut également contenir un projet pour un service web, ainsi que des projets pour les programmes de test dédiés.

    (3) Dans le projet, vous voyez les fichiers sources. Dans le cas présent, il s’agit d’un unique fichier *.py*. La sélection d’un fichier affiche ses propriétés dans la fenêtre **Propriétés** . Le fait de double-cliquer sur un fichier l’ouvre d’une façon appropriée pour ce fichier.

    (4) Le nœud **Environnements Python** figure également sous le projet. Une fois qu’il est développé, vous voyez les interpréteurs Python disponibles. Développez un nœud d’interpréteur pour voir les bibliothèques qui sont installées dans cet environnement (5).

    Cliquez avec le bouton droit sur un nœud ou un élément de **Explorateur de solutions** pour accéder à un menu de commandes applicables. Par exemple, la commande **Renommer** vous permet de changer le nom d’un nœud ou d’un élément, y compris le projet et la solution.

## <a name="next-step"></a>Étape suivante

> [!div class="nextstepaction"]
> [Écrire et exécuter du code](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Approfondir la question

- [Projets python dans Visual Studio](managing-python-projects-in-visual-studio.md).
- [En savoir plus sur le langage Python sur python.org](https://www.python.org)
- [Python pour les débutants](https://www.python.org/about/gettingstarted/) (python.org)
