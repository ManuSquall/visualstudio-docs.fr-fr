---
title: "Utilisation de C++ et Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: "Processus et étapes permettant d’écrire un module ou une extension C++ pour Python dans Visual Studio"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: f8a0bef07667e5f876473c966ed3d14a1b84dd0b
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---

# <a name="creating-a-c-extension-for-python"></a>Création d’une extension C++ pour Python

Les modules écrits en C++ (ou C) sont couramment utilisés pour étendre les fonctionnalités d’un interpréteur Python et pour fournir un accès aux fonctionnalités de système d’exploitation de bas niveau. Il existe trois principaux types de modules :

- Modules d’accélérateur : Python étant un langage interprété, certaines parties du code peuvent être écrites en C++ pour de meilleures performances. 
- Modules de wrapper : exposez des interfaces C/C++ existantes dans le code Python ou exposez une API plus « Pythonique » qui utilise les fonctionnalités du langage Python pour être plus facile à utiliser.
- Modules d’accès au système de bas niveau : créés pour accéder aux fonctionnalités de plus bas niveau du runtime CPython, du système d’exploitation ou du matériel sous-jacent. 

Cette rubrique vous guide dans la création d’un module d’extension C++ pour CPython qui calcule une tangente hyperbolique et l’appelle à partir du code Python. Pour illustrer la différence de performances, vous allez tout d’abord créer et tester la routine dans Python.

L’approche choisie ici est celle pour les extensions CPython standard, comme décrit dans la [documentation de Python](https://docs.python.org/3/c-api/). Une comparaison entre cette approche et d’autres méthodes est décrite sous [Autres approches](#alternative-approaches) à la fin de cette rubrique.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas est écrite pour Visual Studio 2017 avec les charges de travail **Développement Desktop en C++** et **Développement Python** et leurs options par défaut (par exemple, Python 3.6 comme interpréteur par défaut). Dans la charge de travail **Développement Python**, cochez aussi la case située à droite pour **Outils de développement natifs Python**, qui définit la plupart des options décrites dans cette rubrique. (Cette option inclut également la charge de travail C++ automatiquement.) 

![Sélection de l’option Outils de développement natifs Python](~/python/media/cpp-install-native.png)

Pour plus d’informations, consultez [Installation de la prise en charge de Python pour Visual Studio](installation.md), notamment l’utilisation d’autres versions de Visual Studio. Si vous installez Python séparément, veillez à sélectionner **Télécharger les symboles de débogage** et **Télécharger les binaires de débogage** sous **Options avancées** dans le programme d’installation. Vous êtes ainsi certain d’avoir à votre disposition les bibliothèques de débogage nécessaires si vous choisissez d’effectuer une build Debug.

> [!Note]
> Python est également disponible via la charge de travail **Applications de science et analyse des données**, qui inclut Anaconda 3 64 bits (avec la dernière version de CPython) et l’option **Outils de développement natifs Python** par défaut.

## <a name="create-the-python-application"></a>Créer l’application Python

1. Pour créer un projet Python dans Visual Studio, sélectionnez la commande de menu **Fichier > Nouveau > Projet**, recherchez « Python », choisissez le modèle **Application Python** en lui attribuant un nom et un emplacement appropriés, puis sélectionnez **OK**.

1. Dans le fichier `.py` du projet, collez le code suivant qui teste le calcul d’une tangente hyperbolique (implémentation sans utiliser la bibliothèque mathématique pour faciliter la comparaison). N’hésitez pas à entrer le code manuellement pour essayer certaines des [fonctionnalités d’édition de Python](code-editing.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 100000
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
        '''Applies the hyperbolic tanger function to map all values in
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
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Exécutez le programme en utilisant **Déboguer > Exécuter sans débogage** (Ctrl+F5) pour afficher les résultats. Vous verrez que l’exécution de chaque test d’évaluation prend plusieurs secondes.

## <a name="create-the-core-c-project"></a>Créer le projet C++ principal

1. Cliquez avec le bouton droit sur la solution dans l’Explorateur de solutions, puis sélectionnez **Ajouter > Nouveau projet...**. Une solution Visual Studio peut contenir à la fois des projets Python et C++.

1. Recherchez « C++ », sélectionnez **Projet vide**, spécifiez un nom (par exemple, TanhBenchmark) et sélectionnez **OK**. Remarque : Si vous avez installé **Outils de développement natifs Python** avec Visual Studio 2017, vous pouvez démarrer avec le modèle **Module d’extension Python** qui dispose déjà d’une grande partie de ce qui est décrit ici. Pour cette procédure pas à pas, cependant, le fait de démarrer avec un projet vide illustre comment créer le module d’extension étape par étape.

1. Créez un fichier C++ dans le nouveau projet en cliquant avec le bouton droit sur le nœud **Fichiers sources**, puis sélectionnez **Ajouter > Nouvel élément...**, **Fichier C++**, donnez-lui un nom (comme `module.cpp`), puis sélectionnez **OK**. Cette étape est nécessaire pour activer les pages de propriétés C++ dans les prochaines étapes.

1. Cliquez avec le bouton droit sur le nouveau projet, sélectionnez **Propriétés** et, en haut de la boîte de dialogue **Pages de propriétés** qui s’affiche, affectez à **Configuration** la valeur **Toutes les configurations**.

1. Définissez les propriétés spécifiques comme décrit ci-dessous, puis sélectionnez **Appliquer** (vous devrez peut-être cliquer en dehors d’un champ modifiable pour que le bouton **Appliquer** soit disponible).

    | Onglet | Propriété | Valeur | 
    | --- | --- | --- |
    | Général | Général > Nom de la cible | Définissez cette propriété pour qu’elle corresponde exactement au nom du module tel que Python le voit. |
    | | Général > Extension de la cible | .pyd |
    | | Valeurs par défaut du projet > Type de configuration | Bibliothèque dynamique (.dll) |
    | C/C++ > Général | Autres répertoires Include | Ajoutez le dossier `include` Python en fonction de votre installation, par exemple `c:\Python36\include` |     
    | C/C++ > Génération de code | Bibliothèque Runtime | DLL multithread (/MD) (voir l’avertissement ci-dessous) |
    | C/C++ > Préprocesseur | Définitions de préprocesseur | Ajoutez `Py_LIMITED_API;` au début de la chaîne. Cette action limite certaines des fonctions que vous pouvez appeler à partir de Python et rend le code plus portable entre les différentes versions de Python. |
    | Éditeur de liens > Général | Répertoires de bibliothèques supplémentaires | Ajoutez le dossier `lib` Python contenant des fichiers `.lib` en fonction de votre installation, par exemple `c:\Python36\libs`. (Veillez à pointer vers le dossier `libs` qui contient des fichiers `.lib`, et *pas* vers le dossier `Lib` qui contient des fichiers `.py`.) | 

    > [!Tip]
    > Si vous ne voyez pas l’onglet C/C++, le projet ne contient aucun fichier qu’il identifie en tant que fichier source C/C++. Ce cas peut se produire si vous créez un fichier source sans extension `.c` ni `.cpp`. Par exemple, si vous avez accidentellement entré `module.coo` au lieu de `module.cpp` dans la nouvelle boîte de dialogue d’ajout d’élément, Visual Studio crée le fichier, mais ne définit pas le type de fichier « Code C/C++ » qui permet d’activer l’onglet de propriétés C/C++. Tel est le cas même si vous renommez le fichier avec l’extension `.cpp`. Pour corriger ce problème, cliquez avec le bouton droit sur le fichier dans l’Explorateur de solutions, sélectionnez **Propriétés**, puis affectez à **Type de fichier** la valeur **Code C/C++**.

    > [!Warning]
    > N’affectez pas à l’option **C/C++ > Génération de code > Bibliothèque runtime** la valeur « DLL de débogage multithread (/MDd) » même pour une configuration Debug. Vous devez sélectionner le runtime « DLL multithread (/MD) » parce que les binaires Python qui ne sont pas de débogage sont générés avec cette option. S’il vous arrive de définir l’option /MDd, une erreur du type *C1189 : Py_LIMITED_API est incompatible avec Py_DEBUG, Py_TRACE_REFS et Py_REF_DEBUG* s’affiche lors de la création d’une configuration Debug de votre DLL. En outre, si vous supprimez `Py_LIMITED_API` pour éviter l’erreur de build, Python se bloque quand vous tentez d’importer le module. (L’incident se produit dans l’appel de la DLL à `PyModule_Create` comme décrit plus loin, avec le message de sortie du type *Erreur de Python irrécupérable : PyThreadState_Get : aucun thread actuel*.)
    >
    > Notez que l’option /MDd permet de générer les binaires de débogage Python (par exemple, python_d.exe), mais sa sélection pour une DLL d’extension provoque toujours l’erreur de build avec `Py_LIMITED_API`.
   
1. Cliquez avec le bouton droit sur le projet C++ et sélectionnez **Build** pour tester vos configurations (Debug et Release). Notez que vous trouverez les fichiers `.pyd` dans le dossier *solution* sous **Debug** et **Release**, et pas dans le dossier du projet C++ lui-même.

1. Ajoutez le code suivant au fichier `.cpp` principal du projet C++ :

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

    double tanh(x) {
        return sinh(x) / cosh(x);
    }
    ```

1. Régénérez le projet C++ pour confirmer que votre code est correct.


## <a name="convert-the-c-project-to-an-extension-for-python"></a>Convertir le projet C++ en extension pour Python

Pour transformer la DLL C++ en extension pour Python, vous devez modifier la méthode exportée pour interagir avec les types Python. Vous devez ensuite ajouter une fonction qui exporte le module, ainsi que les définitions des méthodes du module. Pour obtenir des informations de base sur ce qui est présenté ici, reportez-vous au manuel [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) et en particulier à [Module Objects](https://docs.python.org/3/c-api/module.html) sur python.org. (Pensez à sélectionner votre version de Python à partir de la liste déroulante en haut à gauche.)

1. Dans le fichier C++, incluez `Python.h` en haut :

    ```cpp
    include <Python.h>
    ```

1. Modifiez la méthode `tanh` pour accepter et retourner des types Python :

    ```cpp
    PyObject* tanh(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Ajoutez une structure qui définit comment la fonction `tanh` C++ est présentée à Python :

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Ajoutez une structure qui définit le module tel que Python pourra le voir :

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Ajoutez une méthode que Python appelle quand il charge le module, qui doit être nommée `PyInit_<module-name>` où *&lt;nom_module&gt;* correspond exactement à la propriété **Général > Nom de la cible** du projet C++ (autrement dit, au nom du fichier `.pyd` généré par le projet).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Régénérez la DLL pour vérifier votre code.

## <a name="test-the-code-and-compare-the-results"></a>Tester le code et comparer les résultats

Maintenant que la DLL est structurée comme une extension Python, vous pouvez y faire référence à partir du projet Python, importer le module et utiliser ses méthodes.

Il existe deux façons de rendre la DLL disponible pour Python. Tout d’abord, vous pouvez ajouter une référence à partir du projet Python au projet C++, sous réserve qu’ils figurent dans la même solution Visual Studio :

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet Python et sélectionnez **Références**. Dans la boîte de dialogue, sélectionnez l’onglet **Projets**, le projet **superfastcode**, puis **OK**.

Ensuite, vous pouvez installer le module dans l’environnement Python global, ce qui le rend également accessible aux autres projets Python. Notez que cette opération nécessite généralement une actualisation de la base de données de saisie semi-automatique IntelliSense pour cet environnement, tout comme la suppression du module de l’environnement.

1. Si vous utilisez Visual Studio 2017, exécutez le programme d’installation de Visual Studio, sélectionnez **Modifier**, **Composants individuels > Compilateurs, outils de génération et runtime > Ensemble d’outils VC++ 2015.3 v140**. En effet, Python (pour Windows) est généré avec Visual Studio 2015 (version 14.0) et attend que ces outils soient accessibles lors de la création d’une extension via la méthode décrite ici.

1. Créez un fichier nommé `setup.py` dans votre projet C++ : cliquez avec le bouton droit sur le projet, sélectionnez **Ajouter > Nouveaux éléments...*, recherchez « Python », sélectionnez **Fichier Python**, nommez-le setup.py et sélectionnez **OK**. Quand le fichier s’affiche dans l’éditeur, collez-y le code suivant :

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    Consultez la page [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (python.org) pour afficher la documentation sur ce script.

1. Le code `setup.py` indique à Python de créer l’extension (à l’aide de l’ensemble d’outils Visual Studio 2015 C++), ce qui se produit à partir de la ligne de commande. Ouvrez une invite de commandes avec élévation de privilèges, accédez au dossier contenant le projet C++ (et `setup.py`), puis entrez la commande suivante :

    ```bash
    pip install .
    ```

Vous pouvez maintenant appeler le code `tanh` du module et comparer ses performances à l’implémentation de Python :

1. Ajoutez les lignes suivantes à `tanhbenchmark.py` pour appeler la méthode `fast_tanh` exportée à partir de la DLL et l’ajouter à la sortie du test d’évaluation. Si vous tapez l’instruction `from s` manuellement, `superfastcode` s’affiche dans la liste de saisie semi-automatique et, après avoir tapé `import`, la méthode `fast_tanh` apparaît.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Exécutez le programme Python et vous verrez que l’exécution de la routine C++ est environ 15 à 20 fois plus rapide que l’implémentation de Python.

## <a name="debug-the-c-code"></a>Déboguer le code C++

Avec la [prise en charge de Python dans Visual Studio](installation.md), vous pouvez [déboguer simultanément le code Python et C++](debugging-mixed-mode.md). Pour ce faire, effectuez les étapes suivantes :

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet Python, sélectionnez **Propriétés**, l’onglet **Déboguer**, puis l’option **Déboguer > Permettre le débogage du code natif**.

    > [!Tip]
    > Quand vous activez le débogage du code natif, la fenêtre de sortie Python peut disparaître immédiatement une fois le programme terminé sans afficher la pause habituelle « Appuyez sur une touche pour continuer... ». Pour forcer une pause, ajoutez l’option `-i` au champ **Exécuter > Arguments de l’interpréteur** sous l’onglet **Déboguer** quand vous activez le débogage du code natif. L’interpréteur Python passe ainsi en mode interactif à la fin du code, où il attend que vous appuyiez sur Ctrl+Z, Entrée pour quitter. (Sinon, si vous êtes prêt à modifier votre code Python, vous pouvez ajouter les instructions `import os` et `os.system("pause")` à la fin de votre programme. Cela double l’invite de pause d’origine.)

1. Dans votre code C++, définissez un point d’arrêt sur la première ligne de la méthode `tanh`, puis démarrez le débogueur. Vous verrez que le débogueur s’arrête quand ce code est appelé :

    ![Arrêt au niveau d’un point d’arrêt dans le code C++](~/python/media/cpp-debugging.png)

1. À ce stade vous pouvez, entre autres, parcourir le code C++ et examiner des variables comme expliqué dans [Débogage simultané de code Python et C++](debugging-mixed-mode.md).

## <a name="alternative-approaches"></a>Autres approches 

Il existe d’autres moyens de créer des extensions Python, comme décrit dans le tableau ci-dessous. La première entrée pour CPython représente ce qui a déjà été abordé dans cette rubrique.

| Approche | Année | Utilisateur(s) représentatif(s) | Avantage(s) | Inconvenient(s) |
| --- | --- | --- | --- | --- |
| Modules d’extension C/C++ pour CPython | 1991 | Bibliothèque standard | [Documentation et didacticiels complets](https://docs.python.org/3/c-api/). Contrôle total. | Compilation, portabilité, gestion des références. Niveau élevé de connaissances en C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Générer des liaisons pour de nombreux langages à la fois. | Surcharge excessive si Python est la seule cible. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Pas de compilation, large disponibilité. | Accès et mutation des structures C fastidieux et sujets aux erreurs. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Semblable à Python. Approche hautement reconnue. Performances élevées. | Compilation, nouvelle syntaxe et chaîne d’outils. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilité d’intégration, compatibilité PyPy. | Nouvelle approche, moins reconnue. |

