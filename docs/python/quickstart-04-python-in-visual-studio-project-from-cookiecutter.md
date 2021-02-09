---
title: 'Démarrage rapide : créer des projets Python à l’aide de Cookiecutter'
description: Avec ce guide de démarrage rapide, vous créez un projet Visual Studio pour Python à l’aide d’un modèle Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c8a3727faa01b69962dd3dc456ac7b704f62882
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902440"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Démarrage rapide : Créer un projet à partir d’un modèle Cookiecutter

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md), il est facile de créer un projet à partir d’un modèle Cookiecutter parmi les nombreux qui sont publiés sur GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) fournit une interface utilisateur graphique pour découvrir des modèles, des options de modèle d’entrée et créer des projets et des fichiers. Cette extension est incluse avec Visual Studio 2017 et ultérieur, et peut être installée séparément dans les versions antérieures de Visual Studio.

1. Pour ce démarrage rapide, installez d’abord la distribution Python Anaconda3, qui inclut les packages Python nécessaires pour le modèle Cookiecutter montré ici. Exécutez le programme d’installation de Visual Studio, sélectionnez **modifier**, développez les options pour le **développement python** sur le côté droit, puis sélectionnez **Anaconda3** (32 bits ou 64 bits). Notez que si l’installation peut prendre un certain temps, dépendant de la vitesse de votre connexion Internet, il s’agit de la méthode la plus simple pour installer les packages nécessaires.

1. Lancez Visual Studio.

1. Sélectionnez **fichier**  >  **nouveau**  >  **à partir de Cookiecutter**. Cette commande ouvre une fenêtre dans Visual Studio, où vous pouvez parcourir les modèles.

    ![Nouveau projet à partir d’un modèle Cookiecutter](media/projects-from-cookiecutter1.png)

1. Sélectionnez le modèle **Microsoft/python-sklearn-classifier-cookiecutter** , puis sélectionnez **suivant**. (Le processus peut prendre plusieurs minutes la première fois que vous utilisez un modèle particulier, car Visual Studio installe les packages Python nécessaires.)

1. À l’étape suivante, définissez un emplacement pour le nouveau projet dans le champ **Créer dans**, puis sélectionnez **Créer et ouvrir un projet**.

    ![Deuxième étape de l’utilisation de Cookiecutter : définition des propriétés du projet](media/projects-from-cookiecutter2.png)

1. Une fois le processus terminé, le message suivant s’affiche : les **fichiers ont été créés avec succès à l’aide du modèle...** Le projet est ouvert dans Explorateur de solutions automatiquement.

1. Appuyez sur **CTRL** + **F5** ou sélectionnez **Déboguer** exécuter  >  **sans débogage** pour exécuter le programme.

    ![Sortie du projet de modèle python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel : Utiliser Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Utiliser l’extension Cookiecutter](using-python-cookiecutter-templates.md)
- [Identifier manuellement un interpréteur Python existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installer la prise en charge de Python dans Visual Studio 2015 et les versions antérieures](installing-python-support-in-visual-studio.md)
- [Emplacements d’installation](installing-python-support-in-visual-studio.md#install-locations)
