---
title: Tutoriel Python dans Visual Studio - étape 6, utilisation de Git
titleSuffix: ''
description: Étape 6 d’une procédure pas à pas portant sur Python dans Visual Studio qui décrit les fonctionnalités Git de Visual Studio.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: cd8ebd706d9228d23eb5d5ce3b1429063bae55e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72289719"
---
# <a name="step-6-work-with-git"></a>Étape 6 : Utiliser Git

**Étape précédente : [Installer des packages et gérer des environnements Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio fournit une intégration directe aux dépôts Git locaux et aux dépôts distants sur des services comme GitHub et Azure Repos. L’intégration inclut le clonage d’un dépôt, la validation des modifications et la gestion des branches.

Cet article donne une vue d’ensemble de base de la création d’un référentiel Git local pour un projet existant et de votre familiarisation avec certaines des fonctionnalités de Visual Studio Git.

1. Avec un projet ouvert dans Visual Studio, comme le projet de [l’étape précédente](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), cliquez avec le bouton droit sur la solution et sélectionnez **Ajouter la solution au contrôle de code source**. Visual Studio crée un référentiel Git local qui contient le code de votre projet.

1. Lorsque Visual Studio détecte que le projet est géré dans un référentiel Git, les contrôles Git s’affichent dans l’angle inférieur droit de la fenêtre Visual Studio. Les contrôles montrent les validations en attente, les modifications, le nom du dépôt et la branche. Placez le curseur sur les contrôles pour afficher des informations supplémentaires.

    ![Des informations supplémentaires apparaissent quand vous placez le curseur sur un contrôle Git dans la fenêtre Visual Studio](media/working-with-git-01.png)

1. Lorsque vous créez un référentiel ou sélectionnez une commande Git, Visual Studio ouvre la fenêtre **Team Explorer**. (Vous pouvez ouvrir la fenêtre à tout moment avec la **vue**  >  Commande de menu **Team Explorer** .) La fenêtre comporte trois volets principaux, que vous pouvez basculer entre l’utilisation de la liste déroulante sur l’en-tête **Team Explorer** . Le volet **synchronisation** , qui fournit des opérations de publication, apparaît également lorsque vous sélectionnez le contrôle **Push** (icône en flèche vers le haut) :

    ![Team Explorer dans Visual Studio après la création d’un dépôt local](media/working-with-git-02.png)

1. Sélectionnez **Modifications** (ou le contrôle Git avec l’icône crayon) pour examiner les modifications non validées et pour les valider si vous le souhaitez.

    ![Team Explorer dans Visual Studio affichant des modifications non validées](media/working-with-git-03.png)

    Double-cliquez sur un fichier dans la liste **Modifications** afin d’ouvrir l’affichage Diff pour ce fichier :

    ![Affichage Diff pour les modifications apportées à un fichier](media/working-with-git-05.png)

1. Sélectionnez **Branches** (ou le contrôle Git avec un nom de branche) pour examiner des branches et effectuer des opérations de fusion et de rebasage :

    ![Team Explorer dans Visual Studio affichant des branches](media/working-with-git-04.png)

1. Si vous sélectionnez le contrôle git avec le nom du dépôt (**CosineWave** dans une image précédente), **Team Explorer** affiche une interface de **connexion** avec laquelle vous pouvez rapidement basculer vers un autre référentiel.

1. Quand vous utilisez un dépôt local, les modifications validées vont directement dans le dépôt. Si vous êtes connecté à un référentiel distant, sélectionnez l’en-tête de liste déroulante dans **Team Explorer**, choisissez **synchroniser** pour basculer vers la section **synchronisation** et utilisez les commandes d' **extraction** et d' **extraction** présentées ici.

## <a name="go-deeper"></a>Approfondir la question

Pour une brève procédure pas à pas de création d’un projet à partir d’un référentiel git distant, consultez [démarrage rapide : cloner un référentiel de code python dans Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Pour un tutoriel beaucoup plus complet, notamment sur la prise en charge des conflits de fusion, la revue du code avec des demandes de tirage, le rebasage et le cherry-picking des changements entre les branches, consultez [Bien démarrer avec Git et Azure Repos](/azure/devops/repos/git/gitquickstart).

## <a name="tutorial-review"></a>Résumé du didacticiel

Félicitations, vous avez terminé ce didacticiel sur Python dans Visual Studio. Dans ce didacticiel, vous avez découvert comment :

- Créer des projets et afficher le contenu d’un projet.
- Utiliser l’éditeur de code et exécuter un projet.
- Utilisez la fenêtre **interactive** pour développer du nouveau code et copier facilement ce code dans l’éditeur.
- Exécuter un programme terminé dans le débogueur Visual Studio.
- Installer des packages et gérer des environnements Python
- Utiliser du code dans un dépôt Git

À partir d’ici, explorez les concepts et les guides pratiques, notamment les articles suivants :

- [Créer une extension C++ pour Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilage](profiling-python-code-in-visual-studio.md)
- [Test unitaire](unit-testing-python-in-visual-studio.md)
