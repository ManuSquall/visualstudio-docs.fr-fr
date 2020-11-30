---
title: Créer un projet de performances et de test de charge de site Web
description: Découvrez comment créer et exécuter un projet de test de performances de site Web et de charge dans Visual Studio avec ce guide de démarrage rapide.
ms.custom: SEO-VS-2020
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3833542dc00f347014dabf96f836fbd4fa810862
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329131"
---
# <a name="quickstart-create-a-load-test-project"></a>Démarrage rapide : Créer un projet de test de charge

Dans ce guide de démarrage rapide de 10 minutes, vous découvrirez comment créer et exécuter un projet de test de performances web et de charge dans Visual Studio. Les tests de charge exécutent des tests de performances web ou des tests unitaires pour simuler l’accès simultané de plusieurs utilisateurs à un serveur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Configuration logicielle requise

Les projets de test de performances web et de test de charge sont disponibles seulement dans l’**édition Enterprise** de Visual Studio.

## <a name="install-the-load-testing-component"></a>Installer le composant de test de charge

Si le composant des outils de test de performances web et de charge n’est pas installé, utilisez pour cela Visual Studio Installer.

1. Ouvrez **Visual Studio installer** à partir du menu **Démarrer** de Windows. Vous pouvez également y accéder dans Visual Studio à partir de la boîte de dialogue Nouveau projet ou en choisissant **Outils**  >  **afficher les outils et les fonctionnalités** dans la barre de menus.

1. Dans **Visual Studio Installer**, choisissez l’onglet **Composants individuels** et faites défiler jusqu’à la section **Débogage et test**. Sélectionnez **Outils de test de performances web et de test de charge**.

   ![Composant Outils de test de performances web et de test de charge](media/web-perf-load-testing-tools-component.png)

1. Choisissez le bouton **Modifier**.

   Le composant des outils de test de performances web et de charge est installé.

## <a name="create-a-load-test-project"></a>Créer un projet de test de charge

Dans cette section, nous créons un projet de test de charge C#. Vous pouvez également créer un projet de test de charge Visual Basic si vous préférez.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

2. Choisissez **Fichier** > **Nouveau** > **Projet** dans la barre de menus.

   La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans la boîte de dialogue **Nouveau Projet**, développez **Installé** et **Visual C#**, puis sélectionnez la catégorie **Test**. Choisissez le modèle **Projet de performances web et de test de charge**.

   ![Projet de performances web et de test de charge](media/web-perf-load-test-project-template.png)

4. Entrez un nom pour le projet si vous ne voulez pas utiliser le nom par défaut, puis choisissez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Dans la page **Créer un projet**, tapez **test web** dans la zone de recherche, puis sélectionnez le modèle **Projet de test de performance web et de charge \[déprécié]** pour C#. Choisissez **Suivant**.

4. Entrez un nom pour le projet si vous ne voulez pas utiliser le nom par défaut, puis choisissez **Créer**.

::: moniker-end

   Visual Studio crée le projet et affiche les fichiers dans **Explorateur de solutions**. Le projet contient initialement un fichier de test Web nommé *WebTest1. WebTest*.

## <a name="add-a-load-test-to-the-project"></a>Ajouter un test de charge au projet

1. Dans le menu contextuel, ou menu contextuel du nœud de projet dans **Explorateur de solutions**, choisissez **Ajouter** un  >  **test de charge**.

   **L’Assistant Nouveau test de charge** s’ouvre.

1. Sélectionnez l’option **Test de charge local**, puis choisissez **Suivant**. Vous pouvez découvrir plus d’informations sur les tests de charge basés sur le cloud [ici](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true).

   ![Assistant Nouveau test de charge - première page](media/load-test-wizard-page-1.png)

1. Choisissez **Suivant** pour franchir les étapes de l’Assistant jusqu’à atteindre la page **Ajouter des tests à un scénario de test de charge et modifier la combinaison de tests**. Choisissez le bouton **Ajouter**.

   La boîte de dialogue **Ajouter des tests** s’ouvre.

1. Sous **Tests disponibles**, sélectionnez **WebTest1**, puis choisissez la flèche droite pour le déplacer vers la zone **Tests sélectionnés**. Choisissez le bouton **OK**.

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
