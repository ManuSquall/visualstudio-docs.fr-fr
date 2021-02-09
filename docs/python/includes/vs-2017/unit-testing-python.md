---
title: Test unitaire de code Python
description: La configuration des tests unitaires pour le code Python dans Visual Studio tire pleinement parti des fonctionnalités de l’Explorateur de tests pour la découverte, l’exécution et le débogage de tests.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 612d4bd7d66add8c3fe7c45e8f03ca3531b0b4c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920665"
---
## <a name="discover-and-view-tests"></a>Exécuter et voir les tests

Par convention, Visual Studio identifie les tests comme des méthodes dont le nom commence par `test`. Pour voir ce comportement, effectuez les opérations suivantes :

1. Ouvrez un [projet Python](../../managing-python-projects-in-visual-studio.md) chargé dans Visual Studio, cliquez avec le bouton droit sur le projet, sélectionnez **Ajouter** > **Nouvel élément**, puis sélectionnez **Test unitaire Python** et **Ajouter**.

1. Vous obtenez un fichier *test1.py* contenant du code qui importe le module `unittest` standard, dérive une classe de test à partir de `unittest.TestCase`, et appelle `unittest.main()` si vous exécutez le script directement :

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Enregistrez le fichier si nécessaire, puis ouvrez l’**Explorateur de tests** avec la commande de menu **Test** > **Fenêtres** > **Explorateur de tests**.

1. L' **Explorateur de tests** recherche des tests dans votre projet et les affiche comme indiqué ci-dessous. Double-cliquez sur un test pour ouvrir son fichier source.

    ![Explorateur de tests indiquant le test_A par défaut](../../media/unit-test-A.png)

1. Lorsque vous ajoutez d’autres tests à votre projet, vous pouvez organiser l’affichage dans l' **Explorateur de tests** à l’aide du menu **regrouper par** de la barre d’outils :

    ![Menu Regrouper par de la barre d’outils de l’Explorateur de tests](../../media/unit-test-group-menu.png)

1. Vous pouvez également entrer du texte dans le champ de **recherche** pour filtrer les tests par nom.

Pour plus d’informations sur le `unittest` module et l’écriture de tests, consultez la [documentation Python 2,7](https://docs.python.org/2/library/unittest.html) ou la [documentation python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Exécuter les tests

Dans l' **Explorateur de tests** , vous pouvez exécuter des tests de plusieurs façons :

- L’option **Exécuter tout** permet d’exécuter tous les tests affichés (sauf si des filtres sont appliqués).
- Le menu **exécuter** vous donne les commandes permettant d’exécuter des tests ayant échoué, ayant réussi ou non exécutés en tant que groupe.
- Vous pouvez sélectionner un ou plusieurs tests, cliquer dessus avec le bouton droit, puis sélectionner **Exécuter les tests sélectionnés**.

Les tests s’exécutent en arrière-plan et l' **Explorateur de tests** met à jour l’état de chaque test à mesure qu’il se termine :

- Les tests réussis sont marqués par une coche verte, accompagnée du temps nécessaire à l’exécution du test :

    ![Réussite de test_A](../../media/unit-test-A-pass.png)

- Les tests ayant échoué sont indiqués par une croix rouge accompagnée d’un lien **Sortie** qui affiche la sortie de la console et la sortie `unittest` de l’exécution du test :

    ![Échec de test_A](../../media/unit-test-A-fail.png)

    ![Échec de test_A avec motif](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Déboguer les tests

Étant donné que les tests unitaires sont des éléments de code, ils sont exposés à des bogues tout comme n’importe quel autre code et doivent parfois être exécutés dans un débogueur. Dans le débogueur, vous pouvez définir des points d’arrêt, examiner des variables et parcourir le code. Visual Studio fournit également des outils de diagnostic pour les tests unitaires.

Pour démarrer le débogage, définissez un point d’arrêt initial dans votre code, cliquez avec le bouton droit sur le test (ou une sélection) dans l' **Explorateur de tests** , puis sélectionnez **déboguer les tests sélectionnés**. Visual Studio démarre le débogueur Python comme il le ferait pour un code d’application.

![Débogage d’un test](../../media/unit-test-debugging.png)

Vous pouvez également utiliser l' **option analyser la couverture du code pour les tests sélectionnés**. Pour plus d’informations, consultez [Utiliser la couverture du code pour déterminer la quantité de code testé](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Problèmes connus

- Quand vous démarrez le débogage, Visual Studio semble démarrer et arrêter le débogage, avant de relancer le processus. Il s’agit du comportement attendu.
- Quand vous déboguez plusieurs tests, chacun d’eux est exécuté indépendamment, ce qui interrompt la session de débogage.
- Visual Studio ne parvient pas toujours à démarrer un test lors du débogage. En règle générale, vous pouvez simplement tenter de relancer le débogage du test.
- Lors du débogage, il est possible de sortir un test dans l’implémentation `unittest`. Normalement, l’étape suivante s’exécute jusqu’à la fin du programme et arrête le débogage.
