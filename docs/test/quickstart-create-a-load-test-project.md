---
title: Créer un projet de test de performances web et de test de charge dans Visual Studio | Microsoft Docs
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: be2a60cad77f2806c3be59e86509ff96d9c416ed
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="quickstart-create-a-load-test-project"></a>Démarrage rapide : Créer un projet de test de charge

Dans ce démarrage rapide de 10 minutes, vous découvrez comment créer et exécuter un projet de test de performances web et de test de charge dans Visual Studio. Les tests de charge exécutent des tests de performances web ou des tests unitaires pour simuler l’accès simultané de plusieurs utilisateurs à un serveur.

> [!IMPORTANT]
> Les projets de test de performances web et de test de charge sont disponibles seulement dans l’édition Enterprise de Visual Studio 2017.

## <a name="install-the-load-testing-component"></a>Installer le composant de test de charge

Si le composant Outils de test de performances web et de test de charge n’est pas installé, vous devez l’installer via le programme d’installation de Visual Studio.

1. Ouvrir le programme d’installation de Visual Studio à partir du menu Démarrer. Vous pouvez également y accéder dans Visual Studio à partir de la boîte de dialogue **Nouveau projet**, ou en choisissant **Outils** > **Obtenir des outils et fonctionnalités...** dans la barre de menus.

1. Dans le programme d’installation de Visual Studio, choisissez l’onglet **Composants individuels** et faites défiler jusqu’à la section **Débogage et test**. Sélectionnez **Outils de test de performances web et de test de charge**.

   ![Composant Outils de test de performances web et de test de charge](media/web-perf-load-testing-tools-component.png)

1. Choisissez le bouton **Modifier**.

   Le composant Outils de test de performances web et de test de charge est installé.

## <a name="create-a-load-test-project"></a>Créer un projet de test de charge

Dans cette section, nous créons un projet de test de charge C#. Vous pouvez également créer un projet de test de charge Visual Basic si vous préférez.

1. Ouvrez Visual Studio et choisissez **Fichier** > **Nouveau** > **Projet...** dans la barre de menus.

   La boîte de dialogue **Nouveau projet** s'affiche.

1. Dans la boîte de dialogue **Nouveau Projet**, développez **Installé** et **Visual C#**, puis sélectionnez la catégorie **Test**. Choisissez le modèle **Projet de performances web et de test de charge**.

   ![Projet de performances web et de test de charge](media/web-perf-load-test-project-template.png)

1. Entrez un nom pour le projet si vous ne voulez pas utiliser le nom par défaut, puis choisissez **OK**.

   Visual Studio crée le projet et affiche les fichiers dans **l’Explorateur de solutions**. Le projet contient initialement un seul fichier de test web nommé *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Ajouter un test de charge au projet

1. Dans le menu contextuel du nœud du projet dans **l’Explorateur de solutions**, choisissez **Ajouter** > **Test de charge...**.

   **L’Assistant Nouveau test de charge** s’ouvre.

1. Sélectionnez l’option **Test de charge local**, puis choisissez **Suivant**. Vous pouvez découvrir plus d’informations sur les tests de charge basés sur le cloud [ici](/vsts/load-test/get-started-simple-cloud-load-test).

   ![Assistant Nouveau test de charge - première page](media/load-test-wizard-page-1.png)

1. Choisissez **Suivant** pour franchir les étapes de l’Assistant jusqu’à atteindre la page **Ajouter des tests à un scénario de test de charge et modifier la combinaison de tests**. Choisissez le bouton **Ajouter** .

   La boîte de dialogue **Ajouter des tests** s’ouvre.

1. Sous **Tests disponibles**, sélectionnez **WebTest1**, puis choisissez la flèche droite pour le déplacer vers la zone **Tests sélectionnés**. Sélectionnez le bouton **OK** .

   ![Boîte de dialogue Ajouter des tests](media/add-tests-dialog-box.png)

1. De retour dans **l’Assistant Nouveau test de charge**, choisissez le bouton **Terminer**.

   Le test de charge est ajouté au projet et le fichier de test de charge s’ouvre dans la fenêtre de l’éditeur.

## <a name="run-the-load-test"></a>Exécuter le test de charge

Nous avons créé un test de charge qui ne fait pas grand-chose, mais nous allons quand même l’exécuter.

Dans le menu contextuel du test de charge qui est ouvert dans l’éditeur, choisissez **Exécuter le test de charge**.

![Menu Exécuter le test de charge](media/run-load-test.png)

L’exécution du test de charge démarre. La fenêtre **Résultats des tests** montre que le test est en cours d’exécution et l’analyseur de test de charge s’affiche dans la fenêtre de l’éditeur. Une fois le test terminé, ce qui doit prendre cinq minutes si vous avez accepté les paramètres par défaut, un récapitulatif est affiché dans l’éditeur. Vous pouvez choisir **Graphiques**, **Tables** ou **Détails** pour obtenir différentes informations sur les résultats du test de charge.

![Fenêtre de l’analyseur de test de charge](media/load-test-analyzer.png)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez créé un projet de test de charge simple, l’étape suivante consiste à configurer des scénarios, des ensembles de compteurs et des paramètres d’exécution.

> [!div class="nextstepaction"]
> [Modifier les paramètres de test](edit-load-tests.md)