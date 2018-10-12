---
title: Bien démarrer avec les tests unitaires
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 171d329ed852bf6a27f20f12ae0f5421103820ff
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370805"
---
# <a name="get-started-with-unit-testing"></a>Bien démarrer avec les tests unitaires

Utilisez Visual Studio pour définir et exécuter vos tests unitaires afin de maintenir l’intégrité du code, garantir la couverture du code et rechercher les erreurs ainsi que les pannes avant vos clients.

## <a name="create-unit-tests"></a>Créer des tests unitaires

Créez des tests unitaires et exécutez-les souvent pour vérifier que votre code fonctionne correctement.

1. Créez un projet de test unitaire.

   ![Ajouter un projet de test unitaire à votre solution](media/createunittest1.png)

1. Nommez votre projet.

   ![Modèle de projet de test unitaire](media/createunittest2.png)

   Le projet est ajouté à votre solution.

   ![Projet de test unitaire dans l’Explorateur de solutions](media/createunittest5.png)

1. Dans le projet de test unitaire, ajoutez une référence au projet que vous voulez tester.

   ![Ajouter une référence à votre projet de test unitaire](media/createunittest6.png)

1. Sélectionnez le projet qui contient le code que vous allez tester.

   ![Sélectionner la référence à ajouter](media/createunittest7.png)

1. Codez votre test unitaire.

   ![Ajouter du code à votre test unitaire](media/createunittest8.png)

Vous pouvez également créer des stubs de méthodes de tests unitaires avec la [commande](create-unit-tests-menu.md) **Créer des tests unitaires**.

![Utilisation de la commande Créer des tests unitaires](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

1. Ouvrez **l’Explorateur de tests**.

   ![Dans le menu Test, ouvrir Explorateur de tests](media/rununittest1.png)

1. Exécutez des tests unitaires.

   ![Exécuter des tests unitaires dans l'Explorateur de tests](media/rununittest2.png)

   Dans **l’Explorateur de tests** apparaissent les tests unitaires qui ont abouti ou échoué.

   ![Examiner les résultats des tests unitaires dans l’Explorateur de tests](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>Afficher les résultats des tests unitaires en direct

Si vous utilisez le framework de tests MSTest, xUnit ou NUnit dans Visual Studio 2017 ou une version ultérieure, vous pouvez afficher les résultats temps réel de vos tests unitaires.

> [!NOTE]
> Les tests unitaires en direct ne sont disponibles que dans Visual Studio 2017 Enterprise.

1. Activez les tests unitaires en direct à partir du menu **Test**.

   ![Activer les tests unitaires en direct](media/live-test-results-start.png)

1. Affichez les résultats des tests dans la fenêtre d’éditeur de code quand vous écrivez et modifiez le code.

   ![Afficher les résultats des tests](media/live-test-results-ui.png)

1. Choisissez les indicateurs des résultats des tests pour afficher d’autres informations.

   ![Choisir les indicateurs des résultats des tests](media/live-test-results-details.png)

Pour plus d’informations, consultez [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Générer des tests unitaires avec IntelliTest

Lorsque vous exécutez IntelliTest, vous pouvez facilement détecter les tests qui échouent et ajouter le code nécessaire pour les corriger. Vous pouvez sélectionner les tests générés à enregistrer dans un projet de test pour fournir une suite de régression. À mesure que vous modifiez votre code, relancez IntelliTest pour synchroniser les tests générés avec les changements de code. Pour savoir comment procéder, voir [Générer des tests unitaires de code avec IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Génération de tests unitaires avec IntelliTest](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>Exécuter des tests unitaires avec l'Explorateur de tests

Utilisez **l’Explorateur de tests** pour exécuter des tests unitaires sur des projets de tests unitaires Visual Studio ou tiers, regrouper des tests en catégories, filtrer la liste de tests et créer, enregistrer et exécuter des sélections de tests. Vous pouvez également déboguer des tests et analyser les performances des tests et la couverture du code. Pour savoir comment procéder, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md).

![Exécution de tests unitaires avec l’Explorateur de tests](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Utiliser la couverture du code pour déterminer la quantité de code testé

Pour déterminer la proportion de code de votre projet qui sera réellement testée par des tests codés, par exemple des tests unitaires, recourez à la fonctionnalité de couverture du code de Visual Studio. Pour assurer une protection efficace contre les bogues, les tests doivent porter sur une part importante du code. Pour savoir comment procéder, voir [Utiliser la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-different-unit-test-framework"></a>Utiliser un autre framework de tests unitaires

Vous pouvez exécuter des tests unitaires dans Visual Studio à l’aide de frameworks de tests tiers tels que Boost, Google et NUnit. Utilisez le plug-in de ce framework pour permettre à Visual Studio Test Runner de fonctionner avec ce dernier.

Voici les étapes à suivre pour activer les frameworks de tests tiers :

1. Dans la barre de menus, choisissez **Outils** > **Extensions et mises à jour**.

1. Dans la boîte de dialogue **Extensions et mises à jour**, développez la catégorie **En ligne**, puis **Visual Studio Marketplace**. Choisissez ensuite **Outils** > **Test en cours**.

   ![Visual Studio Marketplace](media/extensions-and-updates-testing.png)

1. Sélectionnez le framework ou l’adaptateur à installer, puis choisissez **Télécharger**.

1. Créez un projet de bibliothèque de classes, puis ajoutez-le à votre solution.

   ![Nommer le projet de bibliothèque de classes et l’ajouter](media/create3rdpartyunittest3.png)

1. Installez le plug-in. Dans **l’Explorateur de solutions**, sélectionnez le projet de bibliothèque de classes, puis choisissez **Gérer les packages NuGet** dans le menu contextuel.

   ![Gérer les packages NuGet pour installer le plug-in](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) est une extension de Visual Studio que vous pouvez utiliser pour ajouter et mettre à jour des bibliothèques et des outils pour vos projets.

1. Dans la fenêtre **Gestionnaire de package NuGet**, recherchez et sélectionnez le plug-in, puis choisissez **Installer**.

   ![Installer votre framework tiers](media/create3rdpartyunittest4.png)

   Le framework est référencé dans votre projet.

   ![La référence du framework de tests unitaires tiers est ajoutée à votre solution](media/create3rdpartyunittest6.png)

1. Dans le nœud **Références** du projet de bibliothèque de classes, sélectionnez **Ajouter une référence**.

   ![Ajouter une référence au projet](media/createunittest6.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez le projet contenant le code à tester.

   ![Sélectionner le projet de code à tester](media/createunittest7.png)

1. Codez votre test unitaire.

   ![Ajouter du code à votre test unitaire](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>Voir aussi

* [Créer des tests unitaires, commande](create-unit-tests-menu.md)
* [Générer des tests avec IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Exécuter des tests avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md)
* [Déterminer la couverture du code](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Améliorer la qualité du code](improve-code-quality.md)