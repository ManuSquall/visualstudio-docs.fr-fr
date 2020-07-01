---
title: Mode d’application des chemins de recherche Python
description: Visual Studio fournit un moyen plus spécifique de spécifier des chemins de recherche pour les environnements et les projets afin d’éviter d’utiliser des variables à l’échelle du système.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3a23afff970405bf7ae1bbd1c8aad326eb133780
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520378"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Comment Visual Studio utilise les chemins de recherche Python

Dans le cadre de l’utilisation typique de Python, la variable d’environnement `PYTHONPATH` (ou `IRONPYTHONPATH`, etc.) fournit le chemin de recherche par défaut pour les fichiers de module. Autrement dit, lorsque vous utilisez une instruction `from <name> import...` ou `import <name>`, Python recherche un nom correspondant dans les emplacements suivants :

1. Modules intégrés de Python.
1. Dossier contenant le code Python que vous exécutez.
1. « Chemin de recherche du module », comme défini par la variable d’environnement applicable. (Consultez les sections [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Chemin de recherche de module) et [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables d’environnement) dans la documentation Python principale.)

Visual Studio ignore la variable d’environnement de chemin de recherche, même si elle a été définie pour l’ensemble du système. En fait, il est ignoré, *car* il est défini pour l’ensemble du système et génère donc certaines questions qui ne peuvent pas être traitées automatiquement : les modules référencés sont-ils destinés à python 2,7 ou à python 3.6 + ? Vont-ils remplacer les modules de bibliothèque standard ? Le développeur est-il informé de ce comportement ou s’agit-il d’une tentative de piratage ?

Visual Studio fournit ainsi un moyen permettant de spécifier les chemins de recherche directement dans les environnements et les projets. Le code que vous exécutez ou déboguez dans Visual Studio reçoit les chemins de recherche dans la valeur de `PYTHONPATH` (et autres variables équivalentes). En ajoutant des chemins de recherche, Visual Studio inspecte les bibliothèques de ces emplacements et génère des bases de données IntelliSense pour celles-ci lorsque nécessaire (Visual Studio 2017 version 15.5 et versions antérieures ; la construction de la base de données peut prendre un certain temps en fonction du nombre de bibliothèques).

Pour ajouter un chemin de recherche, accédez à l’**Explorateur de solutions**, développez le nœud de votre projet, cliquez avec le bouton droit sur **Chemins de recherche**, puis sélectionnez **Ajouter le dossier au chemin de recherche** :

::: moniker range="vs-2017"
![Commande Ajouter le dossier au chemin de recherche dans l’Explorateur de solutions](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Commande Ajouter le dossier au chemin de recherche dans l’Explorateur de solutions](media/search-paths-command-2019.png)
::: moniker-end

Cette commande permet d’afficher un navigateur dans lequel vous sélectionnez le dossier à inclure.

Si votre variable d’environnement `PYTHONPATH` inclut déjà le ou les dossiers souhaités, utilisez **Ajouter PYTHONPATH au chemin de recherche** en tant que raccourci pratique.

Une fois les dossiers ajoutés aux chemins de recherche, Visual Studio les utilise pour n’importe quel environnement associé au projet. (Vous pouvez voir des erreurs si l’environnement est basé sur Python 3 et que vous essayez d’ajouter un chemin de recherche à des modules Python 2.7.)

Vous pouvez également ajouter les fichiers ayant une extension *.zip* ou *.egg* en tant que chemins de recherche, en sélectionnant la commande **Ajouter une archive zip au chemin de recherche**. À l’instar des dossiers, le contenu de ces fichiers est analysé et mis à disposition d’IntelliSense.

## <a name="see-also"></a>Voir aussi

- [Gérer les environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Utilisation requirements.txt pour les dépendances](managing-required-packages-with-requirements-txt.md)
- [Informations de référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)
