---
title: "Mode d’application des chemins de recherche Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 43e42bf246af0ea5df69a2960d9f13ae97784f6a
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Comment Visual Studio utilise les chemins de recherche Python

Dans le cadre de l’utilisation typique de Python, la variable d’environnement `PYTHONPATH` (ou `IRONPYTHONPATH`, etc.) fournit le chemin de recherche par défaut pour les fichiers de module. Autrement dit, lorsque vous utilisez une instruction `from <name> import...` ou `import <name>`, Python recherche un nom correspondant dans les emplacements suivants :

1. Modules intégrés de Python.
1. Dossier contenant le code Python que vous exécutez.
1. « Chemin de recherche du module », comme défini par la variable d’environnement applicable. (Consultez les sections [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Chemin de recherche de module) et [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables d’environnement) dans la documentation Python principale.)

Visual Studio ignore la variable d’environnement de chemin de recherche, même si elle a été définie pour l’ensemble du système. En fait, elle est ignorée *car* elle est définie pour l’ensemble du système et génère donc certaines questions qui ne peuvent pas être traitées automatiquement : Les modules auxquels il est fait référence sont-ils destinés à Python 2.7 ou Python 3.3 ? Vont-ils remplacer les modules de bibliothèque standard ? Le développeur est-il informé de ce comportement ou s’agit-il d’une tentative de piratage ?

Visual Studio fournit ainsi un moyen permettant de spécifier les chemins de recherche directement dans les environnements et les projets. Le code que vous exécutez ou déboguez dans Visual Studio reçoit les chemins de recherche dans la valeur de `PYTHONPATH` (et autres variables équivalentes). En ajoutant des chemins de recherche, Visual Studio inspecte les bibliothèques de ces emplacements et génère des bases de données IntelliSense pour celles-ci (la construction de la base de données peut prendre un certain temps en fonction du nombre de bibliothèques).

Pour ajouter un chemin de recherche, cliquez avec le bouton droit sur l’élément **Chemins de recherche** dans l’Explorateur de solutions, sélectionnez **Add Folder to Search Path...** (Ajouter un dossier au chemin de recherche...), puis sélectionnez le dossier à inclure. Ce chemin d’accès est utilisé pour n’importe quel environnement associé au projet. (Vous pouvez voir des erreurs si l’environnement est basé sur Python 3 et que vous essayez d’ajouter un chemin de recherche à des modules Python 2.7.)

Les fichiers avec une extension `.zip` ou `.egg` peuvent également être ajoutés en tant que chemins de recherche en sélectionnant **Add Zip Archive to Search Path...** (Ajouter une archive zip au chemin de recherche...). À l’instar des dossiers, le contenu de ces fichiers est analysé et mis à disposition d’IntelliSense.

Si vous utilisez régulièrement les mêmes chemins de recherche et si le contenu ne change pas souvent, il peut être plus efficace de l’installer dans votre dossier site-packages. Analysé et stocké ensuite dans la base de données IntelliSense, le chemin de recherche est toujours associé à l’environnement souhaité et aucun chemin de recherche ne doit être ajouté à chaque projet.

## <a name="see-also"></a>Voir aussi

- [Gestion des environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)