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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568878"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Procédure pas à pas : créer et exécuter des tests unitaires pour des applications UWP

Visual Studio inclut la prise en charge des tests unitaires des applications de plateforme Windows universelle (UWP). Visual Studio fournit des modèles de projet de C#test unitaire pour, C++Visual Basic et.

> [!TIP]
> Pour plus d’informations sur le développement d’applications UWP, consultez [Bien démarrer avec les applications UWP](/windows/uwp/get-started/).

Les procédures suivantes décrivent les étapes permettant de créer, d’exécuter et de déboguer des tests unitaires pour une application UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Créer un projet de test unitaire pour une application UWP

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

2. Dans la zone de recherche de la page **créer un nouveau projet** , entrez **test unitaire**.

   La liste des modèles filtre les filtres pour les tests unitaires.

3. Sélectionnez le modèle **application de test unitaire (Windows universel)** pour C# ou Visual Basic, puis sélectionnez **suivant**.

   ![Créer une application de test unitaire UWP dans Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Si vous le souhaitez, modifiez le nom et l’emplacement du projet ou de la solution, puis sélectionnez **créer**.

5. Si vous le souhaitez, modifiez les versions cible et minimale de la plateforme, puis sélectionnez **OK**.

Une fois ces étapes terminées, le projet de test unitaire est créé et s’affiche dans Explorateur de solutions.

![Projet de test unitaire UWP dans Explorateur de solutions](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Dans le menu **Fichier** , choisissez **Nouveau projet**.

   La boîte de dialogue **Nouveau projet** s’affiche.

2. Sous Modèles, sélectionnez le langage de programmation dans lequel vous voulez créer le test unitaire, puis choisissez la bibliothèque de tests unitaires Windows universel associée. Par exemple, choisissez **Visual C#** , **Windows universel**, puis **Bibliothèque de tests unitaires (Windows universel)** .

3. (Facultatif) Dans la zone de texte **Nom**, entrez le nom à utiliser pour le projet.

4. (Facultatif) Changez le chemin où vous voulez créer le projet en l’entrant dans la zone de texte **Emplacement** ou en choisissant le bouton **Parcourir**.

5. (Facultatif) Dans la zone de texte **Nom de la solution** , entrez le nom à utiliser pour votre solution.

6. Laissez l'option **Créer le répertoire pour la solution** sélectionnée et choisissez le bouton **OK** .

   ![Bibliothèque de test unitaire personnalisée](../test/media/unit_test_win8_1.png)

   Le projet de test unitaire UWP est importé dans **l’Explorateur de solutions**, et l’éditeur de code affiche le test unitaire par défaut intitulé UnitTest1.

   ![Nouveau projet de test unitaire personnalisé](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Modifier le fichier manifeste de l’application UWP du projet de test unitaire

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Package.appxmanifest* et choisissez **Ouvrir**.

2. Dans le **Concepteur de manifeste**, choisissez l’onglet **Fonctionnalités**.

3. Dans la liste sous **Fonctionnalités**, sélectionnez les fonctionnalités dont vous avez besoin pour votre test unitaire et le code qu'il teste. Par exemple, activez la case à cocher **Internet** si le test unitaire est requis et que le code qu'il teste a besoin d'accéder à internet.

   > [!NOTE]
   > Les fonctionnalités que vous sélectionnez doivent être seulement celles qui sont nécessaires pour que le test unitaire fonctionne correctement.

   ![Manifeste de test unitaire](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Coder le test unitaire pour une application UWP

Dans l’éditeur de code, modifiez le test unitaire et ajoutez les assertions et la logique requises pour votre test.

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

Pour générer la solution et exécuter le test unitaire à l’aide de l’Explorateur de tests :

1. Dans le menu **Test** , choisissez **Fenêtres**, puis **Explorateur de tests**.

2. Dans le menu **Générer** , cliquez sur **Générer la solution**.

   Votre test unitaire est maintenant affiché dans l’Explorateur de tests.

   > [!NOTE]
   > Vous devez générer la solution pour mettre à jour la liste des tests unitaires dans l'Explorateur de tests.

3. Dans **l’Explorateur de tests**, sélectionnez le test unitaire que vous avez créé.

4. Choisissez **Exécuter tout**.

   ![Explorateur de tests unitaires &#45; exécuter un test unitaire](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Vous pouvez sélectionner un ou plusieurs tests unitaires listés dans l’Explorateur de tests, puis cliquer avec le bouton droit et choisir **exécuter les tests sélectionnés**.
   >
   > De plus, vous pouvez choisir **Déboguer les tests sélectionnés**, **Ouvrir un test**, puis utiliser l'option **Propriétés** .
   >
   > ![Menu contextuel &#45; de test unitaire de l’Explorateur de tests unitaires](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Le test unitaire s'exécute. Une fois l’opération terminée, l’Explorateur de tests affiche l’état du test et le temps écoulé, et fournit un lien vers la source.

   ![Explorateur de tests unitaires &#45; test terminé](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Voir aussi

- [Tester des applications UWP avec Visual Studio](../test/unit-test-your-code.md)
- [Générer et tester une application UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
