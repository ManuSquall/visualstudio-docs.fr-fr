---
title: Vue d’ensemble de Visual Studio pour les développeurs Python
titleSuffix: ''
ms.date: 12/14/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 97b48daf123ea39cd00070fa95c4b488da9d9163
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952949"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Bienvenue dans l’IDE Visual Studio | Python

*L’environnement de développement intégré* de Visual Studio est une plateforme de lancement créative pour Python (et d’autres langages) qui permet de modifier, déboguer et tester du code, puis de publier une application. Un environnement de développement intégré (IDE) est un programme riche en fonctionnalités qui peut être utilisé pour de nombreux aspects du développement de logiciels. En plus de l’éditeur et du débogueur standard fournis par la plupart des IDE, Visual Studio offre des outils de complétion du code, des environnements REPL interactifs et d’autres fonctionnalités qui facilitent le processus de développement logiciel.

[![Visual Studio avec un projet Python](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Cette image montre Visual Studio avec un projet Python ouvert et plusieurs fenêtres Outil essentielles et souvent utilisées :

- L’[**Explorateur de solutions**](../ide/solutions-and-projects-in-visual-studio.md) (en haut à droite) vous permet d’afficher, de parcourir et de gérer vos fichiers de code. L’**Explorateur de solutions** peut vous aider à organiser votre code en regroupant les fichiers dans des [projets et des solutions](/visualstudio/get-started/tutorial-projects-solutions).
    - À côté de **l’Explorateur de solutions** se trouvent les [**Environnements Python**](managing-python-environments-in-visual-studio.md), qui permettent de gérer les différents interpréteurs Python installés sur l’ordinateur.

- La [fenêtre de l’éditeur](../ide/writing-code-in-the-code-and-text-editor.md) (au centre), où vous passerez sans doute la plupart de votre temps, affiche le contenu des fichiers. C’est là que vous pourrez [modifier le code Python](editing-python-code-in-visual-studio.md), parcourir la structure de votre code et définir des points d’arrêt au cours des sessions de débogage. Avec Python, il est également possible de sélectionner du code et d’appuyer sur Ctrl+Entrée pour l’exécuter dans une [fenêtre REPL interactive](python-interactive-repl-in-visual-studio.md).

- Dans la [fenêtre Sortie](../ide/reference/output-window.md) (en bas au centre), Visual Studio envoie des notifications, par exemple, des messages d’erreur et de débogage, des avertissements, des messages d’état de publication, etc. Chaque source de message a son propre onglet.
    - Une [fenêtre REPL Interactive Python](python-interactive-repl-in-visual-studio.md) apparaît dans la même zone que la fenêtre Sortie.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (en bas à droite) vous permet de suivre des éléments de travail et de partager du code avec d’autres utilisateurs à l’aide des technologies de gestion de versions comme [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Éditions

Visual Studio est disponible pour Windows et Mac ; toutefois, Python n’est pris en charge que sur Visual Studio pour Windows.

Il existe trois éditions de Visual Studio 2017 sur Windows : Community, Professional et Enterprise. Consultez [Comparez les IDE Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) pour en savoir plus sur les fonctionnalités prises en charge dans chaque édition.

## <a name="popular-productivity-features"></a>Fonctionnalités de productivité populaires

Voici quelques-unes des fonctionnalités populaires de Visual Studio qui vous aident à être plus productifs quand vous développez des logiciels :

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense est un terme désignant un ensemble de fonctionnalités qui affichent des informations relatives au code directement dans l’éditeur et qui, dans certains cas, écrivent de petits bouts de code à votre place. Cela revient à avoir de la documentation de base incluse dans l’éditeur, ce qui vous évite d’avoir à rechercher ailleurs des informations sur les types. Les fonctionnalités IntelliSense varient en fonction du langage. L’article [Modifier du code Python](editing-python-code-in-visual-studio.md#intellisense) concerne Python. L’illustration suivante montre comment IntelliSense affiche une liste des membres d’un type :

   ![Complétion de membres avec Visual Studio IntelliSense](media/code-editing-completions-simple.png)

- [Refactorisation](refactoring-python-code.md)

   Si vous cliquez avec le bouton droit sur une partie du code et que vous sélectionnez **Actions rapides et refactorisation**, Visual Studio vous propose des opérations comme le renommage intelligent des variables, l’extraction d’une ou plusieurs lignes de code dans une nouvelle méthode, le changement de l’ordre des paramètres de méthode, etc.

   ![Refactorisation dans Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Linting](refactoring-python-code.md)

   Le linting vérifie l’absence d’erreurs et de problèmes courants dans votre code Python, encourageant ainsi de bons modèles de codage Python.

   ![Commande PyLint dans le menu contextuel des projets Python](media/code-pylint-command.png)

- [Lancement rapide](../ide/reference/quick-launch-environment-options-dialog-box.md)

   La maîtrise de Visual Studio peut sembler insurmontable parfois, avec autant de menus, d’options et de propriétés. La zone de recherche **Lancement rapide** est un excellent moyen de trouver rapidement ce dont vous avez besoin dans Visual Studio. Quand vous commencez à taper le nom d’un élément que vous recherchez, Visual Studio affiche des résultats qui vous mènent exactement où vous devez accéder. Si vous avez besoin ajouter des fonctionnalités à Visual Studio, par exemple pour ajouter la prise en charge d’un langage de programmation supplémentaire, **Lancement rapide** fournit des résultats qui ouvrent Visual Studio Installer pour installer une charge de travail ou un composant spécifique.

   ![Zone de recherche Lancement rapide dans Visual Studio](media/tour-ide-quick-launch.png)

- Tildes et [Actions rapides](../ide/quick-actions.md)

   Les tildes sont des soulignements ondulés qui vous signalent des erreurs ou des problèmes potentiels dans votre code en cours de frappe. Ces indices visuels permettent de résoudre les problèmes immédiatement sans attendre que l’erreur soit découverte durant la génération ou quand vous exécutez le programme. Si vous pointez sur un tilde, vous voyez des informations supplémentaires sur l’erreur. Une ampoule (appelée Action rapide) peut également apparaître dans la marge gauche, avec des actions pour corriger l’erreur.

   ![Tildes dans Visual Studio](media/tour-ide-squiggles.png)

- [Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md)

   La fonctionnalité **Atteindre la définition** vous mène directement à l’emplacement où une fonction ou un type est défini. La commande **Aperçu des définitions** affiche la définition dans une fenêtre sans ouvrir de fichier distinct. La commande **Rechercher toutes les références** représente également un moyen utile de trouver à quel endroit un identificateur donné est défini et utilisé.

   ![Commandes de navigation dans le code](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Fonctionnalités puissantes pour Python

- [REPL interactif Python](python-interactive-repl-in-visual-studio.md)

    Visual Studio intègre une fenêtre REPL (read-evaluate-print loop) interactive pour chacun de vos environnements Python, ce qui permet d’améliorer le REPL obtenu avec *python.exe* sur la ligne de commande. Dans la fenêtre **Interactif**, vous pouvez entrer le code Python et en voir immédiatement les résultats.

    ![Fenêtre interactive Python](media/interactive-window.png)

- [Débogage](debugging-python-in-visual-studio.md)

    Visual Studio offre une expérience de débogage complète pour Python, comprenant notamment l’attachement à des processus en cours d’exécution, l’évaluation d’expressions dans les Fenêtres **Espion** et **Exécution**, l’inspection de variables locales, les points d’arrêt, les instructions de pas à pas détaillé/sortant/principal, la **définition de l’instruction suivante**, etc. Vous pouvez également déboguer du code Python à distance sur des ordinateurs Linux.

    ![Déboguer du code Python dans Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interagir avec C++](working-with-c-cpp-python-in-visual-studio.md)

    De nombreuses bibliothèques créées pour Python sont écrites en C++ pour offrir des performances optimales. Visual Studio propose de riches fonctionnalités pour le développement d’extensions C++, notamment le [débogage en mode mixte](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Débogage en mode mixte de Python et C++](media/mixed-mode-debugging.png)

- [Profilage](profiling-python-code-in-visual-studio.md)

    Si vous utilisez un interpréteur CPython, vous pouvez évaluer les performances de votre code Python dans Visual Studio.

    ![Rapport de performances de profilage](media/profiling-results.png)

- [Tests unitaires](unit-testing-python-in-visual-studio.md)

    Visual Studio assure une prise en charge intégrée de la découverte, de l’exécution et du débogage de tests unitaires, le tout dans le contexte de l’IDE.

    ![Test unitaire affichant un état d’échec](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Étapes suivantes

Explorez plus en profondeur Python dans Visual Studio en suivant l’un des guides de démarrage rapide ou tutoriels suivants :

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer une application web avec Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Utilisation de Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Bien démarrer avec le framework web Django dans Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Bien démarrer avec le framework web Flask dans Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Voir aussi

- Découvrir d’[autres fonctionnalités de Visual Studio](../ide/advanced-feature-overview.md)
- Visiter [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Lire le [blog Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
- Accéder aux cours Visual Studio gratuits sur [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)
