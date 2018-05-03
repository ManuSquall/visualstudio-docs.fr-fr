---
title: Création et exécution de tests unitaires pour les applications UWP dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 4de04bcd612c11f2b739fbdb1521008a45a3aead
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Procédure pas à pas : Créer et exécuter des tests unitaires pour des applications UWP

Visual Studio inclut la prise en charge des tests unitaires des applications de plateforme Windows universelle (UWP). Ceci inclut des modèles de projet de tests unitaires pour Visual C#, Visual Basic et Visual C++.

> [!TIP]
> Pour plus d’informations sur le développement d’applications UWP, consultez [Bien démarrer avec les applications UWP](/windows/uwp/get-started/).

Les procédures suivantes décrivent les étapes nécessaires pour créer, exécuter et déboguer des tests unitaires pour une application UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Créer un projet de test unitaire pour une application UWP

1.  Dans le menu **Fichier** , choisissez **Nouveau projet**.

     La boîte de dialogue Nouveau projet s'affiche.

2.  Sous Modèles, sélectionnez le langage de programmation dans lequel vous voulez créer le test unitaire, puis choisissez la bibliothèque de tests unitaires Windows universel associée. Par exemple, choisissez **Visual C#**, **Windows universel**, puis **Bibliothèque de tests unitaires (Windows universel)**.

3.  (Facultatif) Dans la zone de texte **Nom**, entrez le nom à utiliser pour le projet.

4.  (Facultatif) Changez le chemin où vous voulez créer le projet en l’entrant dans la zone de texte **Emplacement** ou en choisissant le bouton **Parcourir**.

5.  (Facultatif) Dans la zone de texte **Nom de la solution** , entrez le nom à utiliser pour votre solution.

6.  Laissez l'option **Créer le répertoire pour la solution** sélectionnée et choisissez le bouton **OK** .

     ![Bibliothèque de test unitaire personnalisée](../test/media/unit_test_win8_1.png "Unit_Test_Win8_1")

     L’Explorateur de solutions est rempli avec le projet de test unitaire UWP et l’éditeur de code affiche le test unitaire par défaut intitulé UnitTest1.

     ![Nouveau projet de test unitaire personnalisé](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Modifier le fichier manifeste de l’application UWP du projet de test unitaire

1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier *Package.appxmanifest* et choisissez **Ouvrir**.

     Le concepteur de manifeste s'affiche pour la modification.

2.  Dans le concepteur de manifeste, choisissez l'onglet **Fonctionnalités** .

3.  Dans la liste sous **Fonctionnalités**, sélectionnez les fonctionnalités dont vous avez besoin pour votre test unitaire et le code qu'il teste. Par exemple, activez la case à cocher **Internet** si le test unitaire est requis et que le code qu'il teste a besoin d'accéder à internet.

    > [!NOTE]
    > Les fonctionnalités que vous sélectionnez doivent être seulement celles qui sont nécessaires pour que le test unitaire fonctionne correctement.

     ![Manifeste de test unitaire](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Coder le test unitaire pour une application UWP

Dans l'Éditeur de code, modifiez le test unitaire et ajoutez les assertions et la logique requises pour votre test.

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Pour générer la solution et exécuter le test unitaire à l'aide de l'Explorateur de tests

1.  Dans le menu **Test** , choisissez **Fenêtres**, puis **Explorateur de tests**.

     L'Explorateur de tests s'affiche et votre test ne figure pas dans la liste.

2.  Dans le menu **Générer** , cliquez sur **Générer la solution**.

     Votre test unitaire figure maintenant dans la liste.

    > [!NOTE]
    > Vous devez générer la solution pour mettre à jour la liste des tests unitaires dans l'Explorateur de tests.

3.  Dans l'Explorateur de tests, sélectionnez le test unitaire que vous avez créé.

    > [!TIP]
    > L'Explorateur de tests fournit un lien vers le code source en regard de **Source :**.

4.  Choisissez **Exécuter tout**.

     ![Explorateur de tests unitaires &#45; exécuter un test unitaire](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

    > [!TIP]
    > Vous pouvez sélectionner un ou plusieurs tests unitaires répertoriés dans l'explorateur puis cliquer avec le bouton droit et choisir **Exécuter les tests sélectionnés**.
    >
    > De plus, vous pouvez choisir **Déboguer les tests sélectionnés**, **Ouvrir un test**, puis utiliser l'option **Propriétés** .
    >
    > ![Explorateur de tests unitaires &#45; menu contextuel de test unitaire](../test/media/unit_test_win8_unittestexplorer_contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

    Le test unitaire s'exécute. Une fois l’opération terminée, l’Explorateur de tests affiche l’état du test, la durée calendaire et fournit un lien vers la source.

    ![Explorateur de tests unitaires &#45; test terminé](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Voir aussi

- [Test d’applications UWP avec Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Générer et tester une application UWP](/vsts/build-release/apps/windows/universal?tabs=vsts)
