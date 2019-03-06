---
title: Démarrage rapide - Créer un projet Python à l’aide de Cookiecutter
description: Avec ce guide de démarrage rapide, vous créez un projet Visual Studio pour Python à l’aide d’un modèle Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5c5a3170a2fa66a68fd010b616afcd24e8661776
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843102"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Démarrage rapide : Créer un projet à partir d’un modèle Cookiecutter

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio 2017](installing-python-support-in-visual-studio.md), il est facile de créer un projet à partir d’un modèle Cookiecutter parmi les nombreux qui sont publiés sur GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) fournit une interface utilisateur graphique pour découvrir des modèles, des options de modèle d’entrée et créer des projets et des fichiers. Cette extension est incluse avec Visual Studio 2017 et peut être installée séparément dans les versions antérieures de Visual Studio.

1. Pour ce démarrage rapide, installez d’abord la distribution Python Anaconda3, qui inclut les packages Python nécessaires pour le modèle Cookiecutter montré ici. Exécutez Visual Studio Installer, sélectionnez **Modifier**, développez les options pour **Développement Python** sur le côté droit, puis sélectionnez **Anaconda3** (32 bits ou 64 bits). Notez que si l’installation peut prendre un certain temps, dépendant de la vitesse de votre connexion Internet, il s’agit de la méthode la plus simple pour installer les packages nécessaires.

1. Lancez Visual Studio.

1. Sélectionnez **Fichier** > **Nouveau** > **À partir de Cookiecutter**. Cette commande ouvre une fenêtre dans Visual Studio, où vous pouvez parcourir les modèles.

    ![Nouveau projet à partir d’un modèle Cookiecutter](media/projects-from-cookiecutter1.png)

1. Sélectionnez le modèle **Microsoft/python-sklearn-classifier-cookiecutter**, puis sélectionnez **Suivant**. (Le processus peut prendre plusieurs minutes la première fois que vous utilisez un modèle particulier, car Visual Studio installe les packages Python nécessaires.)

1. À l’étape suivante, définissez un emplacement pour le nouveau projet dans le champ **Créer dans**, puis sélectionnez **Créer et ouvrir un projet**.

    ![Deuxième étape de l’utilisation de Cookiecutter : définition des propriétés du projet](media/projects-from-cookiecutter2.png)

1. À la fin du processus, vous voyez s’afficher le message **Fichiers créés à l’aide du modèle**. Le projet est ouvert automatiquement dans l’Explorateur de solutions.

1. Appuyez sur **Ctrl**+**F5**, ou sélectionnez **Déboguer** > **Exécuter sans débogage**, pour exécuter le programme.

    ![Sortie du projet de modèle python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel : Utiliser Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Utiliser l’extension Cookiecutter](using-python-cookiecutter-templates.md)
- [Identifier manuellement un interpréteur Python existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installer la prise en charge de Python dans Visual Studio 2015 et antérieur](installing-python-support-in-visual-studio.md)
- [Emplacements d’installation](installing-python-support-in-visual-studio.md#install-locations)
