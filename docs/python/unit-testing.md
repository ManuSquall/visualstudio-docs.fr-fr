---
title: "Tests unitaires dans Python Tools pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3ad6523-5a4e-4209-8977-adc2da305df2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: adf122a478b29674dc2924dcf7d42972a5a3f52e
ms.openlocfilehash: 878bd0baaa0e08a31274645213b222bf6faeb412
ms.lasthandoff: 04/10/2017

---

# <a name="setting-up-unit-testing-for-python-code"></a>Configuration des tests unitaires pour le code Python

Les tests unitaires sont des éléments de code qui permettent de tester d’autres unités de code dans une application, généralement des fonctions isolées, des classes, etc. Lorsqu’une application réussit tous ses tests unitaires, vous avez au moins la garantie que ses fonctionnalités secondaires sont correctes.

Python utilise largement les tests unitaires pour valider des scénarios lors de la conception d’un programme. Python Tools pour Visual Studio (PTVS) prend en charge la détection, l’exécution et le débogage de tests unitaires dans le cadre de votre processus de développement, sans avoir à les exécuter séparément.

Cette rubrique fournit une brève description des fonctionnalités de tests unitaires contenues dans Visual Studio avec Python. Pour plus d’informations sur les tests unitaires en général, consultez la page [Tests unitaires sur votre code](../test/unit-test-your-code.md).

## <a name="discovering-and-viewing-tests"></a>Détection et affichage des tests

Par convention, PTVS identifie les tests comme des méthodes dont le nom commence par « test ». Pour le voir, procédez comme suit :

1. Ouvrez un [projet Python](python-projects.md) chargé dans Visual Studio, cliquez avec le bouton droit sur votre projet, sélectionnez **Ajouter > Nouvel élément...**, puis sélectionnez **Python Unit Test** (Test unitaire Python) et **Ajouter**.

1. Vous obtenez un fichier test1.py contenant du code qui importe le module `unittest` standard, dérive une classe de test à partir de `unittest.TestCase` et appelle `unittest.main()` si vous exécutez le script directement :

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

Étant donné que les tests unitaires sont des éléments de code, ils sont exposés à des bogues tout comme n’importe quel autre code. Ils doivent parfois être exécutés dans un débogueur, dans lequel vous pouvez définir des points d’arrêt, examiner des variables et parcourir le code. PTVS fournit également des outils de diagnostic

Pour démarrer le débogage, définissez un point d’arrêt initial dans votre code, puis cliquez avec le bouton droit sur le test (ou sur une sélection) dans l’Explorateur de tests et sélectionnez **Debug Selected Tests** (Déboguer les tests sélectionnés). Visual Studio démarre le débogueur Python comme il le ferait pour un code d’application.

![Débogage d’un test](media/unit-test-debugging.png)

Vous pouvez également utiliser les commandes **Analyser la couverture du code pour les tests sélectionnés** et **Profiler le test**, selon votre version de PTVS (voir la [matrice des fonctionnalités](python-in-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Problèmes connus

- Lorsque vous démarrez le débogage, Visual Studio semble démarrer et arrêter le débogage, avant de relancer le processus. Il s'agit du comportement attendu.
- Lorsque vous déboguez plusieurs tests, chacun d’eux est exécuté indépendamment, ce qui interrompt la session de débogage.
- Visual Studio ne parvient pas toujours à démarrer un test lors du débogage. En règle générale, vous pouvez simplement tenter de relancer le débogage du test.
- Lors du débogage, il est possible de sortir un test dans l’implémentation `unittest`. Normalement, l’étape suivante s’exécutera jusqu’à la fin du programme et arrêtera le débogage.
