---
title: Tests unitaires pour Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 3bc7a8f76587e90f9115722c6c7eb04a846f7f07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setting-up-unit-testing-for-python-code"></a>Configuration des tests unitaires pour le code Python

Les tests unitaires sont des éléments de code qui permettent de tester d’autres unités de code dans une application, généralement des fonctions isolées, des classes, etc. Quand une application réussit tous ses tests unitaires, vous avez au moins la garantie que ses fonctionnalités secondaires sont correctes.

Python utilise largement les tests unitaires pour valider des scénarios lors de la conception d’un programme. La prise en charge de Python dans Visual Studio inclut la découverte, l’exécution et le débogage de tests unitaires dans le cadre de votre processus de développement, sans qu’il soit nécessaire d’exécuter les tests séparément.

Cette rubrique fournit une brève description des fonctionnalités de tests unitaires contenues dans Visual Studio avec Python. Pour plus d’informations sur les tests unitaires en général, consultez la page [Tests unitaires sur votre code](../test/unit-test-your-code.md). Regardez également la vidéo [Testing Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567) (Microsoft Virtual Academy, 2 minutes 31 secondes).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567]

## <a name="discovering-and-viewing-tests"></a>Détection et affichage des tests

Par convention, Visual Studio identifie les tests comme des méthodes dont le nom commence par `test`. Pour voir ce comportement, effectuez les opérations suivantes :

1. Ouvrez un [projet Python](python-projects.md) chargé dans Visual Studio, cliquez avec le bouton droit sur votre projet, sélectionnez **Ajouter > Nouvel élément...**, puis sélectionnez **Python Unit Test** (Test unitaire Python) et **Ajouter**.

1. Cette action crée un fichier `test1.py` contenant du code qui importe le module `unittest` standard, dérive une classe de test à partir de `unittest.TestCase` et appelle `unittest.main()` si vous exécutez le script directement :

  ```python
  import unittest

  class Test_test1(unittest.TestCase):
      def test_A(self):
          self.fail("Not implemented")

  if __name__ == '__main__':
      unittest.main()
  ```

1. Enregistrez le fichier si nécessaire, puis ouvrez l’Explorateur de tests avec la commande de menu **Test > Windows > Explorateur de tests**.

1. L’Explorateur de tests recherche des tests dans votre projet et les affiche, comme indiqué ci-dessous. Double-cliquez sur un test pour ouvrir son fichier source.

    ![Explorateur de tests indiquant le test_A par défaut](media/unit-test-A.png)

1. Lorsque vous ajoutez d’autres tests à votre projet, vous pouvez organiser l’affichage dans l’Explorateur de tests à l’aide du menu Regrouper par de la barre d’outils :

    ![Menu Regrouper par de la barre d’outils de l’Explorateur de tests](media/unit-test-group-menu.png)

1. Vous pouvez également saisir du texte dans le champ de recherche pour filtrer les tests par nom.

Pour plus d’informations sur le module `unittest` et sur l’écriture de tests, consultez la [documentation Python 2.7](https://docs.python.org/2/library/unittest.html) ou la [documentation Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="running-tests"></a>Exécution de tests

Dans l’Explorateur de tests, vous pouvez exécuter des tests de plusieurs façons :

- L’option **Exécuter tout** permet d’exécuter tous les tests affichés (sauf si des filtres sont appliqués).
- Le menu **Exécuter...** contient des commandes qui vous permettent d’exécuter les tests ayant échoué ou les tests ayant réussi, ou bien de ne pas exécuter de tests en tant que groupe.
- Vous pouvez sélectionner un ou plusieurs tests, cliquer dessus avec le bouton droit, puis sélectionner **Exécuter les tests sélectionnés**.

Les tests s’exécutent en arrière-plan et l’Explorateur de tests met à jour l’état de chaque test à la fin de son exécution :

- Les tests réussis sont marqués par une coche verte, accompagnée du temps nécessaire à l’exécution du test :

    ![Réussite de test_A](media/unit-test-A-pass.png)

- Les tests ayant échoué sont indiqués par une croix rouge accompagnée d’un lien **Sortie** qui affiche la sortie de la console et la sortie `unittest` de l’exécution du test :

    ![Échec de test_A](media/unit-test-A-fail.png)

    ![Échec de test_A avec motif](media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>Débogage des tests

Étant donné que les tests unitaires sont des éléments de code, ils sont exposés à des bogues tout comme n’importe quel autre code et doivent parfois être exécutés dans un débogueur. Dans le débogueur, vous pouvez définir des points d’arrêt, examiner des variables et parcourir le code. Visual Studio fournit également des outils de diagnostic pour les tests unitaires.

Pour démarrer le débogage, définissez un point d’arrêt initial dans votre code, puis cliquez avec le bouton droit sur le test (ou sur une sélection) dans l’Explorateur de tests et sélectionnez **Debug Selected Tests** (Déboguer les tests sélectionnés). Visual Studio démarre le débogueur Python comme il le ferait pour un code d’application.

![Débogage d’un test](media/unit-test-debugging.png)

Vous pouvez également utiliser les commandes **Analyser la couverture du code pour les tests sélectionnés** et **Profiler le test**, selon votre version de Visual Studio (voir la [matrice des fonctionnalités](python-in-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Problèmes connus

- Quand vous démarrez le débogage, Visual Studio semble démarrer et arrêter le débogage, avant de relancer le processus. Ce comportement est prévu.
- Quand vous déboguez plusieurs tests, chacun d’eux est exécuté indépendamment, ce qui interrompt la session de débogage.
- Visual Studio ne parvient pas toujours à démarrer un test lors du débogage. En règle générale, vous pouvez simplement tenter de relancer le débogage du test.
- Lors du débogage, il est possible de sortir un test dans l’implémentation `unittest`. Normalement, l’étape suivante s’exécute jusqu’à la fin du programme et arrête le débogage.