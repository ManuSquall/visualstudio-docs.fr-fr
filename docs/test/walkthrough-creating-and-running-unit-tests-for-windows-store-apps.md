---
title: Création et exécution de tests unitaires pour les applications UWP
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 4109f743caf7c62450591f78e90b92113fc4107e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568878"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Procédure pas à pas : créer et exécuter des tests unitaires pour des applications UWP

Visual Studio inclut la prise en charge des tests unitaires des applications de plateforme Windows universelle (UWP). Visual Studio fournit des modèles de projets d’essai unitaire pour le C, visual Basic et le CMD.

> [!TIP]
> Pour plus d’informations sur le développement d’applications UWP, consultez [Bien démarrer avec les applications UWP](/windows/uwp/get-started/).

Les procédures suivantes décrivent les étapes pour créer, exécuter et déboguer des tests unitaires pour une application UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Créer un projet de test unitaire pour une application UWP

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

2. Dans la boîte de recherche de la **création d’une nouvelle** page de projet, entrez **le test unitaire**.

   La liste des modèles filtre à ceux pour les tests unitaires.

3. Sélectionnez le modèle **d’application de test unitaire (Windows universel)** pour C ou Visual Basic, puis sélectionnez **Next**.

   ![Créez une nouvelle application de test unitaire UWP dans Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Modifier le nom et l’emplacement du projet ou de la solution, puis sélectionner **Create**.

5. Modifier en option les versions de la plate-forme cible et minimale, puis sélectionnez **OK**.

Après avoir terminé ces étapes, le projet d’essai unitaire est créé et s’affiche dans Solution Explorer.

![Projet d’essai unitaire UWP dans Solution Explorer](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Dans le menu **Fichier** , choisissez **Nouveau projet**.

   Le **dialogue du nouveau projet** affiche.

2. Sous Modèles, sélectionnez le langage de programmation dans lequel vous voulez créer le test unitaire, puis choisissez la bibliothèque de tests unitaires Windows universel associée. Par exemple, choisissez **Visual C#**, **Windows universel**, puis **Bibliothèque de tests unitaires (Windows universel)**.

3. (Facultatif) Dans la zone de texte **Nom**, entrez le nom à utiliser pour le projet.

4. (Facultatif) Changez le chemin où vous voulez créer le projet en l’entrant dans la zone de texte **Emplacement** ou en choisissant le bouton **Parcourir**.

5. (Facultatif) Dans la zone de texte **Nom de la solution** , entrez le nom à utiliser pour votre solution.

6. Laissez l'option **Créer le répertoire pour la solution** sélectionnée et choisissez le bouton **OK** .

   ![Bibliothèque de test unitaire personnalisée](../test/media/unit_test_win8_1.png)

   **Solution Explorer** est peuplé du projet de test unitaire UWP, et l’éditeur de code affiche le test unitaire par défaut intitulé UnitTest1.

   ![Nouveau projet de test unitaire personnalisé](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Modifier le fichier manifeste de l’application UWP du projet de test unitaire

1. Dans **Solution Explorer**, cliquez à droite sur le fichier *Package.appxmanifest* et choisissez **Open**.

2. Dans le **Concepteur de manifeste**, choisissez l’onglet **Fonctionnalités**.

3. Dans la liste sous **Fonctionnalités**, sélectionnez les fonctionnalités dont vous avez besoin pour votre test unitaire et le code qu'il teste. Par exemple, activez la case à cocher **Internet** si le test unitaire est requis et que le code qu'il teste a besoin d'accéder à internet.

   > [!NOTE]
   > Les fonctionnalités que vous sélectionnez doivent être seulement celles qui sont nécessaires pour que le test unitaire fonctionne correctement.

   ![Manifeste de test unitaire](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Coder le test unitaire pour une application UWP

Dans l’éditeur de code, modifiez le test unitaire et ajoutez les affirmations et la logique requises pour votre test.

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

Pour construire la solution et exécuter le test unitaire à l’aide de Test Explorer :

1. Dans le menu **Test** , choisissez **Fenêtres**, puis **Explorateur de tests**.

2. Dans le menu **Build,** choisissez **Build Solution**.

   Votre test unitaire est maintenant affiché dans Test Explorer.

   > [!NOTE]
   > Vous devez générer la solution pour mettre à jour la liste des tests unitaires dans l'Explorateur de tests.

3. Dans **Test Explorer**, choisissez le test unitaire que vous avez créé.

4. Choisissez **Exécuter tout**.

   ![Explorateur de tests unitaires &#45; exécuter un test unitaire](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Vous pouvez sélectionner un ou plusieurs tests unitaires répertoriés dans Test Explorer, puis cliquer à droite et choisir **des tests sélectionnés .**
   >
   > De plus, vous pouvez choisir **Déboguer les tests sélectionnés**, **Ouvrir un test**, puis utiliser l'option **Propriétés** .
   >
   > ![Unit Test Explorer &#45; menu de contexte d’essai unitaire](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Le test unitaire s'exécute. Une fois terminé, Test Explorer affiche l’état du test et le temps écoulé et fournit un lien vers la source.

   ![Explorateur de tests unitaires &#45; test terminé](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Voir aussi

- [Tester des applications UWP avec Visual Studio](../test/unit-test-your-code.md)
- [Générer et tester une application UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
