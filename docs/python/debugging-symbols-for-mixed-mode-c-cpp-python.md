---
title: Symboles de débogage en mode mixte Python/C++
description: Guide pratique sur la capacité de Visual Studio à charger des symboles pour effectuer le débogage en mode mixte C++ et Python.
ms.date: 11/12/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 472cd590627a84ea0a11b9de8b533bba3a88a253
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355433"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Installer les symboles de débogage pour les interpréteurs Python

Pour offrir une expérience de débogage complète, le [débogueur Python en mode mixte](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) dans Visual Studio nécessite des symboles de débogage pour l’interpréteur Python utilisé afin d’analyser de nombreuses structures de données internes. Par exemple, pour *python27.dll*, le fichier de symboles correspondant est *python27.pdb* ; pour *python36.dll*, il s’agit du fichier de symboles *python36.pdb*. Chaque version de l’interpréteur fournit également des fichiers de symboles pour différents modules.

Dans Visual Studio 2017 et ultérieur, les interpréteurs Python 3 et Anaconda 3 installent automatiquement leurs symboles respectifs, qui sont ensuite automatiquement détectés par Visual Studio. Dans Visual Studio 2015 et versions antérieures, ou si vous utilisez des interpréteurs tiers, vous devez télécharger les symboles séparément, puis indiquer leur emplacement à Visual Studio dans la boîte de dialogue **Outils** > **Options** sous l’onglet **Débogage** > **Symboles**. Ces étapes sont détaillées dans les sections suivantes.

Visual Studio peut vous inviter à fournir les symboles dont il a besoin, en général au moment du démarrage d’une session de débogage en mode mixte. Dans ce cas, il affiche une boîte de dialogue avec deux options possibles :

- L’option **Ouvrir la boîte de dialogue des paramètres de symboles** ouvre la boîte de dialogue **Options** sous l’onglet **Débogage** > **Symboles**.
- L’option **Télécharger des symboles pour mon interpréteur** ouvre la présente page de documentation. Dans ce cas, sélectionnez **Outils** > **Options** et accédez à l’onglet **Débogage** > **Symboles** pour continuer.

    ![Invite pour fournir les symboles de débogage en mode mixte](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Télécharger des symboles

- Python 3.5 et versions ultérieures : obtenez les symboles de débogage par le biais du programme d’installation de Python. Sélectionnez **Installation personnalisée**, sélectionnez **Suivant** pour accéder à **Options avancées**, puis cochez les cases **Download debugging symbols** (Télécharger les symboles de débogage) et **Download debug binaries** (Télécharger les binaires de débogage) :

    ![Programme d’installation de Python 3.x incluant les symboles de débogage](media/mixed-mode-debugging-symbols-installer35.png)

    Les fichiers de symboles (*.pdb*) se trouvent dans le dossier d’installation racine (les fichiers de symboles de chaque module sont aussi dans le dossier *DLLs*). Visual Studio peut ainsi les trouver automatiquement, sans autre étape nécessaire.

- Python 3.4.x et versions antérieures : les symboles sont fournis dans des fichiers *.zip* que vous téléchargez à partir des [distributions officielles](#official-distributions) ou [d’Enthought Canopy](#enthought-canopy). Après avoir téléchargé les fichiers, extrayez-les dans un dossier local pour continuer, par exemple un dossier *Symbols* dans le dossier Python.

    > [!Important]
    > Les symboles ne sont pas les mêmes pour les différentes versions mineures de Python et entre les versions 32 bits et 64 bits. Vous devez donc télécharger les versions correspondantes exactes. Pour déterminer quel interpréteur est utilisé, développez le *nœud* **Environnements Python** sous votre projet dans **l’Explorateur de solutions** et notez le nom de l’environnement. Affichez ensuite la *fenêtre* **Environnements Python** et notez l’emplacement d’installation. Ouvrez une fenêtre Commande à cet emplacement, puis lancez *python.exe*, qui indique la version exacte et s’il s’agit d’une version 32 bits ou 64 bits.

- Pour toute autre distribution Python tierce (comme ActiveState Python) : contactez les auteurs de cette distribution pour leur demander de vous fournir les symboles. WinPython incorpore l’interpréteur Python standard sans modifications. Par conséquent, utilisez les symboles de la distribution officielle pour le numéro de version correspondant.

## <a name="point-visual-studio-to-the-symbols"></a>Indiquer les symboles à Visual Studio

Si vous avez téléchargé les symboles séparément, suivez les étapes ci-dessous pour indiquer à Visual Studio où les trouver. Si vous avez installé les symboles par le biais du programme d’installation de Python 3.5 ou version ultérieure, Visual Studio les trouve alors automatiquement.

1. Sélectionnez le menu **Outils** > **Options**, puis accédez à **Débogage** > **Symboles**.

1. Sélectionnez le bouton **Ajouter** dans la barre d’outils (illustrée ci-dessous), entrez le dossier où vous avez développé les symboles téléchargés (à savoir le dossier contenant *python.pdb*, par exemple le dossier *c:\python34\Symbols* illustré ci-dessous), puis sélectionnez **OK**.

    ![Options des symboles de débogueur en mode mixte](media/mixed-mode-debugging-symbols.png)

1. Pendant une session de débogage, Visual Studio peut également vous demander d’indiquer l’emplacement d’un fichier source pour l’interpréteur Python. Si vous avez téléchargé des fichiers sources (à partir de [python.org/downloads/](https://www.python.org/downloads/), par exemple), vous pouvez également y faire référence.

> [!Note]
> Les fonctionnalités de mise en cache des symboles proposées dans la boîte de dialogue permettent de créer un cache local des symboles obtenus à partir d’une source en ligne. Ces fonctionnalités ne sont pas nécessaires avec les symboles de l’interpréteur Python, car ceux-ci sont déjà présents localement. Dans tous les cas, consultez [Spécifier les symboles et les fichiers sources dans le débogueur Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) pour plus d’informations.

## <a name="official-distributions"></a>Distributions officielles

| Version Python | Téléchargements |
| --- | --- |
| 3.5 et ultérieur | Installez les symboles à l’aide du programme d’installation de Python. |
| 3.4.4 | [32 bits](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bits](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bits](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bits](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bits](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bits](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bits](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bits](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bits](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bits](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bits](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32 bits](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32 bits](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32 bits](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32 bits](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32 bits](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bits](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bits](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bits](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bits](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bits](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bits](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bits](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bits](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bits](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bits](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy fournit des symboles pour ses binaires à partir de la version 1.2. Ces symboles sont automatiquement installés en même temps que la distribution, mais vous devez quand même ajouter manuellement le nom du dossier dans lequel ils sont stockés au chemin des symboles, comme décrit précédemment. Dans le cas d’une installation par utilisateur classique de Canopy, les symboles se trouvent dans *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* pour la version 64 bits et dans *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* pour la version 32 bits.

Enthought Canopy 1.1 et les versions antérieures, de même qu’Enthought Python Distribution (EPD), ne fournissent pas de symboles d’interpréteur, et ne sont donc pas compatibles avec le débogage en mode mixte.
