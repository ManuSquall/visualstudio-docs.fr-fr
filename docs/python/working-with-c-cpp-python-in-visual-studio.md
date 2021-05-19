---
title: Écrire des extensions C++ pour Python
description: Cet article vous guide dans la création d’une extension C++ pour Python à l’aide de Visual Studio, CPython et PyBind11, notamment le débogage en mode mixte.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce80ab6647ffc1043bcc452c387abcbdb80a2def
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973438"
---
# <a name="create-a-c-extension-for-python"></a>Créer une extension C++ pour Python

Les modules écrits en C++ (ou C) sont couramment utilisés pour étendre les fonctionnalités d’un interpréteur Python. Ils sont également utilisés pour permettre l’accès aux fonctionnalités du système d’exploitation de bas niveau. 

Les modules se présentent sous trois types principaux :

- **Modules d’accélérateur**: comme Python est un langage interprété, vous pouvez écrire des modules d’accélérateur en C++ pour améliorer les performances.
- **Modules de wrapper**: ces modules exposent des interfaces C/C++ existantes au code python ou exposent une API « Python » plus facile à utiliser à partir de Python.
- **Modules d’accès système de bas niveau**: vous pouvez créer ces modules pour accéder aux fonctionnalités de niveau inférieur du `CPython` Runtime, du système d’exploitation ou du matériel sous-jacent.

Cet article vous guide dans la création d’un module d’extension C++ pour `CPython` qui calcule une tangente hyperbolique et l’appelle à partir du code Python. La routine est implémentée en premier dans Python pour illustrer le gain de performances relatif de l’implémentation de la même routine en C++.

L’article montre également deux façons de rendre l’extension C++ disponible pour Python :

- Utilisez les `CPython` extensions standard, comme décrit dans la [documentation python](https://docs.python.org/3/c-api/).
- Utilisez [PyBind11](https://github.com/pybind/pybind11), que nous recommandons pour c++ 11 en raison de sa simplicité.

Vous trouverez l’exemple terminé dans cette procédure pas à pas sur GitHub à l’adresse [python-Samples-vs-CPP-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2017 ou version ultérieure, avec la charge de travail de développement python installée. La charge de travail comprend les outils de développement natifs Python, qui apportent la charge de travail et les ensembles d’outils C++ nécessaires pour les extensions natives.

    ![Capture d’écran d’une liste d’options de développement Python, en mettant en surbrillance l’option outils de développement natifs Python.](media/cpp-install-native.png)

    > [!NOTE]
    > Lorsque vous installez la charge de travail **applications de science et analyse des données** , Python et l’option **outils de développement natifs python** sont installés par défaut.

Pour plus d’informations sur les options d’installation, consultez [installer la prise en charge de Python pour Visual Studio](installing-python-support-in-visual-studio.md). Si vous installez python séparément, veillez à sélectionner **Télécharger les symboles de débogage** sous **Options avancées** dans son programme d’installation. Cette option est requise pour que vous utilisiez le débogage en mode mixte entre votre code Python et le code natif.

## <a name="create-the-python-application"></a>Créer l’application Python

1. Créez un projet python dans Visual Studio en sélectionnant **fichier**  >  **nouveau**  >  **projet**. Recherchez **python**, sélectionnez le modèle **application python** , entrez un nom et un emplacement, puis sélectionnez **OK**.

1. Dans le fichier *. py* du projet, collez le code suivant. Pour découvrir certaines des [fonctionnalités d’édition de Python](editing-python-code-in-visual-studio.md), essayez d’entrer le code manuellement.  

   Ce code calcule une tangente hyperbolique sans utiliser la bibliothèque mathématique et c’est ce que vous allez accélérer avec les extensions natives.

    > [!Tip]
    > Écrivez votre code en Python pur avant de le réécrire en C++. De cette façon, vous pouvez plus facilement vérifier que votre code natif est correct.

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

1. Pour afficher les résultats, exécutez le programme en sélectionnant **Déboguer**  >  **Démarrer sans débogage** ou en sélectionnant CTRL + F5. 

   Vous pouvez ajuster la variable `COUNT` pour modifier la durée d’exécution des benchmarks. Pour les besoins de cette procédure pas à pas, définissez le nombre de manière à ce que le test d’évaluation prenne environ deux secondes.

   > [!TIP]
   > Quand vous exécutez des tests d’évaluation, utilisez toujours l’exécution du **débogage**  >  **sans débogage**. Cela permet d’éviter la surcharge que vous encourez lorsque vous exécutez le code dans le débogueur Visual Studio.

## <a name="create-the-core-c-projects"></a>Créer les projets C++ principaux

Suivez les instructions de cette section pour créer deux projets C++ identiques, *superfastcode* et *superfastcode2*. Plus tard, vous utiliserez une approche distincte dans chaque projet pour exposer le code C++ à python.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution, puis sélectionnez **Ajouter**  >  **un nouveau projet**. Une solution Visual Studio peut contenir à la fois des projets Python et C++, ce qui constitue l’un des avantages de l’utilisation de Visual Studio pour Python.

1. Effectuez une recherche sur **C++**, sélectionnez **projet vide**, spécifiez **superfastcode** pour le premier projet ou **superfastcode2** pour le deuxième projet, puis sélectionnez **OK**.

    > [!Tip]
    > En guise d’alternative, avec les outils de développement natifs python installés dans Visual Studio, vous pouvez démarrer avec le modèle module d’extension Python. Le modèle contient une grande partie de ce qui est déjà en place. 
    > 
    > Pour cette procédure pas à pas, cependant, le fait de démarrer avec un projet vide illustre comment créer le module d’extension étape par étape. Une fois que vous avez compris le processus, vous pouvez utiliser le modèle pour gagner du temps quand vous écrivez vos propres extensions.

1. Pour créer un fichier C++ dans le nouveau projet, cliquez avec le bouton droit sur le nœud **fichiers sources** , puis sélectionnez **Ajouter**  >  **un nouvel élément**.

1. Sélectionnez **fichier C++**, nommez-le *module. cpp*, puis sélectionnez **OK**.

    > [!Important]
    > Un fichier avec l’extension *.cpp* est nécessaire pour activer les pages de propriétés C++ dans les étapes suivantes.

1. Dans la barre d’outils principale, utilisez le menu déroulant pour effectuer l’une des opérations suivantes :

   * Pour un Runtime python 64 bits, activez la configuration **x64** . 
   * Pour un Runtime python 32 bits, activez la configuration **Win32** .

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet C++, sélectionnez **Propriétés**, puis procédez comme suit : 

   a. Pour la **configuration**, entrez **active (débogage)**.  
   b. Pour **plateforme**, entrez **active (x64)** ou **active (Win32)**, en fonction de votre sélection à l’étape précédente.

    > [!NOTE]
    > Lorsque vous créez vos propres projets, vous souhaiterez configurer les configurations *Debug* et *Release* . Dans cette unité, vous configurez uniquement la configuration de débogage et la définissez pour utiliser une version Release de CPython. Cette configuration désactive certaines fonctionnalités de débogage du runtime C++, y compris les assertions. L’utilisation de fichiers binaires de débogage CPython (*python_d.exe*) requiert des paramètres différents.

1. Définissez les propriétés comme décrit dans le tableau suivant :

    ::: moniker range=">=vs-2019"

    | Onglet | Propriété | Valeur |
    | --- | --- | --- |
    | **Généralités** | **Nom de la cible** | Spécifiez le nom du module pour y faire référence à partir de Python dans les `from...import` instructions. Vous utilisez ce même nom dans le code C++ lorsque vous définissez le module pour Python. Pour utiliser le nom du projet comme nom de module, laissez la valeur par défaut **$\<ProjectName>** .  Pour `python_d.exe` , ajoutez `_d` à la fin du nom. |
    | | **Type de configuration** | **Bibliothèque dynamique (.dll)** |
    | | **Paramètres avancés** > **Extension de fichier cible** | **.pyd** |
    | | **Valeurs par défaut du projet** > **Type de configuration** | **Bibliothèque dynamique (.dll)** |
    | **C/C++** > **Général** | **Autres répertoires Include** | Ajoutez le dossier python *include* en fonction de votre installation (par exemple, `c:\Python36\include` ).  |
    | **C/C++** > **Préprocesseur** | **Définitions de préprocesseur** | Si elle est présente, remplacez la valeur de **_DEBUG** par **NDEBUG** pour qu’elle corresponde à la version de non-débogage de CPython. Lorsque vous utilisez *python_d.exe*, laissez cette valeur inchangée. |
    | **C/C++** > **Génération de code** | **Bibliothèque Runtime** | **DLL multithread (/MD)** qui correspond à la version de non-débogage de CPython. Lorsque vous utilisez *python_d.exe*, laissez cette valeur en tant que **dll de débogage multithread (/MDD)**. |
    | **Éditeur de liens** > **Général** | **Répertoires de bibliothèques supplémentaires** | Ajoutez le dossier python *libs* qui contient les fichiers *. lib* , en fonction de votre installation (par exemple, *c:\Python36\libs*). Veillez à pointer vers le dossier *libs* qui contient les fichiers *. lib* , et *non* le dossier *lib* qui contient les fichiers *. py* . |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Onglet | Propriété | Valeur |
    | --- | --- | --- |
    | **Généralités** | **Général** > **Nom de la cible** | Spécifiez le nom du module pour y faire référence à partir de Python dans les `from...import` instructions. Vous utilisez ce même nom dans le code C++ lorsque vous définissez le module pour Python. Pour utiliser le nom du projet comme nom de module, laissez la valeur par défaut **$\<ProjectName>** . Pour `python_d.exe` , ajoutez `_d` à la fin du nom. |
    | | **Général** > **Extension de la cible** | **.pyd** |
    | | **Valeurs par défaut du projet** > **Type de configuration** | **Bibliothèque dynamique (.dll)** |
    | **C/C++** > **Général** | **Autres répertoires Include** | Ajoutez le dossier python *include* , en fonction de votre installation (par exemple, *c:\Python36\include*).  |
    | **C/C++** > **Préprocesseur** | **Définitions de préprocesseur** | Si elle est présente, remplacez la valeur de **_DEBUG** par **NDEBUG** pour qu’elle corresponde à la version de non-débogage de `CPython` . Lorsque vous utilisez `python_d.exe` , laissez cette valeur inchangée. |
    | **C/C++** > **Génération de code** | **Bibliothèque Runtime** | **DLL multithread (/MD)** qui correspond à la version de non-débogage de `CPython` . Lorsque vous utilisez `python_d.exe` , laissez cette valeur inchangée. |
    | **Éditeur de liens** > **Général** | **Répertoires de bibliothèques supplémentaires** | Ajoutez le dossier python *libs* qui contient les fichiers *. lib* , en fonction de votre installation (par exemple, *c:\Python36\libs*). Veillez à pointer vers le dossier *libs* qui contient les fichiers *. lib* , et *non* le dossier *lib* qui contient les fichiers *. py* . |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > Si l’onglet **c/C++** n’est pas affiché dans les propriétés du projet, le projet ne contient aucun fichier qu’il identifie en tant que fichier source C/c++. Cette condition peut se produire si vous créez un fichier source sans l’extension de fichier *. c* ou *. cpp* . 
    > 
    > Par exemple, si vous avez entré accidentellement *module. Directeur* au lieu de *module. cpp* précédemment dans la boîte de dialogue Nouvel élément, Visual Studio crée le fichier, mais ne définit pas le type de fichier sur *code c/c +*, ce qui active l’onglet Propriétés c/C++. Une telle identification est conservée même si vous renommez le fichier avec une extension de fichier *. cpp* . 
    > 
    > Pour définir correctement le type de fichier, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier et sélectionnez **Propriétés**. Ensuite, pour **type de fichier**, sélectionnez **code C/C++**.

1. Sélectionnez **OK**.

1. Pour tester vos configurations ( *Debug* et *Release*), cliquez avec le bouton droit sur le projet C++, puis sélectionnez **générer**. 

   Vous trouverez les fichiers *. pyd* dans le dossier de *solution* , sous *Debug* et *Release*, et non dans le dossier de projet C++ lui-même.

1. Dans le fichier *module. cpp* du projet C++, ajoutez le code suivant :

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

1. Si vous ne l’avez pas déjà fait, répétez les étapes précédentes pour créer un deuxième projet nommé *superfastcode2* avec une configuration identique.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Convertir les projets C++ en extensions pour Python

Pour que la DLL C++ soit une extension pour Python, vous devez d’abord modifier les méthodes exportées pour interagir avec les types Python. Ensuite, vous ajoutez une fonction qui exporte le module, ainsi que les définitions des méthodes du module.

Les sections qui suivent expliquent comment effectuer ces étapes à l’aide des extensions CPython et PyBind11.

### <a name="use-cpython-extensions"></a>Utiliser les extensions CPython

Pour plus d’informations sur le code présenté dans cette section, consultez le manuel de référence de l' [API Python/C](https://docs.python.org/3/c-api/index.html) et, en particulier, la page [objets du module](https://docs.python.org/3/c-api/module.html) . Veillez à sélectionner votre version de Python dans la liste déroulante en haut à droite.

1. En haut du fichier *module. cpp* , incluez *Python. h*:

    ```cpp
    #include <Python.h>
    ```

1. Modifiez la `tanh_impl` méthode pour accepter et retourner des types Python (autrement dit, a `PyObject*` ) :

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

1. Ajoutez une structure qui définit le module comme vous souhaitez y faire référence dans votre code Python, en particulier lorsque vous utilisez l' `from...import` instruction. 

   Le nom qui est importé dans ce code doit correspondre à la valeur dans les propriétés du projet sous **Propriétés de configuration** nom de la  >    >  **cible** générale. 

   Dans l’exemple suivant, le `"superfastcode"` nom du module signifie que vous pouvez l’utiliser `from superfastcode import fast_tanh` dans Python, car `fast_tanh` est défini dans `superfastcode_methods` . Les noms de fichiers qui sont internes au projet C++, tels que *module. cpp*, sont indirects.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Ajoutez une méthode que Python appelle quand il charge le module, qui doit être nommé `PyInit_<module-name>` , où *\<module-name>* correspond exactement à la propriété du   >  **nom cible** général du projet C++. Autrement dit, il correspond au nom de fichier du fichier *. pyd* généré par le projet.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Regénérez le projet C++ pour vérifier votre code. Si vous rencontrez des erreurs, consultez la section [« résolution des problèmes »](#troubleshoot-compiling-failures) .

### <a name="use-pybind11"></a>Utiliser PyBind11

Si vous avez effectué les étapes de la section précédente, vous avez certainement remarqué que vous avez utilisé une grande quantité de code réutilisable pour créer les structures de module nécessaires pour le code C++. PyBind11 simplifie le processus par le biais de macros dans un fichier d’en-tête C++ qui remplissent le même résultat, mais avec bien moins de code. 

Pour plus d’informations sur le code de cette section, consultez [notions de base de PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst).

1. Installez PyBind11 à l’aide de PIP : `pip install pybind11` ou `py -m pip install pybind11` . 

   Vous pouvez également installer PyBind11 à l’aide de la fenêtre environnements Python, puis utiliser la commande **ouvrir dans PowerShell** pour l’étape suivante.

1. Dans le même terminal, exécutez `python -m pybind11 --includes` ou `py -m pybind11 --includes` . 

   Cela imprime une liste de chemins d’accès que vous devez ajouter à la  >    >  propriété **répertoires Include supplémentaires** généraux C/C++ de votre projet. Veillez à supprimer le `-I` préfixe, s’il est présent.

1. En haut d’un *module. cpp* actualisé qui n’inclut pas les modifications de la section précédente, incluez *pybind11. h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. En bas de *module. cpp*, utilisez la `PYBIND11_MODULE` macro pour définir le point d’entrée de la fonction C++ :

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

1. Générez le projet C++ pour vérifier votre code. Si vous rencontrez des erreurs, consultez la section suivante, « résoudre les problèmes liés à la compilation », pour les solutions.

### <a name="troubleshoot-compiling-failures"></a>Résoudre les échecs de compilation

La compilation du module C++ peut échouer pour les raisons suivantes :

- Erreur : impossible de localiser *Python. h* (**E1696 : impossible d’ouvrir le fichier source « Python. h »** et/ou **C1083 : impossible d’ouvrir le fichier include : « Python. h » : aucun fichier ou répertoire de ce type**) 

  Solution : Vérifiez que le chemin d’accès dans général **C/C++**  >    >  **répertoires Include supplémentaires** dans les propriétés du projet pointe vers le dossier *include* de votre installation Python. Consultez l’étape 6 sous [Créer le projet C++ principal](#create-the-core-c-projects).

- Erreur : impossible de localiser les bibliothèques python 
 
   Solution : Vérifiez que le chemin d' accès des  >    >  **répertoires de bibliothèque supplémentaires** général de l’éditeur de liens dans les propriétés du projet pointe vers le dossier *libs* de votre installation Python. Consultez l’étape 6 sous [Créer le projet C++ principal](#create-the-core-c-projects).

- Erreurs de l’éditeur de liens liées à l’architecture cible
   
   Solution : modifiez l’architecture du projet de la cible C++ pour qu’elle corresponde à celle de votre installation Python. Par exemple, si vous ciblez Win32 avec le projet C++, mais que votre installation Python est 64 bits, remplacez le projet C++ par x64.

## <a name="test-the-code-and-compare-the-results"></a>Tester le code et comparer les résultats

Maintenant que la DLL est structurée en extensions Python, vous pouvez les référencer à partir du projet Python, importer les modules et utiliser leurs méthodes.

### <a name="make-the-dll-available-to-python"></a>Rendre la DLL disponible pour Python

Vous pouvez rendre la DLL disponible pour Python de plusieurs façons. Voici deux approches à prendre en compte : 

* Cette première méthode fonctionne si le projet Python et le projet C++ se trouvent dans la même solution. Effectuez les actions suivantes : 

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **références** de votre projet Python, puis sélectionnez **Ajouter une référence**. 
   1. Dans la boîte de dialogue qui s’affiche, sélectionnez l’onglet **Projets**, sélectionnez les projets **superfastcode** et **superfastcode2**, puis sélectionnez **OK**.

      ![Capture d’écran montrant comment ajouter une référence au projet « superfastcode ».](media/cpp-add-reference.png)

* Une autre méthode installe le module dans votre environnement Python, ce qui rend le module disponible également pour d’autres projets Python. Pour plus d’informations, consultez la [documentation du projet **setuptools**](https://setuptools.readthedocs.io/). Effectuez les actions suivantes :

    1. Créez un fichier nommé *setup.py* dans le projet C++ en cliquant avec le bouton droit sur le projet, puis en sélectionnant **Ajouter** > **Nouvel élément**. 
    
    1. Sélectionnez **fichier C++ (. cpp)**, nommez le fichier *Setup.py*, puis sélectionnez **OK**.
    
       Le fait de nommer le fichier avec l’extension *. py* permet à Visual Studio de le reconnaître en tant que fichier python malgré l’utilisation du modèle de fichier C++. 

       Lorsque le fichier s’affiche dans l’éditeur, collez le code suivant dans celui-ci, en fonction de la méthode d’extension :
    
        **Pour les `CPython` Extensions (projet superfastcode)**:
    
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
    
        **Pour `PyBind11` (projet superfastcode2)**:
    
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
    
    1. Créez un deuxième fichier nommé *pyproject. toml* dans le projet C++, puis collez-y le code suivant :
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Pour générer l’extension, cliquez avec le bouton droit sur l’onglet Ouvrir *pyproject. toml* , puis sélectionnez **copier le chemin d’accès complet**. Vous allez supprimer le nom *pyproject. toml* du chemin d’accès avant de l’utiliser.
    
    1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur l’environnement python actif, puis sélectionnez **gérer les packages python**.
    
        > [!Tip]
        > Si vous avez déjà installé le package, celui-ci est répertorié ici. Avant de continuer, cliquez sur **X** pour le désinstaller.
    
    1. Dans la zone de recherche, collez le chemin d’accès copié, supprimez *pyproject. toml* à la fin, puis sélectionnez entrée pour installer le module à partir de ce répertoire.
    
        > [!Tip]
        > Si l’installation échoue en raison d’une erreur d’autorisation, ajoutez *--User* à la fin, puis réessayez d’exécuter la commande.


### <a name="call-the-dll-from-python"></a>Appeler la DLL à partir de Python

Une fois la DLL disponible pour Python, comme décrit dans la section précédente, vous pouvez appeler les `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` fonctions et à partir du code Python et comparer leurs performances à l’implémentation de Python. Pour appeler la DLL, procédez comme suit :

1. Ajoutez les lignes suivantes dans votre fichier *. py* pour appeler les méthodes qui ont été exportées à partir des dll et afficher leurs sorties :

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Exécutez le programme Python en sélectionnant **Déboguer**  >  **Démarrer sans débogage** ou en sélectionnant CTRL + F5.

    > [!NOTE]
    > Si la commande **exécuter sans débogage** est désactivée, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet Python, puis sélectionnez **définir comme projet de démarrage**.  

    Notez que les routines C++ s’exécutent environ cinq à vingt fois plus rapidement que l’implémentation python. Une sortie classique se présente comme suit :

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. Essayez d’augmenter la variable `COUNT` afin que les différences soient plus marquées. 

    Une version *Debug* du module C++ s’exécute également plus lentement qu’une version *Release* , car la version Debug est moins optimisée et contient plusieurs contrôles d’erreurs. N’hésitez pas à basculer entre ces configurations à des fins de comparaison, mais n’oubliez pas de revenir en arrière et de mettre à jour les propriétés que vous avez définies précédemment pour la configuration Release.

Dans la sortie, vous pouvez voir que l’extension PyBind11 n’est pas aussi rapide que l’extension CPython, même si elle doit être beaucoup plus rapide que l’implémentation python pure. Cette différence est principalement due au fait que vous avez utilisé l' `METH_O` appel, qui ne prend pas en charge plusieurs paramètres, noms de paramètres ou arguments de mots clés. PyBind11 génère un code légèrement plus complexe pour fournir une interface plus de type python aux appelants. Toutefois, étant donné que le code de test appelle la fonction 500 000 fois, les résultats peuvent amplifier la surcharge !

Vous pouvez réduire davantage la surcharge en déplaçant la `for` boucle dans le code natif. Cette approche implique l’utilisation du [protocole Iterator](https://docs.python.org/c-api/iter.html) (ou du `py::iterable` type PyBind11 pour [le paramètre de fonction](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)) pour traiter chaque élément. La suppression des transitions répétées entre Python et C++ est un moyen efficace de réduire le temps nécessaire au traitement de la séquence.

### <a name="troubleshoot-importing-errors"></a>Résoudre les erreurs d’importation

Si vous recevez un `ImportError` message lorsque vous essayez d’importer votre module, vous pouvez le résoudre de l’une des manières suivantes :

* Lorsque vous générez une référence de projet, assurez-vous que vos propriétés de projet C++ correspondent à l’environnement Python qui est activé pour votre projet Python, en particulier les répertoires *include* et *Library* .

* Assurez-vous que votre fichier de sortie est nommé *superfastcode. pyd*. Tout autre nom ou extension empêchera l’importation.

* Si vous avez installé votre module à l’aide du fichier *Setup.py* , vérifiez que vous avez exécuté la commande *PIP* dans l’environnement Python qui est activé pour votre projet Python. Le développement de l’environnement python dans Explorateur de solutions doit afficher une entrée pour *superfastcode*.

## <a name="debug-the-c-code"></a>Déboguer le code C++

Visual Studio prend en charge le débogage simultané du code Python et du code C++. Dans cette section, vous allez parcourir le processus à l’aide du projet *superfastcode* . Le processus est le même pour le projet *superfastcode2* .

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet Python, sélectionnez **Propriétés**, sélectionnez l’onglet **Déboguer** , puis **Sélectionnez l’option débogage**  >  **activer le débogage de code natif** .

    > [!Tip]
    > Lorsque vous activez le débogage de code natif, la fenêtre de sortie python peut se fermer immédiatement après la fin du programme sans vous donner la **touche appuyer sur une touche habituelle pour continuer** la suspension. 
    >
    > Solution : pour forcer une pause après avoir activé le débogage de code natif, ajoutez l' `-i` option au champ **exécuter** l'  >  **interpréteur d’arguments** sous l’onglet **Déboguer** . Cet argument met l’interpréteur Python en mode interactif après l’exécution du code. à partir de là, il attend que vous appuyiez sur Ctrl + Z, puis sur entrée pour fermer la fenêtre. 
    >
    > Si vous n’envisagez pas de modifier votre code Python, vous pouvez également ajouter `import os` des `os.system("pause")` instructions et à la fin de votre programme. Ce code duplique l’invite de pause d’origine.

1. Sélectionnez **fichier**  >  **Enregistrer** pour enregistrer les modifications apportées aux propriétés.

1. Dans la barre d’outils Visual Studio, définissez la configuration de build sur **Debug**.

    ![Capture d’écran du paramètre « Debug » dans la barre d’outils de Visual Studio.](media/cpp-set-debug.png)

1. Étant donné que le code prend généralement plus de temps pour s’exécuter dans le débogueur, vous souhaiterez peut-être modifier la `COUNT` variable de votre fichier *. py* en lui attribuant une valeur qui est environ cinq fois plus petite que la valeur par défaut. Par exemple, remplacez **500000** par **100000**.

1. Dans votre code C++, définissez un point d’arrêt sur la première ligne de la `tanh_impl` méthode, puis démarrez le débogueur en sélectionnant **F5** ou **Déboguer**  >  **Démarrer le débogage**. 

    Le débogueur s’arrête quand le code de point d’arrêt est appelé. Si le point d’arrêt n’est pas atteint, vérifiez que la configuration est définie sur **Debug** et que vous avez enregistré le projet, ce qui ne se produit pas automatiquement lorsque vous démarrez le débogueur.

    ![Capture d’écran du code C++ qui contient un point d’arrêt.](media/cpp-debugging.png)

1. Au point d’arrêt, vous pouvez effectuer un pas à pas détaillé dans le code C++, examiner des variables, et ainsi de suite. Pour plus d’informations sur ces fonctionnalités, consultez [Déboguer en même temps Python et C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Autres approches

Vous pouvez créer des extensions python de différentes manières, comme décrit dans le tableau suivant. Les deux premières lignes, `CPython` et `PyBind11` , sont présentées dans cet article.

| Approche | Vintage | Utilisateurs représentatifs | 
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

Vous trouverez l’exemple terminé dans cette procédure pas à pas sur GitHub à l’adresse [python-Samples-vs-CPP-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).
