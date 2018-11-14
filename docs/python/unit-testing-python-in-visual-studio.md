---
title: Tests unitaires pour Python
description: Configuration des tests unitaires pour le code Python dans Visual Studio pour tirer pleinement parti des fonctionnalités de l’Explorateur de tests pour la découverte, l’exécution et le débogage de tests.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e8a3a61b7c77031033c9cdc988753437f25166a1
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607573"
---
# <a name="set-up-unit-testing-for-python-code"></a>Configurer des tests unitaires pour le code Python

Les tests unitaires sont des éléments de code qui permettent de tester d’autres unités de code dans une application, généralement des fonctions isolées, des classes, etc. Quand une application réussit tous ses tests unitaires, vous avez au moins la garantie que ses fonctionnalités secondaires sont correctes.

Python utilise largement les tests unitaires pour valider des scénarios lors de la conception d’un programme. La prise en charge de Python dans Visual Studio inclut la découverte, l’exécution et le débogage de tests unitaires dans le cadre de votre processus de développement, sans qu’il soit nécessaire d’exécuter les tests séparément.

Cet article fournit une brève description des fonctionnalités de tests unitaires contenues dans Visual Studio avec Python. Pour plus d’informations sur les tests unitaires en général, consultez la page [Tests unitaires sur votre code](../test/unit-test-your-code.md).

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | [Regardez une vidéo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567) sur le test unitaire dans Python (2 min31s). |

## <a name="discover-and-view-tests"></a>Exécuter et voir les tests

Par convention, Visual Studio identifie les tests comme des méthodes dont le nom commence par `test`. Pour voir ce comportement, effectuez les opérations suivantes :

1. Ouvrez un [projet Python](managing-python-projects-in-visual-studio.md) chargé dans Visual Studio, cliquez avec le bouton droit sur le projet, sélectionnez **Ajouter** > **Nouvel élément**, puis sélectionnez **Test unitaire Python** et **Ajouter**.

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

1. L’**Explorateur de tests** recherche des tests dans le projet et les affiche, comme illustré ci-dessous. Double-cliquez sur un test pour ouvrir son fichier source.

    ![Explorateur de tests indiquant le test_A par défaut](media/unit-test-A.png)

1. Au fur et à mesure que vous ajoutez des tests supplémentaires au projet, vous pouvez organiser l’affichage dans l’**Explorateur de tests** à l’aide du menu **Regrouper par** de la barre d’outils :

    ![Menu Regrouper par de la barre d’outils de l’Explorateur de tests](media/unit-test-group-menu.png)

1. Vous pouvez également entrer du texte dans le champ **Recherche** pour filtrer les tests par nom.

Pour plus d’informations sur le module `unittest` et sur l’écriture de tests, consultez la [documentation Python 2.7](https://docs.python.org/2/library/unittest.html) ou la [documentation Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Exécuter les tests

Dans l’**Explorateur de tests**, vous pouvez exécuter les tests de plusieurs façons :

- L’option **Exécuter tout** permet d’exécuter tous les tests affichés (sauf si des filtres sont appliqués).
- Le menu **Exécuter** contient des commandes qui vous permettent d’exécuter les tests non réussis ou réussis, ou bien de ne pas exécuter les tests sous forme de groupe.
- Vous pouvez sélectionner un ou plusieurs tests, cliquer dessus avec le bouton droit, puis sélectionner **Exécuter les tests sélectionnés**.

Les tests s’exécutent en arrière-plan et l’**Explorateur de tests** met à jour l’état de chaque test à la fin de son exécution :

- Les tests réussis sont marqués par une coche verte, accompagnée du temps nécessaire à l’exécution du test :

    ![Réussite de test_A](media/unit-test-A-pass.png)

- Les tests ayant échoué sont indiqués par une croix rouge accompagnée d’un lien **Sortie** qui affiche la sortie de la console et la sortie `unittest` de l’exécution du test :

    ![Échec de test_A](media/unit-test-A-fail.png)

    ![Échec de test_A avec motif](media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Déboguer les tests

Étant donné que les tests unitaires sont des éléments de code, ils sont exposés à des bogues tout comme n’importe quel autre code et doivent parfois être exécutés dans un débogueur. Dans le débogueur, vous pouvez définir des points d’arrêt, examiner des variables et parcourir le code. Visual Studio fournit également des outils de diagnostic pour les tests unitaires.

Pour démarrer le débogage, définissez un point d’arrêt initial dans votre code, cliquez avec le bouton droit sur le test (ou une sélection) dans l’**Explorateur de tests**, puis sélectionnez **Déboguer les tests sélectionnés**. Visual Studio démarre le débogueur Python comme il le ferait pour un code d’application.

![Débogage d’un test](media/unit-test-debugging.png)

Vous pouvez également utiliser les commandes **Analyser la couverture du code pour les tests sélectionnés** et **Profiler le test**, selon votre version de Visual Studio (voir la [matrice des fonctionnalités](overview-of-python-tools-for-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Problèmes connus

- Quand vous démarrez le débogage, Visual Studio semble démarrer et arrêter le débogage, avant de relancer le processus. Ce comportement est prévu.
- Quand vous déboguez plusieurs tests, chacun d’eux est exécuté indépendamment, ce qui interrompt la session de débogage.
- Visual Studio ne parvient pas toujours à démarrer un test lors du débogage. En règle générale, vous pouvez simplement tenter de relancer le débogage du test.
- Lors du débogage, il est possible de sortir un test dans l’implémentation `unittest`. Normalement, l’étape suivante s’exécute jusqu’à la fin du programme et arrête le débogage.
