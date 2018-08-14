---
title: Utilisation de C++ et Python
description: Procédure pas à pas de création d’une extension C++ pour Python à l’aide de Visual Studio, notamment le débogage en mode mixte.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 289d22798b243a7276d74257b0d3b1f7213b3a32
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586558"
---
# <a name="create-a-c-extension-for-python"></a>Créer une extension C++ pour Python

Les modules écrits en C++ (ou C) sont couramment utilisés pour étendre les fonctionnalités d’un interpréteur Python et pour fournir un accès aux fonctionnalités de système d’exploitation de bas niveau. Il existe trois principaux types de modules :

- Modules d’accélérateur : Python étant un langage interprété, certaines parties du code peuvent être écrites en C++ pour de meilleures performances.
- Modules de wrapper : exposent des interfaces C/C++ existantes dans le code Python ou une API plus « Pythonique » qui est facile à utiliser à partir de Python.
- Modules d’accès au système de bas niveau : créés pour accéder aux fonctionnalités de plus bas niveau du runtime CPython, du système d’exploitation ou du matériel sous-jacent.

Cet article vous guide dans la création d’un module d’extension C++ pour CPython qui calcule une tangente hyperbolique et l’appelle à partir du code Python. La routine est implémentée en premier dans Python pour illustrer le gain de performances relatif de l’implémentation de la même routine en C++.

L’approche choisie ici est celle pour les extensions CPython standard, comme décrit dans la [documentation de Python](https://docs.python.org/3/c-api/). Une comparaison entre cette approche et d’autres méthodes est décrite sous [Autres approches](#alternative-approaches) à la fin de cet article.

L’exemple terminé de cette procédure pas à pas se trouve dans [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Prérequis

- Visual Studio 2017 avec les charges de travail **Développement Desktop en C++** et **Développement Python** installées avec les options par défaut.
- Dans la charge de travail **Développement Python**, cochez également la case de droite **Outils de développement natifs Python**. Cette option définit la plupart de la configuration décrite dans cet article. (Cette option inclut également la charge de travail C++ automatiquement.)

    ![Sélection de l’option Outils de développement natifs Python](media/cpp-install-native.png)

    > [!Tip]
    > L’installation de la charge de travail **Applications de science et analyse des données** inclut par défaut Python et l’option **Outils de développement natifs Python**.

Pour plus d’informations, consultez [Installation de la prise en charge de Python pour Visual Studio](installing-python-support-in-visual-studio.md), notamment les aspects relatifs à l’utilisation d’autres versions de Visual Studio. Si vous installez Python séparément, veillez à sélectionner **Télécharger les symboles de débogage** et **Télécharger les binaires de débogage** sous **Options avancées** dans le programme d’installation. Cette option garantit que vous avez à votre disposition les bibliothèques de débogage nécessaires si vous choisissez d’effectuer une build de débogage.

## <a name="create-the-python-application"></a>Créer l’application Python

1. Créez un projet Python dans Visual Studio en sélectionnant **Fichier** > **Nouveau** > **Projet**. Recherchez « Python », sélectionnez le modèle **Application Python** en lui attribuant un nom et un emplacement appropriés, puis sélectionnez **OK**.

1. L’utilisation de C++ impose d’utiliser un interpréteur Python 32 bits (Python 3.6 recommandé). Dans la fenêtre **Explorateur de solutions** de Visual Studio, développez le nœud du projet, puis le nœud **Environnements Python**. Si l’environnement 32 bits n’apparaît pas par défaut (soit en gras, soit avec l’étiquette **global par défaut**), suivez les instructions de la page [Sélectionner un environnement Python pour un projet](selecting-a-python-environment-for-a-project.md). Si vous n’avez pas d’interpréteur 32 bits, consultez la page [Installer des interpréteurs Python](installing-python-interpreters.md).

1. Dans le fichier *.py* du projet, collez le code suivant qui teste le calcul d’une tangente hyperbolique (implémentée sans utiliser la bibliothèque mathématique pour faciliter la comparaison). N’hésitez pas à entrer le code manuellement pour essayer certaines des [fonctionnalités d’édition de Python](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Exécutez le programme via **Déboguer** > **Exécuter sans débogage** (**Ctrl**+**F5**) pour voir les résultats. Vous pouvez ajuster la variable `COUNT` pour modifier la durée pendant laquelle les benchmarks s’exécutent. Pour les besoins de cette procédure pas à pas, définissez cette valeur pour que chaque benchmark dure environ deux secondes.

## <a name="create-the-core-c-project"></a>Créer le projet C++ principal

1. Cliquez avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis sélectionnez **Ajouter** > **Nouveau projet**. Une solution Visual Studio peut contenir à la fois des projets Python et C++ (ce qui est l’un des avantages de l’utilisation de Visual Studio pour Python).

1. Recherchez « C++ », sélectionnez **Projet vide**, spécifiez un nom (cet article utilise « superfastcode ») et sélectionnez **OK**.

    > [!Tip]
    > Si vous avez installé **Outils de développement natifs Python** dans Visual Studio 2017, vous pouvez plutôt démarrer avec le modèle **Module d’extension Python** qui dispose déjà d’une grande partie de ce qui est décrit ci-dessous. Pour cette procédure pas à pas, cependant, le fait de démarrer avec un projet vide illustre comment créer le module d’extension étape par étape. Une fois que vous avez compris le processus, le modèle vous permet de gagner du temps lors de l’écriture de vos propres extensions.

1. Créez un fichier C++ dans le nouveau projet en cliquant avec le bouton droit sur le nœud **Fichiers sources**, puis sélectionnez **Ajouter** > **Nouvel élément**, sélectionnez **Fichier C++**, nommez-le `module.cpp`, puis sélectionnez **OK**.

    > [!Important]
    > Un fichier avec l’extension *.cpp* est nécessaire pour activer les pages de propriétés C++ dans les étapes suivantes.

1. Cliquez avec le bouton droit sur le projet C++ dans l’**Explorateur de solutions**, puis sélectionnez **Propriétés**.

1. En haut de la boîte de dialogue **Pages de propriétés** qui s’affiche, affectez à **Configuration** la valeur **Toutes les configurations** et à **Plateforme** la valeur **Win32**.

1. Définissez les propriétés spécifiques décrites dans le tableau suivant, puis sélectionnez **OK**.

    | Onglet | Property | Value |
    | --- | --- | --- |
    | **Général** | **Général** > **Nom de la cible** | Spécifiez le nom du module comme vous voulez y faire référence à partir de Python dans les instructions `from...import`. Vous utilisez ce même nom dans le code C++ lors de la définition du module pour Python. Si vous souhaitez utiliser le nom du projet comme nom de module, laissez la valeur par défaut **$(ProjectName)**. |
    | | **Général** > **Extension de la cible** | **.pyd** |
    | | **Valeurs par défaut du projet** > **Type de configuration** | **Bibliothèque dynamique (.dll)** |
    | **C/C++** > **Général** | **Autres répertoires Include** | Ajoutez le dossier *include* Python en fonction de votre installation, par exemple `c:\Python36\include`.  |
    | **C/C++** > **Préprocesseur** | **Définitions de préprocesseur** | Ajoutez `Py_LIMITED_API;` au début de la chaîne (y compris le point-virgule). Cette définition limite certaines des fonctions que vous pouvez appeler à partir de Python et rend le code plus portable entre les différentes versions de Python. |
    | **C/C++** > **Génération de code** | **Bibliothèque runtime** | **DLL multithread (/MD)** (consultez l’avertissement ci-dessous) |
    | **Éditeur de liens** > **Général** | **Répertoires de bibliothèques supplémentaires** | Ajoutez le dossier *libs* Python contenant des fichiers *.lib* en fonction de votre installation, par exemple `c:\Python36\libs`. (Veillez à pointer vers le dossier *libs* qui contient des fichiers *.lib*, et *non* vers le dossier *Lib* qui contient des fichiers *.py*.) |

    > [!Tip]
    > Si vous ne voyez pas l’onglet C/C++ dans les propriétés du projet, cela signifie que le projet ne contient aucun fichier qu’il identifie en tant que fichier source C/C++. Cette situation peut se produire si vous créez un fichier source sans extension *.c* ou *.cpp*. Par exemple, si vous avez accidentellement entré `module.coo` au lieu de `module.cpp` dans la nouvelle boîte de dialogue d’ajout d’élément, Visual Studio crée le fichier, mais ne définit pas le type de fichier « Code C/C++ » qui permet d’activer l’onglet de propriétés C/C++. Une telle erreur d’identification demeure, même si vous renommez le fichier avec l’extension `.cpp`. Pour définir correctement le type de fichier, cliquez avec le bouton droit sur celui-ci dans l’**Explorateur de solutions**, sélectionnez **Propriétés**, puis affectez à **Type de fichier** la valeur **Code C/C++**.

    > [!Warning]
    > Affectez toujours à l’option **C/C++** > **Génération de code** > **Bibliothèque runtime** la valeur **DLL multithread (/MD)**, même pour une configuration Debug, car les ressources binaires Python qui ne sont pas des ressources binaires de débogage sont générées avec ce paramètre. Si vous définissez l’option **DLL de débogage multithread (/MDd)**, la génération d’une configuration **Debug** produit l’ erreur **C1189 : Py_LIMITED_API est incompatible avec Py_DEBUG, Py_TRACE_REFS et Py_REF_DEBUG**. En outre, si vous supprimez `Py_LIMITED_API` pour éviter l’erreur de build, Python se bloque quand vous tentez d’importer le module. (L’incident se produit dans l’appel de la DLL à `PyModule_Create` comme décrit plus loin, avec le message de sortie du type **Erreur de Python irrécupérable : PyThreadState_Get : aucun thread actuel**.)
    >
    > L’option /MDd permet de générer les ressources binaires de débogage Python (par exemple *python_d.exe*), mais sa sélection pour une DLL d’extension provoque toujours l’erreur de build avec `Py_LIMITED_API`.

1. Cliquez avec le bouton droit sur le projet C++, puis sélectionnez **Build** pour tester vos configurations (**Debug** et **Release**). Les fichiers *.pyd* sont situés dans le dossier **solution** sous **Debug** et **Release**, et non dans le dossier du projet C++ lui-même.

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

## <a name="convert-the-c-project-to-an-extension-for-python"></a>Convertir le projet C++ en extension pour Python

Pour transformer la DLL C++ en extension pour Python, vous commencez par modifier les méthodes exportées pour interagir avec les types Python. Ensuite, vous ajoutez une fonction qui exporte le module, ainsi que les définitions des méthodes du module.

Pour obtenir des informations de base sur les éléments présentés dans cette section pour Python 3.x, reportez-vous au manuel [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) et en particulier à [Module Objects](https://docs.python.org/3/c-api/module.html) sur python.org (pensez à sélectionner votre version de Python dans la zone combinée déroulante en haut à droite pour afficher la documentation appropriée).

Si vous utilisez Python 2.7, reportez-vous plutôt aux rubriques [Extending Python 2.7 with C or C++](https://docs.python.org/2.7/extending/extending.html) et [Porting Extension Modules to Python 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. Dans le fichier C++, incluez *Python.h* tout en haut :

    ```cpp
    #include <Python.h>
    ```

1. Modifiez la méthode `tanh_impl` pour accepter et retourner des types Python (autrement dit, un `PyOjbect*`) :

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Ajoutez une structure qui définit comment la fonction `tanh_impl` C++ est présentée à Python :

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Ajoutez une structure qui définit le module tel que vous souhaitez y faire référence dans votre code Python, en particulier lors de l’utilisation de l’instruction `from...import`. (Faites-la correspondre à la valeur indiquée dans les propriétés du projet sous **Propriétés de configuration** > **Général** > **Nom de la cible**.) Dans l’exemple suivant, le nom du module « superfastcode » signifie que vous pouvez utiliser `from superfastcode import fast_tanh` dans Python, car `fast_tanh` est défini dans `superfastcode_methods`. (Les noms de fichiers internes au projet C++, par exemple *module.cpp*, n’ont aucune incidence.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Ajoutez une méthode que Python appelle quand il charge le module, méthode qui doit être nommée `PyInit_<module-name>`, où &lt;module-name&gt; correspond exactement à la propriété **Général** > **Nom de la cible** du projet C++ (en d’autres termes, le nom du fichier *.pyd* généré par le projet).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Affectez la valeur **Release** à la configuration cible, puis regénérez le projet C++ pour vérifier votre code. Si vous rencontrez des erreurs, vérifiez les cas suivants :
    - Impossible de localiser *Python.h* (**E1696 : impossible d’ouvrir le fichier source « Python.h »** et/ou **C1083 : impossible d’ouvrir le fichier Include : « Python.h » : fichier ou répertoire inexistant**) : vérifiez que le chemin indiqué dans **C/C++** > **Général** > **Autres répertoires Include** dans les propriétés du projet pointe vers le dossier *include* de votre installation de Python. Consultez l’étape 6 sous [Créer le projet C++ principal](#create-the-core-c-project).
    - Bibliothèques Python introuvables : vérifiez que le chemin indiqué via **Éditeur de liens** > **Général** > **Répertoires de bibliothèques supplémentaires** dans les propriétés du projet pointe vers le dossier *libs* de votre installation de Python. Consultez l’étape 6 sous [Créer le projet C++ principal](#create-the-core-c-project).
    - Erreurs de l’éditeur de liens liées à l’architecture cible : modifiez l’architecture de projet de la cible C++ pour qu’elle corresponde à celle de votre installation Python. Par exemple, si vous ciblez x64 avec le projet C++, mais que votre installation de Python est x86, modifiez le projet C++ de façon à cibler x86.

## <a name="test-the-code-and-compare-the-results"></a>Tester le code et comparer les résultats

Maintenant que la DLL est structurée comme une extension Python, vous pouvez y faire référence à partir du projet Python, importer le module et utiliser ses méthodes.

### <a name="make-the-dll-available-to-python"></a>Rendre la DLL disponible pour Python

Il existe deux façons de rendre la DLL disponible pour Python.

La première méthode fonctionne si le projet Python et le projet C++ se trouvent dans la même solution. Accédez à l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet Python, puis sélectionnez **Ajouter une référence**. Dans la boîte de dialogue qui s’affiche, sélectionnez l’onglet **Projets**, sélectionnez le projet **superfastcode** (ou le nom que vous utilisez), puis **OK**.

![Ajout d’une référence au projet superfastcode](media/cpp-add-reference.png)

L’autre méthode, décrite dans les étapes suivantes, permet d’installer le module dans l’environnement Python global, ce qui le rend également accessible aux autres projets Python. (Cette méthode exige généralement une actualisation de la base de données d’exécution de code IntelliSense pour cet environnement dans Visual Studio 2017 version 15.5 et versions antérieures. Une actualisation est aussi nécessaire lors de la suppression du module de l’environnement.)

1. Si vous utilisez Visual Studio 2017, exécutez Visual Studio Installer, sélectionnez **Modifier**, **Composants individuels** > **Compilateurs, outils de génération et runtime** > **Ensemble d’outils Visual C++ 2015.3 v140**. Cette étape est nécessaire, car Python (pour Windows) est lui-même généré avec Visual Studio 2015 (version 14.0) et attend que ces outils soient disponibles lors de la génération d’une extension via la méthode décrite ici. (Notez que vous devrez peut-être installer une version 32 bits de Python et cibler la DLL sur Win32 et non sur x64.)

1. Créez un fichier nommé *setup.py* dans votre projet C++ en cliquant avec le bouton droit sur le projet, puis en sélectionnant **Ajouter** > **Nouvel élément**. Sélectionnez ensuite **Fichier C++ (.cpp)**, nommez le fichier `setup.py`, puis sélectionnez **OK** (le fait de nommer le fichier avec l’extension *.py* permet à Visual Studio de le reconnaître comme étant au format Python, malgré l’utilisation du modèle de fichier C++). Quand le fichier s’affiche dans l’éditeur, collez-y le code suivant :

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Consultez la page [Building C and C++ extensions](https://docs.python.org/3/extending/building.html) (python.org) pour afficher la documentation sur ce script.

1. Le code de *setup.py* indique à Python de générer l’extension à l’aide de l’ensemble d’outils Visual C++ pour Visual Studio 2015 à partir de la ligne de commande. Ouvrez une invite de commandes avec élévation de privilèges, accédez au dossier contenant le projet C++ (c’est-à-dire le dossier qui contient *setup.py*), puis entrez la commande suivante :

    ```command
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Appeler la DLL à partir de Python

Une fois que vous avez effectué une des méthodes ci-dessus, vous pouvez appeler la fonction `fast_tanh` à partir du code Python et comparer ses performances à l’implémentation Python :

1. Ajoutez les lignes suivantes à votre fichier *.py* pour appeler la méthode `fast_tanh` exportée à partir de la DLL et afficher sa sortie.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Exécutez le programme Python (**Déboguer** > **Exécuter sans débogage** ou **Ctrl**+**F5**). Vous pouvez noter que la routine C++ s’exécute cinq à 20 fois plus vite que l’implémentation Python. Une sortie classique se présente comme suit :

    ```output
    Running benchmarks with COUNT = 500000
    sequence_tanh took 1.542 seconds

    [tanh(x) for x in d] took 1.087 seconds

    [fast_tanh(x) for x in d] took 0.158 seconds
    ```

    Si la commande **Exécuter sans débogage** est désactivée, cliquez avec le bouton droit sur le projet Python dans l’**Explorateur de solutions**, puis sélectionnez **Définir en tant que projet de démarrage**.

1. Essayez d’augmenter la variable `COUNT` afin que les différences soient plus marquées. Une build **Debug** du module C++ s’exécute également plus lentement qu’une build **Release**, car la build **Debug** est moins optimisée et contient diverses vérifications des erreurs. Vous pouvez basculer entre ces configurations pour les comparer.

## <a name="debug-the-c-code"></a>Déboguer le code C++

Visual Studio prend en charge le débogage simultané du code Python et du code C++.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet Python, sélectionnez **Propriétés**, l’onglet **Déboguer**, puis l’option **Déboguer** > **Activer le débogage du code natif**.

    > [!Tip]
    > Quand vous activez le débogage du code natif, la fenêtre Sortie Python peut disparaître immédiatement à la fin de l’exécution du programme, sans afficher le message de pause habituel **Appuyez sur une touche pour continuer**. Pour forcer une pause, ajoutez l’option `-i` au champ **Exécuter** > **Arguments de l’interpréteur** sous l’onglet **Déboguer** quand vous activez le débogage du code natif. Avec cet argument, l’interpréteur Python passe en mode interactif à la fin du code, où il attend que vous appuyiez sur **Ctrl**+**Z** > **Entrée** pour quitter. (Sinon, si vous êtes prêt à modifier votre code Python, vous pouvez ajouter les instructions `import os` et `os.system("pause")` à la fin de votre programme. Ce code double l’invite de pause d’origine.)

1. Sélectionnez **Fichier** > **Enregistrer** pour enregistrer les changements apportés à la propriété.

1. Définissez la configuration de build **Debug** dans la barre d’outils de Visual Studio.

    ![Définition de la configuration de build sur Debug](media/cpp-set-debug.png)

1. Comme le code met généralement plus de temps à s’exécuter dans le débogueur, vous pouvez remplacer la valeur de la variable `COUNT` de votre fichier *.py* par une valeur cinq fois plus petite (par exemple, en la faisant passer de `500000` à `100000`).

1. Dans votre code C++, définissez un point d’arrêt sur la première ligne de la méthode `tanh_impl`, puis démarrez le débogueur (**F5** ou **Déboguer** > **Démarrer le débogage**). Le débogueur s’arrête quand ce code est appelé. Si le point d’arrêt n’est pas atteint, vérifiez que la configuration est définie à **Debug** et que vous avez enregistré le projet (ce qui ne se produit pas automatiquement au démarrage du débogueur).

    ![Arrêt au niveau d’un point d’arrêt dans le code C++](media/cpp-debugging.png)

1. À ce stade vous pouvez exécuter pas à pas le code C++, examiner les variables, etc. Ces fonctionnalités sont détaillées dans [Déboguer simultanément Python et C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Autres approches

Il existe différents autres moyens de créer des extensions Python, comme décrit dans le tableau suivant. La première entrée pour CPython correspond à ce qui a déjà été présenté dans cet article.

| Approche | Année | Utilisateur(s) représentatif(s) | Avantage(s) | Inconvenient(s) |
| --- | --- | --- | --- | --- |
| Modules d’extension C/C++ pour CPython | 1991 | Bibliothèque standard | [Documentation et didacticiels complets](https://docs.python.org/3/c-api/). Contrôle total. | Compilation, portabilité, gestion des références. Niveau élevé de connaissances en C. |
| [pybind11](https://github.com/pybind/pybind11) (recommandé pour C++) | 2015 |  | Bibliothèque légère et à en-tête uniquement pour la création de liaisons Python de code C++ existant. Peu de dépendances. Compatibilité PyPy. | Plus récente, moins reconnue. Utilisation intensive des fonctionnalités C++11. Très peu de compilateurs pris en charge (Visual Studio est inclus). |
| Cython (recommandé pour C) | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Semblable à Python. Approche hautement reconnue. Performances élevées. | Compilation, nouvelle syntaxe, nouvelle chaîne d’outils. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Fonctionne avec pratiquement tous les compilateurs C++. | Suite volumineuse et complexe de bibliothèques ; contient de nombreuses solutions de contournement pour les anciens compilateurs. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Pas de compilation, large disponibilité. | Accès et mutation des structures C fastidieux et sujets aux erreurs. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Générer des liaisons pour de nombreux langages à la fois. | Surcharge excessive si Python est la seule cible. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilité d’intégration, compatibilité PyPy. | Plus récente, moins reconnue. |

## <a name="see-also"></a>Voir aussi

L’exemple terminé de cette procédure pas à pas se trouve dans [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).