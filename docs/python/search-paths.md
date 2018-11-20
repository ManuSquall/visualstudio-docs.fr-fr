---
title: Mode d’application des chemins de recherche Python
description: Présentation de la façon dont Visual Studio utilise les chemins de recherche Python dans les environnements et les projets.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: ab55c7cf1daa02416e6192a02a01ee3f9a35f6f0
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607899"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Comment Visual Studio utilise les chemins de recherche Python

Dans le cadre de l’utilisation typique de Python, la variable d’environnement `PYTHONPATH` (ou `IRONPYTHONPATH`, etc.) fournit le chemin de recherche par défaut pour les fichiers de module. Autrement dit, lorsque vous utilisez une instruction `from <name> import...` ou `import <name>`, Python recherche un nom correspondant dans les emplacements suivants :

1. Modules intégrés de Python.
1. Dossier contenant le code Python que vous exécutez.
1. « Chemin de recherche du module », comme défini par la variable d’environnement applicable. (Consultez les sections [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Chemin de recherche de module) et [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables d’environnement) dans la documentation Python principale.)

Visual Studio ignore la variable d’environnement de chemin de recherche, même si elle a été définie pour l’ensemble du système. En fait, elle est ignorée, *car* elle est définie pour l’ensemble du système et entraîne donc certaines questions auxquelles il est impossible de répondre automatiquement : les modules référencés sont-ils destinés à Python 2.7 ou à Python 3.6 ? Vont-ils remplacer les modules de bibliothèque standard ? Le développeur est-il informé de ce comportement ou s’agit-il d’une tentative de piratage ?

Visual Studio fournit ainsi un moyen permettant de spécifier les chemins de recherche directement dans les environnements et les projets. Le code que vous exécutez ou déboguez dans Visual Studio reçoit les chemins de recherche dans la valeur de `PYTHONPATH` (et autres variables équivalentes). En ajoutant des chemins de recherche, Visual Studio inspecte les bibliothèques de ces emplacements et génère des bases de données IntelliSense pour celles-ci lorsque nécessaire (Visual Studio 2017 version 15.5 et versions antérieures ; la construction de la base de données peut prendre un certain temps en fonction du nombre de bibliothèques).

Pour ajouter un chemin de recherche, accédez à l’**Explorateur de solutions**, développez le nœud de votre projet, cliquez avec le bouton droit sur **Chemins de recherche**, puis sélectionnez **Ajouter le dossier au chemin de recherche** :

![Commande Ajouter le dossier au chemin de recherche dans l’Explorateur de solutions](media/search-paths-command.png)

Cette commande permet d’afficher un navigateur dans lequel vous sélectionnez le dossier à inclure.

Si votre variable d’environnement `PYTHONPATH` inclut déjà le ou les dossiers souhaités, utilisez **Ajouter PYTHONPATH au chemin de recherche** en tant que raccourci pratique.

Une fois les dossiers ajoutés aux chemins de recherche, Visual Studio les utilise pour n’importe quel environnement associé au projet. (Vous pouvez voir des erreurs si l’environnement est basé sur Python 3 et que vous essayez d’ajouter un chemin de recherche à des modules Python 2.7.)

Vous pouvez également ajouter les fichiers ayant une extension *.zip* ou *.egg* en tant que chemins de recherche, en sélectionnant la commande **Ajouter une archive zip au chemin de recherche**. À l’instar des dossiers, le contenu de ces fichiers est analysé et mis à disposition d’IntelliSense.

## <a name="see-also"></a>Voir aussi

- [Gérer les environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utiliser requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)
