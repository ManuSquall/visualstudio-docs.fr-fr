---
title: Sélection et installation des interpréteurs Python
description: La liste complète des interpréteurs Python pris en charge dans Visual Studio, accompagnée d’instructions brèves pour trouver les programmes d’installation associés.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 6491f5ec5fdcfc1435891cd953287e2c5123538a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548962"
---
# <a name="install-python-interpreters"></a>Installer les interpréteurs Python

Par défaut, l’installation de la charge de travail de développement Python dans Visual Studio 2017 installe également Python 3 (64 bits). Vous pouvez choisir d’installer les versions 32 bits et 64 bits de Python 2, Python 3, Anaconda 2 et Anaconda 3, comme décrit dans la rubrique [Installation](installing-python-support-in-visual-studio.md).

Vous pouvez également installer manuellement l’un des interpréteurs figurant dans le tableau suivant en dehors de Visual Studio installer. Par exemple, si vous avez installé Anaconda 3 avant Visual Studio, vous n’avez pas besoin de le réinstaller avec Visual Studio Installer.

Avec **Visual Studio 2015 et les versions antérieures**, vous devez installer manuellement un des interpréteurs.

Visual Studio (toutes versions) détecte automatiquement chacun des interpréteurs Python installés et l’environnement associé en consultant le Registre (conformément à [PEP 514 – Inscription de Python dans le Registre Windows](https://www.python.org/dev/peps/pep-0514/)). Les installations de Python se trouvent généralement sous **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32 bits) et **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64 bits), puis dans les nœuds correspondant à la distribution (par exemple, **PythonCore** pour CPython et **ContinuumAnalytics** pour Anaconda).

Si Visual Studio ne parvient pas à détecter un environnement installé, consultez la section [Identifier manuellement un environnement existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio affiche tous les environnements connus dans la fenêtre [**Environnements Python**](managing-python-environments-in-visual-studio.md), et détecte automatiquement les mises à jour apportées aux interpréteurs existants.

| Interpréteur | Description |
| --- | --- |
| [CPython](https://www.python.org/) | Interpréteur « natif » et le plus couramment utilisé, disponible en versions 32 bits et 64 bits (version 32 bits recommandée). Il inclut les dernières fonctionnalités du langage, une compatibilité des packages Python maximale, la prise en charge complète du débogage et l’interopérabilité avec [IPython](http://ipython.org/). Consultez aussi : [Should I use Python 2 or Python 3 ?](https://wiki,python.org/moin/Python2orPython3). Notez que Visual Studio 2015 et les versions antérieures ne prennent pas en charge Python 3.6+, et qu’ils peuvent générer des erreurs telles que **Python version 3.6 n’est pas pris en charge**. Utilisez à la place Python 3.5 ou antérieur. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implémentation .NET de Python, disponible en versions 32 bits et 64 bits, fournissant une interopérabilité C#/F#/Visual Basic, un accès aux API .NET, le débogage Python standard (mais pas le débogage en mode mixte C++) et le débogage mixte IronPython/C#. Toutefois, IronPython, ne prend pas en charge les environnements virtuels. |
| [Anaconda](https://www.continuum.io) | Une plateforme de science des données ouverte alimentée par Python, qui inclut la dernière version de CPython et la plupart des packages difficiles à installer. Nous vous la recommandons si vous ne pouvez pas décider autrement. |
| [PyPy](https://www.pypy.org/) | Une implémentation JIT de suivi hautes performances de Python qui convient aux programmes longs et aux situations dans lesquelles vous identifiez des problèmes de performances, mais que vous ne trouvez pas d’autres solutions. Fonctionne avec Visual Studio, mais avec une prise en charge limitée des fonctionnalités de débogage avancées. |
| [Jython](http://www.jython.org/) | Une implémentation de Python sur la Machine virtuelle Java (JVM). Similaire à IronPython, le code s’exécutant dans Jython peut interagir avec les bibliothèques et les classes Java, mais n’est peut-être pas en mesure d’utiliser de nombreuses bibliothèques destinées à CPython. Fonctionne avec Visual Studio, mais avec une prise en charge limitée des fonctionnalités de débogage avancées. |

Pour les développeurs qui souhaitent créer de nouvelles formes de détection pour les environnements Python, consultez [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Détection d’environnement PTVS ; github.com).

## <a name="move-an-interpreter"></a>Déplacer un interpréteur

Si vous déplacez un interpréteur existant vers un nouvel emplacement à l’aide du système de fichiers, Visual Studio ne détectera pas automatiquement la modification.

- Si vous avez spécifié à l’origine l’emplacement de l’interpréteur via la fenêtre **Environnements Python**, modifiez son environnement à l’aide de l’onglet **Configurer** de cette fenêtre pour identifier le nouvel emplacement. Consultez [Identifier manuellement un environnement existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Si vous avez installé l’interpréteur à l’aide d’un programme d’installation, suivez les étapes ci-dessous pour le réinstaller au nouvel emplacement :

  1. Restaurez l’interpréteur Python à son emplacement d’origine.
  2. Désinstallez l’interpréteur à l’aide de son programme d’installation ; cette opération entraîne l’effacement des entrées de Registre.
  3. Réinstallez l’interpréteur à l’emplacement souhaité.
  4. Redémarrez Visual Studio, qui devrait détecter automatiquement le nouvel emplacement à la place de l’ancien.

Ce processus garantit que les entrées de Registre qui identifient l’emplacement de l’interpréteur, utilisées par Visual Studio, sont correctement mises à jour. Le programme d’installation gère également les autres effets secondaires qui pourraient éventuellement se produire.

## <a name="see-also"></a>Voir aussi

- [Gérer des environnements Python](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Chemins de recherche](search-paths.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)
