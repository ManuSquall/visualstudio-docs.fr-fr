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
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933482"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Sélectionner l’infrastructure de test pour un projet python

Visual Studio prend en charge deux infrastructures de test pour Python, [UnitTest](https://docs.python.org/3/library/unittest.html) et [pytest](https://pytest.org/en/latest/) (disponibles dans Visual Studio 2019 à partir de la version 16,3). Par défaut, aucune infrastructure n’est sélectionnée lorsque vous créez un projet Python. Pour spécifier une infrastructure, cliquez avec le bouton droit sur le nom du projet dans Explorateur de solutions puis sélectionnez l’option **Propriétés** . Cela ouvre le concepteur de projets, qui vous permet de configurer des tests via l’onglet **test** . À partir de cet onglet, vous pouvez sélectionner l’infrastructure de test que vous souhaitez utiliser pour votre projet. 

* Pour l’infrastructure **UnitTest** , le répertoire racine du projet est utilisé pour la découverte de test. Cet emplacement, ainsi que le modèle de texte pour l’identification des tests, peuvent être modifiés dans l’onglet **test** avec les valeurs spécifiées par l’utilisateur.
* Pour l’infrastructure **pytest** , les options de test, telles que l’emplacement de test et les modèles de nom de fichier, sont spécifiées à l’aide du fichier de configuration pytest. ini standard. Pour plus d’informations, consultez la [documentation de référence pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

Une fois que vous avez enregistré la sélection et les paramètres de votre infrastructure, la découverte des tests est lancée dans l’Explorateur de tests. Si la fenêtre Explorateur de tests n’est pas déjà ouverte, accédez à la barre d’outils et sélectionnez **tester** > l' **Explorateur de tests**.

## <a name="configure-testing-for-python-without-a-project"></a>Configurer des tests pour Python sans projet
Visual Studio vous permet d’exécuter et de tester le code python existant sans projet, en [ouvrant un dossier avec le](../../quickstart-05-python-visual-studio-open-folder.md) code Python. Dans ce cas, vous devez utiliser un fichier **PythonSettings. JSON** pour configurer le test. 
1. Ouvrez votre code python existant à l’aide de l’option **ouvrir un dossier local** . 

   ![L’écran de démarrage de Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Dans la fenêtre de Explorateur de solutions, cliquez sur l’icône **Afficher tous les fichiers** pour afficher tous les fichiers dans le dossier actif.

   ![Bouton Afficher tous les fichiers](../../media/unit-test-show-files.png)

1. Accédez au fichier **PythonSettings. JSON** dans le dossier **Local Settings** . Si vous ne voyez pas ce fichier dans le dossier **Local Settings** , créez-le manuellement.
   
1. Ajoutez le champ **TestFrameWork** au fichier de paramètres et affectez-lui la valeur **pytest** ou **UnitTest** en fonction de l’infrastructure de test que vous souhaitez utiliser.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Pour l’infrastructure **UnitTest** , si les champs **UnitTestRootDirectory** et **UnitTestPattern** ne sont pas spécifiés dans le fichier PythonSettings. JSON, ils sont ajoutés et affectés respectivement les valeurs par défaut « . » et « test *. py ».

1. Si votre dossier contient un répertoire **src** distinct du dossier qui contient vos tests, spécifiez le chemin d’accès au dossier **src** à l’aide du champ **SearchPaths** dans votre fichier **PythonSettings. JSON** .

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Enregistrez vos modifications dans le fichier PythonSettings. JSON pour lancer la découverte de test pour le Framework spécifié. 
   > [!Note]
   > Si la fenêtre Explorateur de tests est déjà ouverte **CTRL** + **R, une** détection est également déclenchée.

## <a name="discover-and-view-tests"></a>Exécuter et voir les tests

Par défaut, Visual Studio identifie les tests **UnitTest** et **pytest** comme des méthodes dont les noms commencent par `test`. Pour voir la découverte des tests, procédez comme suit :

1. Ouvrez un [projet python](../../managing-python-projects-in-visual-studio.md).

1. Une fois le projet chargé dans Visual Studio, cliquez avec le bouton droit sur votre projet dans Explorateur de solutions puis sélectionnez **UnitTest** ou **pytest** Framework dans l’onglet Propriétés de **test** .
   > [!Note]
   > Si vous utilisez l’infrastructure pytest, vous pouvez spécifier l’emplacement de test et les modèles de nom de fichier à l’aide du fichier de configuration pytest. ini standard. Par défaut, le dossier espace de travail/projet est utilisé, avec un modèle de `test_*py` et `*_test.py`. Pour plus d’informations, consultez la [documentation de référence pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

1. Une fois le Framework sélectionné, cliquez à nouveau avec le bouton droit sur le projet et sélectionnez **ajouter** > **nouvel élément**, puis sélectionnez **test unitaire python** suivi de **Ajouter**.

1. Cette action crée un fichier *test_1. py* avec du code qui importe le module de `unittest` standard, dérive une classe de test de `unittest.TestCase`et appelle `unittest.main()` si vous exécutez le script directement :

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Enregistrez le fichier si nécessaire, puis ouvrez l' **Explorateur de tests** à l’aide de la commande de menu **test** > de l’Explorateur de **tests** .

1. L’**Explorateur de tests** recherche des tests dans le projet et les affiche, comme illustré ci-dessous. Double-cliquez sur un test pour ouvrir son fichier source.

    ![Explorateur de tests indiquant le test_A par défaut](../../media/unit-test-a-2.png) 

1. Lorsque vous ajoutez d’autres tests à votre projet, vous pouvez organiser l’affichage dans l' **Explorateur de tests** à l’aide du menu **regrouper par** de la barre d’outils :

    ![Menu Regrouper par de la barre d’outils de l’Explorateur de tests](../../media/unit-test-group-menu-2.png) 

1. Vous pouvez également entrer du texte dans le champ **Recherche** pour filtrer les tests par nom.

Pour plus d’informations sur le module `unittest` et l’écriture de tests, consultez la [documentation python 2,7](https://docs.python.org/2/library/unittest.html) ou la [documentation python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Exécuter les tests

Dans l’**Explorateur de tests**, vous pouvez exécuter les tests de plusieurs façons :

- L’option **Exécuter tout** permet d’exécuter tous les tests affichés (sauf si des filtres sont appliqués).
- Le menu **Exécuter** contient des commandes qui vous permettent d’exécuter les tests non réussis ou réussis, ou bien de ne pas exécuter les tests sous forme de groupe.
- Vous pouvez sélectionner un ou plusieurs tests, cliquer dessus avec le bouton droit, puis sélectionner **Exécuter les tests sélectionnés**.

Les tests s’exécutent en arrière-plan et l’**Explorateur de tests** met à jour l’état de chaque test à la fin de son exécution :

- Les tests réussis sont marqués par une coche verte, accompagnée du temps nécessaire à l’exécution du test :

    ![Réussite de test_A](../../media/unit-test-A-pass.png)

- Les tests ayant échoué sont indiqués par une croix rouge accompagnée d’un lien **Sortie** qui affiche la sortie de la console et la sortie `unittest` de l’exécution du test :

    ![Échec de test_A](../../media/unit-test-A-fail.png)

    ![Échec de test_A avec motif](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Déboguer les tests

Étant donné que les tests unitaires sont des éléments de code, ils sont exposés à des bogues tout comme n’importe quel autre code et doivent parfois être exécutés dans un débogueur. Dans le débogueur, vous pouvez définir des points d’arrêt, examiner des variables et parcourir le code. Visual Studio fournit également des outils de diagnostic pour les tests unitaires.

> [!Note]
> Par défaut, le débogage de test utilise le débogueur ptvsd 4. Si vous souhaitez utiliser à la place ptvsd 3, vous pouvez sélectionner l' **option utiliser le débogueur hérité** sur les **outils** > **options** > le **débogage** **python** > . 

Pour démarrer le débogage, définissez un point d’arrêt initial dans votre code, cliquez avec le bouton droit sur le test (ou une sélection) dans l’**Explorateur de tests**, puis sélectionnez **Déboguer les tests sélectionnés**. Visual Studio démarre le débogueur Python comme il le ferait pour un code d’application.

![Débogage d’un test](../../media/unit-test-debugging.png)

Vous pouvez également utiliser l' **option analyser la couverture du code pour les tests sélectionnés**. Pour plus d’informations, consultez [Utiliser la couverture du code pour déterminer la quantité de code testé](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
