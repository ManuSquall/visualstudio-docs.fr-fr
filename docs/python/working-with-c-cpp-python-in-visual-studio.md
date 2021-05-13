---
title: Écrire des extensions C++ pour Python
description: Procédure pas à pas de création d’une extension C++ pour Python en utilisant Visual Studio, CPython et PyBind11, avec le débogage en mode mixte.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 866b588b8b46477b397cda92076780d1955cfa83
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848303"
---
# <a name="create-a-c-extension-for-python"></a>Créer une extension C++ pour Python

Les modules écrits en C++ (ou C) sont couramment utilisés pour étendre les fonctionnalités d’un interpréteur Python et pour fournir un accès aux fonctionnalités de système d’exploitation de bas niveau. Il existe trois principaux types de modules :

- Modules d’accélérateur : Python étant un langage interprété, certaines parties du code peuvent être écrites en C++ pour de meilleures performances.
- Modules de wrapper : exposent des interfaces C/C++ existantes dans le code Python ou une API plus « Pythonique » qui est facile à utiliser à partir de Python.
- Modules d’accès au système de bas niveau : ils sont créés pour accéder aux fonctionnalités de niveau inférieur du `CPython` Runtime, du système d’exploitation ou du matériel sous-jacent.

Cet article vous guide dans la création d’un module d’extension C++ pour `CPython` qui calcule une tangente hyperbolique et l’appelle à partir du code Python. La routine est implémentée en premier dans Python pour illustrer le gain de performances relatif de l’implémentation de la même routine en C++.

Cet article montre également deux façons de rendre C++ disponible pour Python :

- Les `CPython` extensions standard décrites dans la [documentation python](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), qui est recommandé pour C ++ 11 en raison de sa simplicité.

L’exemple terminé de cette procédure pas à pas se trouve dans [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2017 ou version ultérieure avec la charge de travail de **développement python** installée, y compris les **outils de développement natifs python**, qui intègrent la charge de travail et les ensembles d’outils C++ nécessaires pour les extensions natives.

    ![Sélection de l’option Outils de développement natifs Python](media/cpp-install-native.png)

    > [!Tip]
    > L’installation de la charge de travail **Applications de science et analyse des données** inclut par défaut Python et l’option **Outils de développement natifs Python**.

Pour plus d’informations sur les options d’installation, consultez [installer la prise en charge de Python pour Visual Studio](installing-python-support-in-visual-studio.md). Si vous installez python séparément, veillez à sélectionner **Télécharger les symboles de débogage** sous **Options avancées** dans son programme d’installation. Cette option est requise pour utiliser le débogage en mode mixte entre votre code Python et le code natif.

## <a name="create-the-python-application"></a>Créer l’application Python

1. Créez un projet python dans Visual Studio en sélectionnant **fichier**  >  **nouveau**  >  **projet**. Recherchez « Python », sélectionnez le modèle **application python** , attribuez-lui un nom et un emplacement de votre choix, puis sélectionnez **OK**.

1. Dans le fichier *. py* du projet, collez le code suivant (ou entrez-le manuellement pour découvrir certaines des [fonctionnalités d’édition de Python](editing-python-code-in-visual-studio.md)). Ce code calcule une tangente hyperbolique sans utiliser la bibliothèque mathématique et est ce que nous allons accélérer avec les extensions natives.

    > [!Tip]
    > Écrivez votre code en Python pur avant de réécrire en C++. De cette façon, vous pouvez plus facilement vérifier que votre code natif est correct

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Exécutez le programme en utilisant **Déboguer** exécuter  >  **sans débogage** (**CTRL** + **F5**) pour afficher les résultats. Vous pouvez ajuster la variable `COUNT` pour modifier la durée d’exécution des benchmarks. Pour les besoins de cette procédure pas à pas, définissez cette valeur pour que le benchmark dure environ deux secondes.

> [!TIP]
> Lors de l’exécution des tests d’évaluation, utilisez toujours l’exécution du **débogage**  >  **sans débogage** pour éviter la surcharge générée lors de l’exécution du code dans le débogueur Visual Studio.

## <a name="create-the-core-c-projects"></a>Créer les projets C++ principaux

Suivez les instructions de cette section pour créer deux projets C++ identiques nommés « superfastcode » et « superfastcode2 ». Plus tard, vous allez utiliser deux approches différentes dans chaque projet pour exposer le code C++ à python.

1. Cliquez avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis sélectionnez **Ajouter** > **Nouveau projet**. Une solution Visual Studio peut contenir à la fois des projets Python et C++ (ce qui est l’un des avantages de l’utilisation de Visual Studio pour Python).

1. Rechercher « C++ », sélectionnez **Projet vide**, spécifiez le nom « superfastcode » (« superfastcode2 » pour le second projet), puis sélectionnez **OK**.

    > [!Tip]
    > Si vous avez installé **Outils de développement natifs Python** dans Visual Studio, vous pouvez à la place démarrer avec le modèle **Module d’extension Python**, qui dispose déjà d’une grande partie de ce qui est décrit ci-dessous. Pour cette procédure pas à pas, cependant, le fait de démarrer avec un projet vide illustre comment créer le module d’extension étape par étape. Une fois que vous avez compris le processus, le modèle vous permet de gagner du temps lors de l’écriture de vos propres extensions.

1. Créez un fichier C++ dans le nouveau projet en cliquant avec le bouton droit sur le nœud **Fichiers sources**, puis sélectionnez **Ajouter** > **Nouvel élément**, sélectionnez **Fichier C++**, nommez-le `module.cpp`, puis sélectionnez **OK**.

    > [!Important]
    > Un fichier avec l’extension *.cpp* est nécessaire pour activer les pages de propriétés C++ dans les étapes suivantes.

1. Si vous utilisez un Runtime python 64 bits, activez la configuration **x64** à l’aide du menu déroulant dans la barre d’outils principale. Pour un Runtime python 32 bits, activez la configuration **Win32** .

1. Cliquez avec le bouton droit sur le projet C++ dans l’**Explorateur de solutions**, puis sélectionnez **Propriétés**. La valeur de la **configuration** doit **être active (débogage)** et la **plateforme** est **active (x64)** ou **active (Win32)** en fonction de votre sélection à l’étape précédente.

    > [!Tip]
    > Pour vos propres projets, vous souhaiterez configurer des configurations Debug et Release. Ici, nous configurons uniquement la configuration Debug, puis nous la définissons pour utiliser une *version Release* de `CPython` , qui désactive certaines fonctionnalités de débogage du runtime C++, y compris les assertions. L’utilisation `CPython` de fichiers binaires de *débogage* ( `python_d.exe` ) nécessite des paramètres différents.

1. Définissez les propriétés spécifiques décrites dans le tableau suivant, puis sélectionnez **OK**.
    ::: moniker range=">=vs-2019"
    | Onglet | Propriété | Valeur |
    | --- | --- | --- |
    | **Général** | **Général** > **Nom de la cible** | Spécifiez le nom du module comme vous voulez y faire référence à partir de Python dans les instructions `from...import`. Vous utilisez ce même nom dans le code C++ lors de la définition du module pour Python. Si vous souhaitez utiliser le nom du projet comme nom de module, laissez la valeur par défaut **$(ProjectName)**. |
    | | **Paramètres avancés** > **Extension de fichier cible** | **.pyd** |
    | | **Valeurs par défaut du projet** > **Type de configuration** | **Bibliothèque dynamique (.dll)** |
    | **C/C++** > **Général** | **Autres répertoires Include** | Ajoutez le dossier *include* Python en fonction de votre installation, par exemple `c:\Python36\include`.  |
    | **C/C++** > **Préprocesseur** | **Définitions de préprocesseur** | **CPython uniquement** : ajoutez `Py_LIMITED_API;` (point-virgule compris) au début de la chaîne. Cette définition limite certaines des fonctions que vous pouvez appeler à partir de Python et rend le code plus portable entre les différentes versions de Python. Si vous travaillez avec PyBind11, n’ajoutez pas cette définition, car cela provoquerait des erreurs de build. |
    | **C/C++** > **Génération de code** | **Bibliothèque Runtime** | **DLL multithread (/MD)** (Voir l’avertissement ci-dessous) |
    | **Éditeur de liens** > **Général** | **Répertoires de bibliothèques supplémentaires** | Ajoutez le dossier *libs* Python contenant des fichiers *.lib* en fonction de votre installation, par exemple `c:\Python36\libs`. (Veillez à pointer vers le dossier *libs* qui contient des fichiers *.lib*, et *non* vers le dossier *Lib* qui contient des fichiers *.py*.) |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | Onglet | Propriété | Valeur |
    | --- | --- | --- |
    | **Général** | **Général** > **Nom de la cible** | Spécifiez le nom du module comme vous voulez y faire référence à partir de Python dans les instructions `from...import`. Vous utilisez ce même nom dans le code C++ lors de la définition du module pour Python. Si vous souhaitez utiliser le nom du projet comme nom de module, laissez la valeur par défaut **$(ProjectName)**. Pour `python_d.exe` , ajoutez `_d` à la fin du nom. |
    | | **Général** > **Extension de la cible** | **.pyd** |
    | | **Valeurs par défaut du projet** > **Type de configuration** | **Bibliothèque dynamique (.dll)** |
    | **C/C++** > **Général** | **Autres répertoires Include** | Ajoutez le dossier *include* Python en fonction de votre installation, par exemple `c:\Python36\include`.  |
    | **C/C++** > **Préprocesseur** | **Définitions de préprocesseur** | Le cas échéant, remplacez la valeur de **_DEBUG** par **NDEBUG** pour qu’elle corresponde à la version de non-débogage de `CPython` . (Lorsque vous utilisez `python_d.exe` , laissez ce reste inchangé.) |
    | **C/C++** > **Génération de code** | **Bibliothèque Runtime** | **DLL multithread (/MD)** qui correspond à la version de non-débogage de `CPython` . (Lorsque vous utilisez `python_d.exe` , laissez ce reste inchangé.) |
    | **Éditeur de liens** > **Général** | **Répertoires de bibliothèques supplémentaires** | Ajoutez le dossier *libs* Python contenant des fichiers *.lib* en fonction de votre installation, par exemple `c:\Python36\libs`. (Veillez à pointer vers le dossier *libs* qui contient des fichiers *.lib*, et *non* vers le dossier *Lib* qui contient des fichiers *.py*.) |
    ::: moniker-end
    
    > [!Tip]
    > Si vous ne voyez pas l’onglet C/C++ dans les propriétés du projet, cela signifie que le projet ne contient aucun fichier qu’il identifie en tant que fichier source C/C++. Cette situation peut se produire si vous créez un fichier source sans extension *.c* ou *.cpp*. Par exemple, si vous avez accidentellement entré `module.coo` plutôt que `module.cpp` dans la boîte de dialogue Nouvel élément, Visual Studio crée le fichier mais ne définit pas le type de fichier sur « C/c + code », ce qui active l’onglet Propriétés c/C++. Ce type d’inversion reste le cas même si vous renommez le fichier avec `.cpp` . Pour définir correctement le type de fichier, cliquez avec le bouton droit sur le fichier dans **Explorateur de solutions**, sélectionnez **Propriétés**, puis définissez  **type de fichier** sur **code C/C++**.

1. Cliquez avec le bouton droit sur le projet C++ et sélectionnez **Build** pour tester vos configurations ( **Debug** et **Release**). Les fichiers *.pyd* sont situés dans le dossier **solution** sous **Debug** et **Release**, et non dans le dossier du projet C++ lui-même.

1. Ajoutez le code suivant au fichier *module.cpp* du projet C++ :

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Régénérez le projet C++ pour confirmer que votre code est correct.

1. Si vous ne l’avez pas déjà fait, répétez les étapes ci-dessus pour créer un second projet nommé « superfastcode2 » avec un contenu identique.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Convertir les projets C++ en extensions pour Python

Pour transformer la DLL C++ en extension pour Python, vous commencez par modifier les méthodes exportées pour interagir avec les types Python. Ensuite, vous ajoutez une fonction qui exporte le module, ainsi que les définitions des méthodes du module.

Les sections qui suivent expliquent comment effectuer ces étapes à l’aide des `CPython` extensions et PyBind11.

### <a name="cpython-extensions"></a>Extensions CPython

Pour plus d’informations sur ce qui est affiché dans cette section, reportez-vous au manuel de référence de l' [API Python/C](https://docs.python.org/3/c-api/index.html) et plus particulièrement aux [objets de module](https://docs.python.org/3/c-api/module.html) sur Python.org (n’oubliez pas de sélectionner votre version de Python dans le contrôle déroulant en haut à droite pour afficher la documentation appropriée).

1. En haut de *module.cpp*, incluez *Python.h* :

    ```cpp
    #include <Python.h>
    ```

1. Modifiez la méthode `tanh_impl` pour accepter et retourner des types Python (autrement dit, un `PyObject*`) :

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Ajoutez une structure qui définit comment la fonction `tanh_impl` C++ est présentée à Python :

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Ajoutez une structure qui définit le module tel que vous souhaitez y faire référence dans votre code Python, en particulier lors de l’utilisation de l’instruction `from...import`. (Faire correspondre la valeur dans les propriétés du projet sous **Propriétés**  >  de configuration **Général**  >  **Nom** de la cible.) Dans l’exemple suivant, le nom du module « superfastcode » signifie que vous pouvez utiliser `from superfastcode import fast_tanh` dans Python, car `fast_tanh` est défini dans `superfastcode_methods` . (Les noms de fichiers internes au projet C++, tels que *module. cpp*, ne sont pas apparentés.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Ajoutez une méthode que Python appelle quand il charge le module, qui doit être nommé `PyInit_<module-name>` , où &lt; module-name &gt; correspond exactement à la propriété nom **cible général** du projet C++  >   (autrement dit, il correspond au nom du fichier *. pyd* généré par le projet).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Regénérez le projet C++ pour vérifier votre code. Si vous rencontrez des erreurs, consultez la section [Résolution des problèmes](#troubleshooting) ci-dessous.

### <a name="pybind11"></a>PyBind11

Si vous avez effectué les étapes de la section précédente, vous avez certainement remarqué que vous avez utilisé une grande quantité de code réutilisable pour créer les structures de module nécessaires pour le code C++. PyBind11 simplifie le processus via des macros dans un fichier d’en-tête C++ qui produisent le même résultat avec beaucoup moins de code. Pour plus d’informations sur les éléments présentés dans cette section, consultez [Concepts de base de PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Installez PyBind11 avec pip : `pip install pybind11` ou `py -m pip install pybind11`. (Vous pouvez également installer à l’aide de la fenêtre environnements Python, puis utiliser la commande « ouvrir dans PowerShell » pour l’étape suivante.)

1. Dans le même terminal, exécutez `python -m pybind11 --includes` ou `py -m pybind11 --includes` . Cette opération permet d’imprimer la liste des chemins d’accès que vous devez ajouter à la  >    >  propriété **répertoires Include supplémentaires** généraux C/C++ de votre projet (en supprimant le `-I` préfixe, le cas échéant).

1. En haut d’un *module. cpp* actualisé, qui n’inclut pas les modifications de la section précédente, incluez *pybind11. h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. Dans le bas de *module.cpp*, utilisez la macro `PYBIND11_MODULE` pour définir le point d’entrée pour la fonction C++ :

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Générez le projet C++ pour vérifier votre code. Si vous rencontrez des erreurs, consultez la section suivante sur la résolution des problèmes.

### <a name="troubleshooting"></a>Dépannage

La compilation du module C++ peut échouer pour les raisons suivantes :

- Impossible de localiser *Python.h* (**E1696 : impossible d’ouvrir le fichier source « Python.h »** et/ou **C1083 : impossible d’ouvrir le fichier Include : « Python.h » : fichier ou répertoire inexistant**) : vérifiez que le chemin indiqué dans **C/C++** > **Général** > **Autres répertoires Include** dans les propriétés du projet pointe vers le dossier *include* de votre installation de Python. Consultez l’étape 6 sous [Créer le projet C++ principal](#create-the-core-c-projects).

- Impossible de localiser les bibliothèques Python : Vérifiez que le chemin d’accès des  >    >  **répertoires de bibliothèque généraux supplémentaires** dans l’éditeur de liens dans les propriétés du projet pointe vers le dossier *libs* de votre installation Python. Consultez l’étape 6 sous [Créer le projet C++ principal](#create-the-core-c-projects).

- Erreurs de l’éditeur de liens liées à l’architecture cible : modifiez l’architecture de projet de la cible C++ pour qu’elle corresponde à celle de votre installation Python. Par exemple, si vous ciblez **Win32** avec le projet c++, mais que votre installation Python est 64 bits, remplacez le projet c++ par **x64**.

## <a name="test-the-code-and-compare-the-results"></a>Tester le code et comparer les résultats

Maintenant que la DLL est structurée en extensions Python, vous pouvez les référencer à partir du projet Python, importer les modules et utiliser leurs méthodes.

### <a name="make-the-dll-available-to-python"></a>Rendre la DLL disponible pour Python

Il existe deux façons de rendre la DLL disponible pour Python.

La première méthode fonctionne si le projet Python et le projet C++ se trouvent dans la même solution. Accédez à **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **références** de votre projet Python, puis sélectionnez **Ajouter une référence**. Dans la boîte de dialogue qui s’affiche, sélectionnez l’onglet **Projets**, sélectionnez les projets **superfastcode** et **superfastcode2**, puis sélectionnez **OK**.

![Ajout d’une référence au projet superfastcode](media/cpp-add-reference.png)

L’autre méthode, décrite dans les étapes suivantes, installe le module dans votre environnement Python, ce qui le rend disponible pour d’autres projets Python. Pour obtenir une documentation plus complète, visitez le [projet **setuptools**](https://setuptools.readthedocs.io/) .

1. Créez un fichier nommé *setup.py* dans le projet C++ en cliquant avec le bouton droit sur le projet, puis en sélectionnant **Ajouter** > **Nouvel élément**. Sélectionnez ensuite **Fichier C++ (.cpp)**, nommez le fichier `setup.py`, puis sélectionnez **OK** (le fait de nommer le fichier avec l’extension *.py* permet à Visual Studio de le reconnaître comme étant au format Python, malgré l’utilisation du modèle de fichier C++). Quand le fichier apparaît dans l’éditeur, collez-y le code suivant, selon ce qui est approprié pour la méthode d’extension :

    **`CPython` extensions (projet superfastcode) :**

    ```python
    from setuptools import setup, Extension

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(
        name='superfastcode',
        version='1.0',
        description='Python Package with superfastcode C++ extension',
        ext_modules=[sfc_module]
    )
    ```

    **`PyBind11` (projet superfastcode2) :**

    ```python
    from setuptools import setup, Extension
    import pybind11

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2',
        sources=['module.cpp'],
        include_dirs=[pybind11.get_include()],
        language='c++',
        extra_compile_args=cpp_args,
        )

    setup(
        name='superfastcode2',
        version='1.0',
        description='Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules=[sfc_module],
    )
    ```

1. Créez un deuxième fichier nommé *pyproject. toml* dans le projet C++, puis collez-y le code suivant.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. Pour générer l’extension, cliquez avec le bouton droit sur l’onglet Ouvrir *pyproject. toml* et sélectionnez « Copier le chemin d’accès complet » (nous allons supprimer le nom *pyproject. toml* du chemin d’accès avant de l’utiliser).

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur l’environnement python actif, puis sélectionnez *gérer les packages python*.

    > [!Tip]
    > Si vous avez déjà installé le package, celui-ci est répertorié ici. Cliquez sur « X » pour la désinstaller avant de continuer.

1. Collez le chemin d’accès copié dans la zone de recherche et supprimez-le `pyproject.toml` de la fin. Appuyez ensuite sur entrée pour installer à partir de ce répertoire.

    > [!Tip]
    > Si l’installation échoue en raison d’une erreur d’autorisation, ajoutez `--user` et réessayez la commande.


### <a name="call-the-dll-from-python"></a>Appeler la DLL à partir de Python

Après avoir rendu la DLL disponible pour Python comme décrit dans la section précédente, vous pouvez maintenant appeler les fonctions `superfastcode.fast_tanh` et `superfastcode2.fast_tanh2` à partir du code Python, et comparer leurs performances à l’implémentation Python :

1. Ajoutez les lignes suivantes à votre fichier *.py* pour appeler les méthodes exportées à partir des DLL et afficher leur sortie :

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Exécutez le programme Python (**Déboguer**  >  **Démarrer sans débogage** ou **CTRL** + **F5**) et observez que les routines C++ s’exécutent cinq à vingt fois plus rapidement que l’implémentation de Python. Une sortie classique se présente comme suit :

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Si la commande **exécuter sans débogage** est désactivée, cliquez avec le bouton droit sur le projet Python dans **Explorateur de solutions** , puis sélectionnez **définir comme projet de démarrage**.

1. Essayez d’augmenter la variable `COUNT` afin que les différences soient plus marquées. Une version **Debug** du module C++ s’exécute également plus lentement qu’une version **Release** , car la version **Debug** est moins optimisée et contient plusieurs contrôles d’erreurs. N’hésitez pas à basculer entre ces configurations pour la comparaison (mais n’oubliez pas de revenir en arrière et de mettre à jour les propriétés précédemment pour la configuration **Release** ).

Dans la sortie, vous pouvez voir que l’extension PyBind11 n’est pas aussi rapide que l' `CPython` extension, bien qu’elle soit beaucoup plus rapide que l’implémentation python pure. Cette différence est principalement due au fait que nous avons utilisé l' `METH_O` appel, qui ne prend pas en charge plusieurs paramètres, noms de paramètres ou arguments de mots clés. PyBind11 génère un code légèrement plus complexe pour fournir une interface plus python aux appelants, mais étant donné que le code de test appelle la fonction 500 000 fois, les résultats peuvent augmenter sensiblement la surcharge.

Nous pourrions réduire davantage la surcharge en déplaçant la `for` boucle dans le code natif. Cela implique l’utilisation du [protocole Iterator](https://docs.python.org/c-api/iter.html) (ou du `py::iterable` type PyBind11's pour [le paramètre de fonction](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)) pour traiter chaque élément. La suppression des transitions répétées entre Python et C++ est un moyen efficace de réduire le temps nécessaire au traitement de la séquence.

### <a name="troubleshooting"></a>Dépannage

Si vous recevez un `ImportError` lors de la tentative d’importation de votre module, il est probable que l’un des problèmes suivants soit la cause :

* Lors de la génération d’une référence de projet, assurez-vous que vos propriétés de projet C++ correspondent à l’environnement python activé pour votre projet Python, en particulier les répertoires Include et Library.

* Assurez-vous que votre fichier de sortie est nommé `superfastcode.pyd` . Un nom ou une extension différent empêchera l’importation.

* Si vous avez installé votre module à l’aide du fichier *Setup.py* , vérifiez que vous avez exécuté la commande *PIP* dans l’environnement python activé pour votre projet Python. Le développement de l’environnement python dans Explorateur de solutions doit afficher une entrée pour `superfastcode` .

## <a name="debug-the-c-code"></a>Déboguer le code C++

Visual Studio prend en charge le débogage simultané du code Python et du code C++. Cette section décrit pas à pas le processus en utilisant le projet **superfastcode** ; les étapes sont les mêmes pour le projet **superfastcode2**.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet Python, sélectionnez **Propriétés**, l’onglet **Déboguer**, puis l’option **Déboguer** > **Activer le débogage du code natif**.

    > [!Tip]
    > Quand vous activez le débogage du code natif, la fenêtre de sortie Python peut disparaître immédiatement une fois le programme terminé sans afficher la pause habituelle **Appuyez sur une touche pour continuer**. Pour forcer une pause, ajoutez l' `-i` option au champ **exécuter**  >  des arguments de l'**interpréteur** sous l’onglet **Déboguer** lorsque vous activez le débogage de code natif. Cet argument met l’interpréteur Python en mode interactif à la fin du code, à partir duquel il attend que vous appuyiez sur **CTRL** + **Z**  >  **entrée** pour quitter. (Sinon, si vous êtes prêt à modifier votre code Python, vous pouvez ajouter les instructions `import os` et `os.system("pause")` à la fin de votre programme. Ce code double l’invite de pause d’origine.)

1. Sélectionnez **fichier**  >  **Enregistrer** pour enregistrer les modifications apportées aux propriétés.

1. Définissez la configuration de build sur **Déboguer** dans la barre d’outils de Visual Studio.

    ![Définition de la configuration de build sur Debug](media/cpp-set-debug.png)

1. Comme le code met généralement plus de temps à s’exécuter dans le débogueur, vous pouvez remplacer la valeur de la variable `COUNT` de votre fichier *.py* par une valeur cinq fois plus petite (par exemple, en la faisant passer de `500000` à `100000`).

1. Dans votre code C++, définissez un point d’arrêt sur la première ligne de la méthode `tanh_impl`, puis démarrez le débogueur (**F5** ou **Déboguer** > **Démarrer le débogage**). Le débogueur s’arrête quand ce code est appelé. Si le point d’arrêt n’est pas atteint, vérifiez que la configuration est définie sur **Debug** et que vous avez enregistré le projet (ce qui ne se produit pas automatiquement lors du démarrage du débogueur).

    ![Arrêt au niveau d’un point d’arrêt dans le code C++](media/cpp-debugging.png)

1. À ce stade vous pouvez exécuter pas à pas le code C++, examiner les variables, etc. Ces fonctionnalités sont détaillées dans [Déboguer simultanément Python et C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Autres approches

Il existe différents autres moyens de créer des extensions Python, comme décrit dans le tableau suivant. Les deux premières entrées pour `CPython` et `PyBind11` sont ce qui a déjà été abordé dans cet article.

| Approche | Vintage | Utilisateur(s) représentatif(s) | 
| --- | --- | --- |
| Modules d’extension C/C++ pour `CPython` | 1991 | bibliothèque standard | 
| [PyBind11](https://github.com/pybind/pybind11) (recommandé pour C++) | 2015 |  |
| [Cython](https://cython.org) (recommandé pour C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [cryptography](https://cryptography.io/), [pypy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Voir aussi

L’exemple terminé de cette procédure pas à pas se trouve dans [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
