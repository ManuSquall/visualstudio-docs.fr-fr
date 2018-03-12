---
title: "Utilisation de Python dans Visual Studio, étape 6 - utilisation de Git | Microsoft Docs"
description: "Étape 6 d’un didacticiel de base sur l’utilisation de Python dans Visual Studio, décrivant les fonctionnalités Git de Visual Studio."
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
ms.openlocfilehash: eb39d8807deb0c08b12b04128365c584d9bd8251
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="step-6-working-with-git"></a>Étape 6 : Utilisation de Git

**Étape précédente : [Installation de packages et gestion de votre environnement Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio fournit une intégration directe aux dépôts Git locaux, et à ceux qui se trouvent sur des services comme GitHub et Visual Studio Team Services. L’intégration inclut le clonage d’un dépôt, la validation des modifications et la gestion des branches.

Cette rubrique décrit la création d’un dépôt Git local pour un projet existant. Pour une procédure pas à pas de création d’un projet à partir d’un dépôt Git distant, consultez [Démarrage rapide : cloner un dépôt de code Python dans Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

1. Avec un projet ouvert dans Visual Studio, comme le projet de [l’étape précédente](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), cliquez avec le bouton droit sur la solution et sélectionnez **Ajouter la solution au contrôle de code source**. Visual Studio crée un dépôt Git local qui contient le code de votre projet et affiche les contrôles liés à Git, qui apparaissent également dans la partie inférieure de la fenêtre Visual Studio. Les contrôles montrent les validations en attente, les modifications, le nom du dépôt et la branche. Placez le curseur sur les contrôles pour afficher des informations supplémentaires.

  ![Des informations supplémentaires apparaissent quand vous placez le curseur sur un contrôle Git dans la fenêtre Visual Studio](media/working-with-git-01.png)

1. La fenêtre **Team Explorer** s’affiche également avec différentes options Git disponibles en sélectionnant l’en-tête du dépôt. Le volet **Synchroniser**, qui apparaît ainsi quand vous sélectionnez l’en-tête **Push**, fournit des options pour la publication sur un dépôt distant.

  ![Team Explorer dans Visual Studio après la création d’un dépôt local](media/working-with-git-02.png)

1. Sélectionnez **Modifications** pour examiner les modifications non validées et pour les valider quand vous le souhaitez.

  ![Team Explorer dans Visual Studio affichant des modifications non validées](media/working-with-git-03.png)

1. Sélectionnez **Branches** pour examiner des branches, et pour effectuer des opérations de fusion et de rebasage :

  ![Team Explorer dans Visual Studio affichant des branches](media/working-with-git-04.png)

1. Quand vous utilisez un dépôt local, les modifications validées vont directement dans le dépôt. Si vous êtes connecté à un dépôt distant, sélectionnez l’en-tête, choisissez **Synchroniser** pour passer à la section **Synchronisation** et utiliser les commandes présentées.

## <a name="going-deeper"></a>Pour aller plus loin

Pour un didacticiel plus étendu sur l’utilisation de Git, consultez [Partager votre code avec Visual Studio 2017 et VSTS Git](/vsts/git/share-your-code-in-git-vs-2017)

## <a name="tutorial-review"></a>Résumé du didacticiel

Félicitations, vous avez terminé ce didacticiel sur Python dans Visual Studio. Dans ce didacticiel, vous avez découvert comment :

- Créer des projets et afficher le contenu d’un projet.
- Utiliser l’éditeur de code et exécuter un projet.
- Utiliser la fenêtre interactive pour développer du nouveau code et copier facilement ce code dans l’éditeur.
- Exécuter un programme terminé dans le débogueur Visual Studio.
- Installer des packages et gérer des environnements Python
- Travailler avec du code dans un dépôt Git

À partir d’ici, explorez les concepts et les guides pratiques, notamment les suivants :

- [Création d’une extension C++ pour Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publication sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilage](profiling-python-code-in-visual-studio.md)
- [Tests unitaires](unit-testing-python-in-visual-studio.md)
