---
title: "Utilisation de Python dans Visual Studio, Étape 6 | Microsoft Docs"
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
ms.openlocfilehash: 46048b135dc0023e2a7b918b72ec226af3ed22b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="step-6-working-with-git"></a>Étape 6 : Utilisation de Git

**Étape précédente : [Installation de packages et gestion de votre environnement Python](vs-tutorial-01-05.md)**

Visual Studio fournit une intégration directe aux dépôts Git locaux, et à ceux qui se trouvent sur des services comme GitHub et Visual Studio Team Services. L’intégration inclut le clonage d’un dépôt, la validation des modifications et la gestion des branches.

Cette rubrique décrit la création d’un dépôt Git local pour un projet existant. Pour une procédure pas à pas de création d’un projet à partir d’un dépôt Git distant, consultez [Démarrage rapide : cloner un dépôt de code Python dans Visual Studio](quickstart-03-project-from-repository.md).

1. Avec un projet ouvert dans Visual Studio, comme le projet de [l’étape précédente](vs-tutorial-01-05.md), cliquez avec le bouton droit sur la solution et sélectionnez **Ajouter la solution au contrôle de code source**. Visual Studio crée un dépôt Git local qui contient le code de votre projet et affiche les contrôles liés à Git, qui apparaissent également dans la partie inférieure de la fenêtre Visual Studio. Les contrôles montrent les validations en attente, les modifications, le nom du dépôt et la branche. Placez le curseur sur les contrôles pour afficher des informations supplémentaires.

  ![Des informations supplémentaires apparaissent quand vous placez le curseur sur un contrôle Git dans la fenêtre Visual Studio](media/working-with-git-01.png)

1. La fenêtre **Team Explorer** s’affiche également avec différentes options Git disponibles en sélectionnant l’en-tête du dépôt. Le volet **Synchronisation** qui est illustré fournit des options pour la publication sur un dépôt distant.

  ![Team Explorer dans Visual Studio après la création d’un dépôt local](media/working-with-git-02.png)

1. Sélectionnez **Modifications** pour examiner les modifications non validées et pour les valider quand vous le souhaitez.

  ![Team Explorer dans Visual Studio affichant des modifications non validées](media/working-with-git-03.png)

1. Sélectionnez **Branches** pour examiner des branches, et pour effectuer des opérations de fusion et de rebasage :

  ![Team Explorer dans Visual Studio affichant des branches](media/working-with-git-04.png)

1. Quand vous utilisez un dépôt local, les modifications validées vont directement dans le dépôt. Si vous êtes connecté à un dépôt distant, sélectionnez **Synchroniser** pour pousser (push) vos validations locales.

## <a name="going-deeper"></a>Pour aller plus loin

Pour un didacticiel plus étendu sur l’utilisation de Git, consultez [Partager votre code avec Visual Studio 2017 et VSTS Git](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs-2017)

## <a name="tutorial-review"></a>Résumé du didacticiel

Félicitations, vous avez terminé ce didacticiel sur Python dans Visual Studio. Dans ce didacticiel, vous avez découvert comment :

- Créer des projets et afficher le contenu d’un projet.
- Utiliser l’éditeur de code et exécuter un projet.
- Utiliser la fenêtre interactive pour développer du nouveau code et copier facilement ce code dans l’éditeur.
- Exécuter un programme terminé dans le débogueur Visual Studio.
- Installer des packages et gérer des environnements Python
- Travailler avec du code dans un dépôt Git

À partir d’ici, explorez les concepts et les guides pratiques, notamment les suivants :

- [Création d’une extension C++ pour Python](cpp-and-python.md)
- [Publication sur Azure App Service](publishing-to-azure.md)
- [Profilage](profiling.md)
- [Tests unitaires](unit-testing.md)
