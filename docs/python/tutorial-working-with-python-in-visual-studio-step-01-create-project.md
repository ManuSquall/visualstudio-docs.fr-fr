---
title: "Utilisation de Python dans Visual Studio, étape 1 - création d’un projet | Microsoft Docs"
description: "Étape 1 d’un didacticiel de base pour utiliser Python dans Visual Studio, présentant le didacticiel dans sa globalité, décrivant les conditions préalables requises, ainsi que le processus de création d’un nouveau projet Python."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 469494b2c0c4704ac1eab42d36934657adc2313d
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="working-with-python-in-visual-studio"></a>Utilisation de Python dans Visual Studio

Python est un langage de programmation très apprécié, car il est fiable, souple, simple d’emploi et utilisable sur tous les systèmes d’exploitation. Il est soutenu à la fois par une solide communauté de développeurs et par de nombreuses bibliothèques gratuites. Le langage prend en charge toutes les méthodes de développement, notamment les applications Web, les services web, les applications pour poste de travail, les scripts et le calcul scientifique, et il est utilisé par une multitude d’universités, de scientifiques et de développeurs, aussi bien occasionnels que professionnels.

Visual Studio fournit une prise en charge du langage de premier ordre pour Python. Ce didacticiel vous guide tout au long des étapes suivantes :

- [Étape 0 : Installation](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Étape 1 : Création d’un projet Python (cet article)](#step-1-create-a-new-python-project)
- [Étape 2 : Écriture et exécution du code pour voir à l’œuvre Visual Studio IntelliSense](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Étape 3 : Créer davantage de code dans la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Étape 4 : Exécuter le programme terminé dans le débogueur Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Étape 5 : Installation de packages et gestion des environnements Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Étape 6 : Utilisation de Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2017 avec la charge de travail Python installée. Pour obtenir des instructions, consultez [Étape 0](tutorial-working-with-python-in-visual-studio-step-00-installation.md).

## <a name="step-1-create-a-new-python-project"></a>Étape 1 : Créer un projet Python

Un *projet* représente la façon dont Visual Studio gère tous les fichiers qui constituent ensemble une application, notamment le code source, les ressources, les configurations, etc. Un projet formalise et maintient la relation entre tous les projets fichiers du projet, ainsi que des ressources externes qui sont partagées entre plusieurs projets. Ainsi, un projet vous permet de développer beaucoup plus facilement votre application qu’en gérant simplement les relations d’un projet dans des dossiers, des scripts, des fichiers texte ad hoc, et même dans votre esprit.

Dans ce didacticiel, vous commencez avec un projet simple contenant un seul fichier de code vide.

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau > Projet** (Ctrl+Maj+N) pour afficher la boîte de dialogue **Nouveau projet**. Ici, vous parcourez les modèles pour différents langages, puis vous en sélectionnez un pour votre projet et vous spécifiez l’emplacement où Visual Studio place les fichiers.

1. Pour voir les modèles Python, sélectionnez **Installés > Python** à gauche, ou effectuez une recherche sur « Python ». L’utilisation de la recherche est un bon moyen de trouver un modèle quand vous ne vous souvenez pas de son emplacement dans l’arborescence des langages.

    ![Boîte de dialogue Nouveau projet avec les projets Python](media/vs-getting-started-python-01-new-project.png)

    Notez que la prise en charge de Python dans Visual Studio comprend un certain nombre de modèles de projet, notamment des applications web utilisant les frameworks Bottle, Flask et Django. Dans le cadre de cette procédure pas à pas, nous allons cependant commencer avec un projet vide.

1. Sélectionnez le modèle **Application Python**, spécifiez un nom pour le projet, puis sélectionnez **OK**.

1. Après quelques instants, Visual Studio affiche la structure du projet dans la fenêtre **Explorateur de solutions** (1). Le fichier de code par défaut est ouvert dans l’éditeur (2). La fenêtre Propriétés (3) apparaît également et affiche des informations supplémentaires sur les éléments sélectionnés dans l’Explorateur de solutions, notamment son emplacement exact sur le disque.

    ![Explorateur de solutions avec un projet Python](media/vs-getting-started-python-02-windows.png)

1. Prenez quelques moments pour vous familiariser avec l’Explorateur de solutions, qui est l’endroit où vous parcourez les fichiers et les dossiers de votre projet.

    ![L’Explorateur de solutions développé pour montrer différentes fonctionnalités](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Votre projet mis en gras, avec le nom que vous avez donné dans la boîte de dialogue Nouveau projet. Sur le disque, ce projet est représenté par un fichier `.pyproj` dans le dossier de votre projet.

    (2) Au niveau le plus élevé, vous voyez une *solution*, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier `.sln` sur le disque, est un conteneur pour un ou plusieurs projets connexes. Par exemple, si vous écrivez une extension C++ pour votre application Python, ce projet C++ peut se trouver dans la même solution. La solution peut également contenir un projet pour un service web, ainsi que des projets pour les programmes de test dédiés. 

    (3) Dans votre projet, vous voyez les fichiers sources : dans le cas présent, il n’y a qu’un seul fichier `.py`. La sélection d’un fichier fait apparaître ses propriétés dans la fenêtre Propriétés. Le fait de double-cliquer sur un fichier l’ouvre d’une façon appropriée pour ce fichier.

    (4) Le nœud **Environnements Python** figure également sous le projet. Une fois qu’il est développé, vous voyez les interpréteurs Python disponibles. Développez un nœud d’interpréteur pour voir les bibliothèques qui sont installées dans cet environnement (5).

    Cliquez avec le bouton droit sur n’importe quel nœud ou élément dans l’Explorateur de solutions pour accéder à un menu des commandes applicables. Par exemple, la commande **Renommer** vous permet de changer le nom d’un nœud ou d’un élément, y compris le projet et la solution.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Écriture et exécution de code](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="going-deeper"></a>Pour aller plus loin

- [Projets Python dans Visual Studio](managing-python-projects-in-visual-studio.md).
- [En savoir plus sur le langage Python sur python.org](https://www.python.org)
- [Python pour les débutants](https://www.python.org/about/gettingstarted/) (python.org)
- [Cours Python gratuits sur Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Principales questions sur Python sur Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)
