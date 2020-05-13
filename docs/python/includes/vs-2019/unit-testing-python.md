---
title: Test unitaire de code Python
description: La configuration des tests unitaires pour le code Python dans Visual Studio tire pleinement parti des fonctionnalités de l’Explorateur de tests pour la découverte, l’exécution et le débogage de tests.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933482"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Sélectionnez le cadre de test d’un projet Python

Visual Studio prend en charge deux cadres de test pour Python, [unittest](https://docs.python.org/3/library/unittest.html) et [pytest](https://pytest.org/en/latest/) (disponible dans Visual Studio 2019 à partir de la version 16.3). Par défaut, aucun cadre n’est sélectionné lorsque vous créez un projet Python. Pour spécifier un cadre, cliquez à droite sur le nom du projet dans Solution Explorer et sélectionnez l’option **Propriétés.** Cela ouvre le concepteur du projet, qui vous permet de configurer les tests à travers **l’onglet Test.** À partir de cet onglet, vous pouvez sélectionner le cadre de test que vous souhaitez utiliser pour votre projet. 

* Pour le cadre le **plus unitaire,** le répertoire racine du projet est utilisé pour la découverte des tests. Cet emplacement, ainsi que le modèle de texte pour identifier les tests, peuvent être modifiés sur **l’onglet Test** aux valeurs spécifiées par l’utilisateur.
* Pour le cadre **pytest,** les options de test telles que l’emplacement du test et les modèles de nom de fichier sont spécifiées à l’aide du fichier de configuration pytest .ini standard. Voir la [documentation de référence pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) pour plus de détails.

Une fois que vous avez enregistré votre sélection et vos paramètres de cadre, la découverte de test est initiée dans le Test Explorer. Si la fenêtre Test Explorer n’est pas déjà ouverte, naviguez vers la barre d’outils et sélectionnez **Test** > **Explorer**.

## <a name="configure-testing-for-python-without-a-project"></a>Configurer les tests pour Python sans projet
Visual Studio vous permet d’exécuter et de tester le code Python existant sans projet, [en ouvrant un dossier](../../quickstart-05-python-visual-studio-open-folder.md) avec du code Python. Dans ces circonstances, vous devrez utiliser un fichier **PythonSettings.json** pour configurer les tests. 
1. Ouvrez votre code Python existant à l’aide de l’option **Open a Local Folder.** 

   ![L’écran de démarrage de Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Dans la fenêtre Solution Explorer, cliquez sur l’icône **Afficher tous les fichiers** pour afficher tous les fichiers dans le dossier actuel.

   ![Afficher tous les boutons de fichiers](../../media/unit-test-show-files.png)

1. Naviguez vers le fichier **PythonSettings.json** dans le dossier **Paramètres locaux.** Si vous ne voyez pas ce fichier dans le dossier **Paramètres locaux,** créez-le manuellement.
   
1. Ajoutez le **champ TestFramework** au fichier des paramètres et définissez-le en **test ou** **unitaire** en fonction du cadre de test que vous souhaitez utiliser.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Pour le cadre le **plus unitaire,** si les champs **UnitTestRootDirectory** et **UnitTestPattern** ne sont pas spécifiés dans le fichier PythonSettings.json, ils sont ajoutés et attribués des valeurs par défaut de "." et "test.py" respectivement.

1. Si votre dossier contient un répertoire **de cr** qui est séparé du dossier qui contient vos tests, spécifiez le chemin vers le dossier de **cr cr** en utilisant le champ **SearchPaths** dans votre fichier **PythonSettings.json.**

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Enregistrez vos modifications au fichier PythonSettings.json pour initier la découverte des tests pour le cadre spécifié. 
   > [!Note]
   > Si la fenêtre Test Explorer est déjà ouverte **CTRL** + **R,A** déclenche également la découverte.

## <a name="discover-and-view-tests"></a>Exécuter et voir les tests

Par défaut, Visual Studio identifie les tests **unittest** et `test` **pytest** comme des méthodes dont les noms commencent par . Pour voir la découverte des tests, faites ce qui suit :

1. Ouvrez un [projet Python](../../managing-python-projects-in-visual-studio.md).

1. Une fois que le projet est chargé dans Visual Studio, cliquez à droite sur votre projet dans Solution Explorer et sélectionnez le cadre le **plus unitaire** ou le **pytest** de l’onglet Properties **Test.**
   > [!Note]
   > Si vous utilisez le cadre pytest, vous pouvez spécifier l’emplacement du test et les modèles de nom de fichier à l’aide du fichier de configuration pytest .ini standard. Par défaut, le dossier espace de travail/projet `test_*py` est `*_test.py`utilisé, avec un modèle de et . Voir la [documentation de référence pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) pour plus de détails.

1. Une fois le cadre sélectionné, cliquez à nouveau sur le projet et **sélectionnez Ajouter** > **un nouvel élément,** puis sélectionnez **Python Unit Test** suivi **d’Add**.

1. Cette action crée un fichier *test_1.py* avec `unittest` du code qui importe `unittest.TestCase`le module `unittest.main()` standard, tire une classe de test de , et invoque si vous exécutez le script directement:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Enregistrez le fichier si nécessaire, puis ouvrez **Test Explorer** avec la commande de menu **Test** > **Explorer.**

1. **Test Explorer** recherche vos tests et les affiche comme indiqué ci-dessous. Double-cliquez sur un test pour ouvrir son fichier source.

    ![Explorateur de tests indiquant le test_A par défaut](../../media/unit-test-a-2.png) 

1. En additionnant d’autres tests à votre projet, vous pouvez organiser la vue dans **Test Explorer** à l’aide du menu **Groupe Par** sur la barre d’outils :

    ![Menu Regrouper par de la barre d’outils de l’Explorateur de tests](../../media/unit-test-group-menu-2.png) 

1. Vous pouvez également entrer du texte dans le champ **de recherche** pour filtrer les tests par leur nom.

Pour plus d’informations sur le module et les `unittest` tests d’écriture, consultez la documentation Python [2.7](https://docs.python.org/2/library/unittest.html) ou la documentation Python [3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Exécuter les tests

Dans **Test Explorer,** vous pouvez exécuter des tests de diverses façons :

- L’option **Exécuter tout** permet d’exécuter tous les tests affichés (sauf si des filtres sont appliqués).
- Le menu **Run** vous donne l’ordre d’exécuter échoué, passé, ou ne pas exécuter des tests en tant que groupe.
- Vous pouvez sélectionner un ou plusieurs tests, cliquer dessus avec le bouton droit, puis sélectionner **Exécuter les tests sélectionnés**.

Les tests sont exécutés en arrière-plan et **Test Explorer** met à jour l’état de chaque test au fur et à mesure qu’il se termine :

- Les tests réussis sont marqués par une coche verte, accompagnée du temps nécessaire à l’exécution du test :

    ![Réussite de test_A](../../media/unit-test-A-pass.png)

- Les tests ayant échoué sont indiqués par une croix rouge accompagnée d’un lien **Sortie** qui affiche la sortie de la console et la sortie `unittest` de l’exécution du test :

    ![Échec de test_A](../../media/unit-test-A-fail.png)

    ![Échec de test_A avec motif](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Déboguer les tests

Étant donné que les tests unitaires sont des éléments de code, ils sont exposés à des bogues tout comme n’importe quel autre code et doivent parfois être exécutés dans un débogueur. Dans le débogueur, vous pouvez définir des points d’arrêt, examiner des variables et parcourir le code. Visual Studio fournit également des outils de diagnostic pour les tests unitaires.

> [!Note]
> Par défaut, le débogage de test utilise le ptvsd 4 debugger. Si vous souhaitez plutôt utiliser ptvsd 3, vous pouvez sélectionner **l’option Use Legacy Debugger** sur **Tools** > **Options** > **Python** > **Debugging**. 

Pour commencer à débogage, définissez un point de rupture initial dans votre code, puis cliquez à droite sur le test (ou une sélection) dans **Test Explorer** et sélectionnez **Debug Selected Tests**. Visual Studio démarre le débogueur Python comme il le ferait pour un code d’application.

![Débogage d’un test](../../media/unit-test-debugging.png)

Vous pouvez également utiliser la **couverture du code d’analyse pour les tests sélectionnés**. Pour plus d’informations, consultez [Utiliser la couverture du code pour déterminer la quantité de code testé](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
