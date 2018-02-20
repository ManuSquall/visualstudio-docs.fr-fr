---
title: Gestion des environnements Python dans Visual Studio | Microsoft Docs
description: "Guide pratique pour utiliser la fenêtre Environnements Python dans Visual Studio afin de gérer des environnements globaux et virtuels, configurer des environnements personnalisés, installer des interpréteurs Python, installer des packages, définir des chemins de recherche et gérer des environnements pour des projets Visual Studio."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 40f901c65872fe593457883c36f0d60bf7e2fd8a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="python-environments"></a>Environnements Python

Un *environnement* Python est un contexte dans lequel vous exécutez le code Python. Un comprend un interpréteur, une bibliothèque (généralement la bibliothèque Python standard) et un ensemble de packages installés. Tous ces composants déterminent les constructions de langage et la syntaxe valides, les fonctionnalités du système d’exploitation auxquelles vous pouvez accéder et quels packages utiliser.

Dans Visual Studio, vous gérez tous vos environnements à l’aide de la [fenêtre des environnements Python](#managing-python-environments-in-visual-studio), comme décrit dans cet article. Pour un projet donné, vous sélectionnez un environnement à utiliser pour l’exécution du code, le débogage, la vérification de la syntaxe, l’affichage de l’importation et les saisies semi-automatiques de membres, et les autres tâches spécifiques à l’interpréteur et aux bibliothèques installées. Pour chaque environnement, Visual Studio gère aussi une base de données IntelliSense qui permet la saisie semi-automatique lors de la saisie du code.

Visual Studio fournit prend également en charge les environnements virtuels, les fichiers `requirements.txt` et les chemins de recherche.

**Remarque**: si vous utilisez Python dans Visual Studio, consultez les articles suivants pour obtenir les informations nécessaires :

- [Utilisation de Python dans Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installation de la prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md)

## <a name="global-and-virtual-environments"></a>Environnements globaux et virtuels

Il existe deux types d’environnement Python : global et virtuel.

**Environnements globaux** : chaque installation de Python (par exemple, Python 2.7, Python 3.6 et Anaconda 4.4.0, voir [Sélection et installation des interpréteurs Python](#selecting-and-installing-python-interpreters)) gère son propre environnement. Chaque environnement se compose de l’interpréteur Python spécifique, de sa bibliothèque standard et d’un ensemble de packages préinstallés. L’installation d’un package dans un environnement global le rend disponible à tous les projets qui utilisent cet environnement. Si l’environnement se trouve dans une zone protégée du système de fichiers (par exemple `c:\program files`), l’installation des packages nécessite des privilèges d’administrateur.

Les environnements globaux sont disponibles à tous les projets sur l’ordinateur. Dans Visual Studio, vous sélectionnez un environnement global par défaut, qui est utilisé pour tous les projets, sauf si vous choisissez spécifiquement un autre environnement pour un projet. Pour plus d’informations, consultez [Sélection d’un environnement pour un projet](#selecting-an-environment-for-a-project).

**Environnements virtuels** : puisque les packages installés dans un environnement global sont disponibles pour tous les projets qui utilisent cet environnement, des conflits peuvent survenir lorsque deux projets nécessitent des packages incompatibles ou différentes versions du même package. Les environnements virtuels évitent de tels conflits en utilisant l’interpréteur et la bibliothèque standard d’un environnement global, mais en conservant ses propres magasins de package dans des dossiers isolés.

Dans Visual Studio, vous pouvez créer un environnement virtuel pour un projet spécifique, qui est stocké dans un sous-dossier du projet (consultez [Création d’environnements virtuels](#creating-virtual-environments). Le fichier du projet identifie également l’environnement virtuel. Visual Studio enregistre aussi tous les packages que vous installez dans cet environnement virtuel dans le fichier `requirements.txt` du projet. Si vous partagez ensuite le projet et que d’autres développeurs l’ouvrent sur leurs ordinateurs, Visual Studio offre la possibilité de recréer l’environnement virtuel.

### <a name="selecting-and-installing-python-interpreters"></a>Sélection et installation des interpréteurs Python

Par défaut, l’installation de la charge de travail de développement Python dans Visual Studio 2017 installe également Python 3 (64 bits). Vous pouvez choisir d’installer les versions 32 bits et 64 bits de Python 2, Python 3, Anaconda 2 et Anaconda 3, comme décrit dans la rubrique [Installation](installing-python-support-in-visual-studio.md). Vous pouvez également installer manuellement l’un des interpréteurs répertoriés dans le tableau suivant.

Pour Visual Studio 2015 et versions antérieures, vous devez installer manuellement un des interpréteurs.

Visual Studio (toutes les versions) crée automatiquement un environnement pour chaque interpréteur Python installé en vérifiant le Registre (d’après le document [PEP 514 - Python registration in the Windows registry](https://www.python.org/dev/peps/pep-0514/) (PEP 514 - Inscription de Python dans le Registre Windows)). Si Visual Studio ne détecte pas un environnement installé, consultez la section [Création d’un environnement pour un interpréteur existant](#creating-an-environment-for-an-existing-interpreter).

| Interpréteur | Description |
| --- | --- |
| [CPython](https://www.python.org/) | Interpréteur « natif » et le plus couramment utilisé, disponible en versions 32 bits et 64 bits (version 32 bits recommandée). Il inclut les dernières fonctionnalités du langage, une compatibilité des packages Python maximale, la prise en charge complète du débogage et l’interopérabilité avec [IPython](http://ipython.org/). Consultez aussi : [Should I use Python 2 or Python 3 ?](http://wiki.python.org/moin/Python2orPython3). Notez que Visual Studio 2015 et antérieur ne prend pas en charge Python 3.6, et peut provoquer l’erreur « Python version 3.6 n’est pas pris en charge ». Utilisez à la place Python 3.5 ou antérieur. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implémentation .NET de Python, disponible en versions 32 bits et 64 bits, fournissant une interopérabilité C#/F#/Visual Basic, un accès aux API .NET, le débogage Python standard (mais pas le débogage en mode mixte C++) et le débogage mixte IronPython/C#. Toutefois, IronPython, ne prend pas en charge les environnements virtuels. |
| [Anaconda](https://www.continuum.io) | Une plateforme de science des données ouverte alimentée par Python, qui inclut la dernière version de CPython et la plupart des packages difficiles à installer. Nous vous la recommandons si vous ne pouvez pas décider autrement. |
| [PyPy](http://www.pypy.org/) | Une implémentation JIT de suivi hautes performances de Python qui convient aux programmes longs et aux situations dans lesquelles vous identifiez des problèmes de performances, mais que vous ne trouvez pas d’autres solutions. Fonctionne avec Visual Studio, mais avec une prise en charge limitée des fonctionnalités de débogage avancées. |
| [Jython](http://www.jython.org/) | Une implémentation de Python sur la Machine virtuelle Java (JVM). Similaire à IronPython, le code s’exécutant dans Jython peut interagir avec les bibliothèques et les classes Java, mais n’est peut-être pas en mesure d’utiliser de nombreuses bibliothèques destinées à CPython. Fonctionne avec Visual Studio, mais avec une prise en charge limitée des fonctionnalités de débogage avancées. |

Pour les développeurs qui souhaitent créer de nouvelles formes de détection pour les environnements Python, consultez [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Détection d’environnement PTVS ; github.com).

## <a name="managing-python-environments-in-visual-studio"></a>Gestion des environnements Python dans Visual Studio

Pour ouvrir la fenêtre Environnements Python, sélectionnez le menu de commande **Affichage > Autres fenêtres > Environnements Python**, ou cliquez avec le bouton droit sur le nœud **Environnements Python** d’un projet dans l’Explorateur de solutions, puis sélectionnez **Afficher tous les environnements Python** :

![Commande Afficher tous les environnements dans l’Explorateur de solutions](media/environments-view-all.png)

Dans les deux cas, la fenêtre Environnements Python s’affiche en tant qu’onglet frère de l’Explorateur de solutions :

![Fenêtre Environnements Python](media/environments-default-view.png)

L’exemple ci-dessus indique que Python 3.4 (CPython 32 bits) est installé avec les versions 32 bits et 64 bits d’IronPython 2.7. L’environnement par défaut en gras est Python 3.4, qui est utilisé pour tous les nouveaux projets. Si aucun environnement n’est répertorié, cela signifie que vous avez installé Python Tools pour Visual Studio dans Visual Studio 2015 ou version antérieure, mais que vous n’avez pas installé d’interpréteur Python (consultez la section [Sélection et installation des interpréteurs Python](#selecting-and-installing-python-interpreters) ci-dessus). La commande **+ Personnalisé...** vous permet de [créer un environnement pour un interpréteur existant](#creating-an-environment-for-an-existing-interpreter).

À droite de chaque environnement apparaît un contrôle qui ouvre une fenêtre interactive pour cet environnement. Un autre contrôle peut s’afficher, permettant d’actualiser la base de données IntelliSense pour cet environnement.

Sous la liste des environnements apparaît une liste déroulante pour les options **Vue d’ensemble**, **Packages** et **IntelliSense** décrites ultérieurement dans cette section. Si vous agrandissez suffisamment la fenêtre **Environnements Python**, ces options s’affichent sous forme d’onglets, sans doute plus pratiques à utiliser :

![Affichage développé de la fenêtre Environnements Python](media/environments-expanded-view.png)

> [!Note]
> Bien que Visual Studio respecte l’option system-site-packages, il ne fournit pas de moyen permettant de la modifier à partir de Visual Studio.

Pour une présentation vidéo de la gestion des environnements dans Visual Studio, regardez [Gestion des environnements Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (Microsoft Virtual Academy, 2 minutes 35 secondes).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Managing-Python-Environments-qrDmN4LWE_8305918567]

### <a name="creating-an-environment-for-an-existing-interpreter"></a>Création d’un environnement pour un interpréteur existant

Si Visual Studio ne trouve pas un interpréteur (par exemple, lorsqu’il est installé dans un emplacement non standard), vous pouvez créer un environnement comme suit :

1. Sélectionnez **+ Personnalisé...** dans la [fenêtre Environnements Python](#managing-python-environments-in-visual-studio), ce qui crée un environnement et ouvre [l’onglet **Configurer**](#configure-tab) décrit ci-dessous.

    ![Affichage par défaut pour un nouvel environnement personnalisé](media/environments-custom-1.png)

1. Entrez un nom pour l’environnement dans le champ **Description**.
1. Entrez ou recherchez le chemin d’accès de l’interpréteur dans le champ **Prefix path** (Chemin du préfixe).
1. Sélectionnez **Détecter automatiquement** pour que Visual Studio renseigne les champs restants ou renseignez-les manuellement.
1. Sélectionnez **Appliquer** pour enregistrer l’environnement.
1. Si vous devez supprimer l’environnement, sélectionnez la commande **Supprimer** sur l’onglet **Configurer**. Les environnements détectés automatiquement ne fournissent pas cette option. Pour plus d’informations, consultez la section suivante.

### <a name="moving-an-existing-interpreter"></a>Déplacement d’un interpréteur existant

Si vous déplacez un interpréteur existant vers un nouvel emplacement dans le système de fichiers, Visual Studio ne détecte pas automatiquement le changement, et vous devez manuellement mettre à jour son environnement :

- Si vous avez initialement créé un environnement pour cet interpréteur, modifiez cet environnement pour qu’il pointe vers le nouvel emplacement.

- Si l’environnement a été détecté automatiquement à l’origine, il a été installé sur l’ordinateur avec un programme d’installation distinct qui a créé les entrées de Registre examinées par Visual Studio. Dans ce cas, commencez par restaurer l’interpréteur Python à son emplacement d’origine. Ensuite, désinstallez-le à l’aide du programme d’installation ; cette opération entraîne l’effacement des entrées de Registre. Ensuite, réinstallez l’interpréteur à l’emplacement souhaité. Redémarrez Visual Studio, qui doit alors détecter automatiquement le nouvel emplacement. Grâce à ce processus, tous les autres effets secondaires du programme d’installation sont correctement appliqués.

### <a name="overview-tab"></a>Onglet Vue d’ensemble

Fournit des commandes et des informations de base pour l’environnement :

![Onglet Vue d’ensemble, Environnements Python](media/environments-overview-tab.png)

| Commande | Description |
| --- | --- |
| Make this environment the default for new projects (Définir cet environnement par défaut pour les nouveaux projets) | Définit l’environnement actif, ce qui risque d’interrompre brièvement le fonctionnement de Visual Studio lors du chargement de la base de données IntelliSense. Les environnements avec de nombreux packages peuvent être interrompus pendant plus longtemps. |
| Visit the distributor’s website (Visiter le site web du serveur de distribution) | Dans un navigateur, ouvre l’URL fournie par la distribution Python. Python 3.x, par exemple, accède à python.org. |
| Ouvrir une fenêtre interactive | Ouvre la [fenêtre (REPL) interactive](python-interactive-repl-in-visual-studio.md) pour cet environnement au sein de Visual Studio, en appliquant tous les [scripts de démarrage (voir ci-dessous)](#startup-scripts). |
| Explorer les scripts interactifs | Consultez [Scripts de démarrage](#startup-scripts). |
| Utiliser le mode interactif IPython | Quand cette option est définie, ouvre la fenêtre interactive avec IPython par défaut. Cela permet d’activer les tracés inline ainsi que la syntaxe IPython étendue comme `name?` pour afficher l’aide et `!command` pour les commandes de l’interpréteur de commandes. Cette option est recommandée lors de l’utilisation d’une distribution Anaconda, car elle nécessite des packages supplémentaires. Pour plus d’informations, consultez [Utilisation d’IPython dans la fenêtre interactive](interactive-repl-ipython.md). |
| Ouvrir dans PowerShell | Démarre l’interpréteur dans une fenêtre Commande PowerShell. |
| (Liens du dossier) | Vous fournissent un accès rapide au dossier d’installation de l’environnement, à l’interpréteur python.exe et à l’interpréteur pythonw.exe. Le premier s’ouvre dans l’Explorateur Windows et les deux autres ouvrent une fenêtre de console. |

#### <a name="startup-scripts"></a>Scripts de démarrage

Quand vous utilisez des fenêtres interactives dans votre flux de travail quotidien, vous développez probablement des fonctions d’assistance que vous utilisez régulièrement. Par exemple, vous pouvez créer une fonction qui ouvre une tramedonnées dans Excel, puis enregistrer ce code comme un script de démarrage afin qu’il soit toujours disponible dans la fenêtre interactive.

Les scripts de démarrage contiennent du code que la fenêtre interactive charge et exécute automatiquement, dont les importations, les définitions de fonctions et, littéralement, tout autre élément. Ces scripts sont référencés de deux manières :

1. Quand vous installez un environnement, Visual Studio crée un dossier `Documents\Visual Studio 2017\Python Scripts\<environment>` où &lt;environnement&gt' correspond au nom de l’environnement. Vous pouvez facilement accéder au dossier spécifique à l’environnement avec la commande **Explorer les scripts interactifs**. Quand vous démarrez la fenêtre interactive pour cet environnement, elle charge et exécute tous les fichiers `.py` qui s’y trouvent dans l’ordre alphabétique.

1. Le contrôle **Scripts** dans l’onglet **Outils > Options > Python Tools > Fenêtres interactives** (consultez [Options des fenêtres interactives](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) est destiné à spécifier un dossier supplémentaire pour les scripts de démarrage qui sont chargés et exécutés dans tous les environnements. Toutefois, cette fonctionnalité ne fonctionne pas actuellement.

### <a name="configure-tab"></a>Onglet Configurer

S’il est affiché, il contient des informations comme décrit dans le tableau ci-dessous. Si cet onglet n’est pas affiché, cela signifie que Visual Studio gère automatiquement toutes les informations.

![Onglet Configurer, Environnements Python](media/environments-configure-tab.png)

| Champ | Description |
| --- | --- |
| **Description** | Le nom à donner à l’environnement. |
| **Prefix path** (Chemin du préfixe) | L’emplacement du dossier de base de l’interpréteur. En indiquant cette valeur et en cliquant sur **Détecter automatiquement**, Visual Studio tente de renseigner les autres champs pour vous. |
| **Interpreter Path** (Chemin d’interpréteur) | Le chemin d’accès à l’interpréteur exécutable, généralement le chemin de préfixe suivi de `python.exe`. |
| **Windowed interpreter** (Interpréteur avec fenêtre) | Le chemin d’accès à l’exécutable autre qu’une console, souvent le chemin de préfixe suivi de `pythonw.exe`. |
| **Chemin d’accès à la bibliothèque** | Spécifie la racine de la bibliothèque standard, mais cette valeur peut être ignorée si Visual Studio est en mesure de demander un chemin d’accès plus précis à partir de l’interpréteur. |
| **Version du langage** | Sélectionnée à partir du menu déroulant. |
| **Architecture** | Normalement détectée et renseignée automatiquement, sinon, 32 bits ou 64 bits est spécifié. |
| **Path environment variable** (Variable d’environnement de chemin d’accès) | La variable d’environnement que l’interpréteur utilise pour rechercher les chemins de recherche. Visual Studio modifie la valeur de la variable lors du démarrage de Python pour qu’il contienne les chemins de recherche du projet. En général, cette propriété doit être définie sur `PYTHONPATH`, mais certains interpréteurs utilisent une autre valeur. |

### <a name="pip-tab"></a>Onglet pip

Gère les packages installés dans l’environnement, ce qui vous permet également de rechercher des packages et d’en installer de nouveaux (y compris toutes les dépendances). La recherche filtre vos packages actuellement installés et [PyPI](https://pypi.python.org). En outre, vous pouvez entrer directement une commande `pip install` dans la zone de recherche, y compris les indicateurs tels que `--user` ou `--no-deps`.

![Onglet pip, Environnements Python](media/environments-pip-tab.png)

L’installation d’un package crée des sous-dossiers au sein du dossier `Lib` de l’environnement sur le système de fichiers. Par exemple, si Python 3.6 est installé dans `c:\Python36`, les packages sont installés dans `c:\Python36\Lib` ; si Anaconda 3 est installé dans `c:\Program Files\Anaconda3`, les packages sont installés dans `c:\Program Files\Anaconda3\Lib`.

Dans le dernier cas, étant donné que l’environnement se trouve dans une zone protégée du système de fichiers, `c:\Program Files`, Visual Studio doit exécuter une `pip install` avec élévation de privilèges pour lui permettre de créer des sous-dossiers de package. Quand une élévation est requise, Visual Studio affiche l’invite « Des privilèges d’administrateur peuvent être nécessaires pour installer, mettre à jour ou supprimer des packages pour cet environnement. » :

![Invite d’élévation pour l’installation de packages](media/environments-pip-elevate.png)

**Élever les privilèges maintenant** accorde des privilèges d’administrateur à pip pour une seule opération, pouvant aussi faire l’objet d’une demande d’autorisations du système d’exploitation. En sélectionnant **Continuer sans privilège d’administrateur**, une tentative d’installation du package est effectuée, mais pip échoue en essayant de créer des dossiers avec une sortie telle que « Erreur. Impossible de créer 'C:\Program Files\Anaconda3\Lib\site-packages\png.py' : Autorisation refusée. ».

En sélectionnant **Toujours élever les privilèges pour l’installation et la suppression des packages**, vous empêchez la boîte de dialogue de s’afficher pour l’environnement en question. Pour que la boîte de dialogue s’affiche à nouveau, accédez à **Outils > Options > Python Tools > Général** et sélectionnez le bouton **Réinitialiser toutes les boîtes de dialogue masquées définitivement**.

Dans ce même onglet d’options, vous pouvez également sélectionner **Toujours exécuter pip comme administrateur** pour supprimer la boîte de dialogue pour tous les environnements. Consultez [Options - Onglet Général](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="intellisense-tab"></a>Onglet IntelliSense

Affiche l’état actuel de la base de données de saisie semi-automatique IntelliSense :

![Onglet IntelliSense, Environnements Python](media/environments-intellisense-tab.png)

La base de données contient des métadonnées pour toutes les bibliothèques de l’environnement, améliore la vitesse d’IntelliSense et réduit l’utilisation de la mémoire. Lorsque Visual Studio détecte un nouvel environnement (ou que vous en ajoutez un), il commence automatiquement à compiler la base de données en analysant les fichiers source de la bibliothèque. Ce processus peut prendre entre une minute et plus d’une heure, selon ce qui est installé. (Anaconda, par exemple, est fourni avec de nombreuses bibliothèques et la compilation de la base de données prend un certain temps). Une fois ce processus terminé, vous obtenez la base de données IntelliSense détaillée et n’avez pas à actualiser une nouvelle fois la base de données (avec le bouton **Refresh DB** (Actualiser base de données)) jusqu’à ce que vous installiez d’autres bibliothèques.

Les bibliothèques pour lesquelles les données n’ont pas été compilées sont marquées d’un **!** ; si la base de données d’un environnement n’est pas complète, un **!** apparaît également en regard de celle-ci dans la liste principale des environnements.

## <a name="selecting-an-environment-for-a-project"></a>Sélection d’un environnement pour un projet

Les environnements spécifiques au projet garantissent qu’un projet s’exécute toujours dans un environnement particulier, en ignorant l’environnement global par défaut. Par exemple, si l’environnement global par défaut est CPython, mais qu’un projet requiert IronPython et certaines bibliothèques qui ne sont pas installées dans l’environnement global, alors un environnement spécifique au projet est nécessaire.

Les environnements de projet sont répertoriés dans l’Explorateur de solutions sous le nœud Environnements Python. L’entrée en gras est actuellement active et Visual Studio l’utilise pour le débogage, l’importation et les saisies semi-automatiques de membres, la vérification de la syntaxe et les autres tâches qui nécessitent un environnement :

![Environnements de projet affichés dans l’Explorateur de solutions](media/environments-project.png)

Pour activer un environnement différent pour le projet, cliquez avec le bouton droit sur cet environnement et sélectionnez **Activate Environment** (Activer l’environnement).

N’importe quel environnement global peut être ajouté en tant qu’environnement de projet en cliquant avec le bouton droit sur **Environnements Python** et en sélectionnant **Add/Remove Python Environments...** (Ajouter/supprimer des environnements Python...). Dans la liste affichée, vous pouvez sélectionner ou désélectionner les environnements disponibles dans votre projet.

![Boîte de dialogue Ajouter/supprimer des environnements Python](media/environments-add-remove.png)

Dans l’Explorateur de solutions, vous pouvez également développer l’environnement pour afficher ses packages installés (ceux que vous pouvez importer et utiliser dans votre code lorsque l’environnement est actif) :

![Packages Python pour un environnement dans l’Explorateur de solutions](media/environments-installed-packages.png)

Pour installer de nouveaux packages, cliquez avec le bouton droit sur l’environnement, sélectionnez **Install Python Package...** (Installer un package Python...) et entrez le nom du package de votre choix. Les packages (et les dépendances) sont téléchargés à partir de [l’index de package Python (PyPI)](https://pypi.python.org/pypi), où vous pouvez également rechercher des packages disponibles. La barre d’état de Visual Studio et la fenêtre Sortie affichent des informations sur l’installation. Pour désinstaller un package, cliquez avec le bouton sur celui-ci et sélectionnez **Supprimer**.

> [!Note]
> La prise en charge de la gestion des packages de Python est actuellement en cours de développement par l’équipe de développement Python principale. Les entrées affichées peuvent ne pas toujours être exactes, et l’installation et la désinstallation ne sont peut-être pas fiables ou disponibles. Visual Studio utilise le gestionnaire de packages pip s’il est disponible, et le télécharge et l’installe si besoin. Visual Studio peut également utiliser le gestionnaire de packages easy_install. Les packages installés à l’aide de pip ou d’easy_install à partir de la ligne de commande sont également affichés.

> [!Tip]
> Il est courant que pip ne parvienne pas à installer un package quand celui-ci inclut le code source pour les composants natifs dans les fichiers `*.pyd`. Si la version requise de Visual Studio n’est pas installée, pip n’est pas en mesure de compiler ces composants. Le message d’erreur affiché dans ce cas est `error: Unable to find vcvarsall.bat`. `easy_install` est souvent capable de télécharger des binaires précompilés, et vous pouvez télécharger un compilateur approprié pour les versions antérieures de Python à partir de [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Pour plus d’informations, consultez le billet [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Comment gérer l’erreur « unable to find vcvarsallbat ») sur le blog de l’équipe Python Tools.

## <a name="creating-virtual-environments"></a>Création d’environnements virtuels

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’Explorateur de solutions, puis sélectionnez **Add Virtual Environment...** (Ajouter un environnement virtuel...), qui affiche ce qui suit :

    ![Création d’un environnement virtuel](media/environments-add-virtual-1.png)

1. Spécifiez un nom pour créer l’environnement virtuel dans votre chemin du projet, ou un chemin d’accès complet pour le créer ailleurs. (Pour assurer une compatibilité maximale avec d’autres outils, utilisez uniquement des chiffres et des lettres dans le nom.)

1. Sélectionnez un environnement global comme interpréteur de base et cliquez sur **Créer**. Si les packages `pip` et `virtualenv` ou `venv` ne sont pas disponibles, ils sont téléchargés et installés.

    Si le chemin fourni est un environnement virtuel existant, l’interpréteur de base est détecté et le bouton Créer est modifié en bouton **Ajouter** :

    ![Ajout d’un environnement virtuel existant](media/environments-add-virtual-2.png)

Un environnement virtuel existant peut également être ajouté en cliquant avec le bouton droit sur **Environnements Python** dans l’Explorateur de solutions et en sélectionnant **Add Existing Virtual Environment...** (Ajouter un environnement virtuel existant...). Visual Studio détecte automatiquement l’interpréteur de base à l’aide du fichier `orig-prefix.txt` dans le répertoire `lib` de l’environnement.

Après avoir été ajouté à votre projet, l’environnement virtuel apparaît dans la fenêtre **Environnements Python** et vous pouvez l’activer comme tout autre environnement, ainsi que gérer ses packages. Le fait de cliquer avec le bouton droit sur celui-ci et de sélectionner **Supprimer** supprime la référence à l’environnement ou supprime l’environnement et tous ses fichiers sur le disque (mais pas l’interpréteur de base).

Notez que les environnements virtuels présentent l’inconvénient de contenir des chemins d’accès aux fichiers codés en dur et sont donc plus difficiles à partager ou à transférer vers d’autres ordinateurs de développement. Heureusement, vous pouvez utiliser le fichier `requirements.txt`, comme décrit dans la section suivante, pour autoriser les destinataires de votre projet à restaurer facilement l’environnement.

## <a name="managing-required-packages-requirementstxt"></a>Gestion des packages requis (requirements.txt)

Si vous partagez un projet avec d’autres utilisateurs, à l’aide d’un système de génération, ou si vous envisagez de [le publier sur Microsoft Azure](python-azure-cloud-service-project-template.md), vous devez spécifier les packages externes que le projet requiert. L’approche recommandée consiste à utiliser un [fichier requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) qui contient une liste de commandes pour pip qui installe les versions requises des packages dépendants.

Techniquement, tout filename peut être utilisé pour suivre les spécifications (à l’aide de `-r <full path to file>` lors de l’installation d’un package), mais Visual Studio fournit une prise en charge spécifique pour `requirements.txt` :

- Si vous avez chargé un projet contenant `requirements.txt` et si vous souhaitez installer tous les packages répertoriés dans ce fichier, développez le nœud **Environnements Python** dans **l’Explorateur de solutions**, puis cliquez avec le bouton droit sur un nœud Environnement et sélectionnez **Install from requirements.txt** (Installer à partir de requirements.txt) :

    ![Installer à partir de requirements.txt](media/environments-requirements-txt-install.png)

- Si vous avez déjà installé tous les packages nécessaires dans un projet, cliquez avec le bouton droit sur un environnement dans l’Explorateur de solutions et sélectionnez **Generate requirements.txt** (Générer requirements.txt) pour créer le fichier requis. Si le fichier existe déjà, une invite s’affiche sur le mode de mise à jour :

    ![Options de mise à jour pour requirements.txt](media/environments-requirements-txt-replace.png)

  - **Replace entire file** (Remplacer l’intégralité du fichier) supprime tous les éléments, commentaires et options qui existent.
  - **Actualiser les entrées existantes** détecte les spécifications du package et met à jour les spécificateurs de version pour qu’ils correspondent à la version actuellement installée.
  - **Update and add entries** (Mettre à jour et ajouter des entrées) actualise les spécifications trouvées et ajoute tous les autres packages à la fin du fichier.

Les fichiers `requirements.txt` étant destinés à figer les spécifications de votre projet, tous les packages installés sont écrits avec les versions précises. L’utilisation de versions précises vous assure une reproduction simple de votre environnement sur un autre ordinateur. Les packages sont inclus même s’ils ont été installés avec une plage de versions, en tant que dépendance d’un autre package, ou avec un programme d’installation autre que pip.

Si un fichier `requirements.txt` existe quand vous ajoutez un nouvel environnement virtuel, la boîte de dialogue **Ajouter un environnement virtuel** affiche une option pour installer les packages automatiquement, ce qui vous permet de recréer facilement un environnement sur un autre ordinateur :

![Créer un environnement virtuel avec requirements.txt](media/environments-requirements-txt.png)

Si un package ne peut pas être installé par pip et s’il apparaît dans un fichier `requirements.txt`, l’ensemble de l’installation échoue. Dans ce cas, modifiez manuellement le fichier à exclure de ce package ou utilisez [les options de pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) pour faire référence à une version installable du package. Par exemple, vous préférez peut-être utiliser [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) pour compiler une dépendance et ajouter l’option `--find-links <path>` à votre `requirements.txt` :

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>Chemins de recherche

Dans le cadre de l’utilisation typique de Python, la variable d’environnement `PYTHONPATH` (ou `IRONPYTHONPATH`, etc.) fournit le chemin de recherche par défaut pour les fichiers de module. Autrement dit, lorsque vous utilisez une instruction `from <name> import...` ou `import <name>`, Python recherche un nom correspondant dans les emplacements suivants :

1. Modules intégrés de Python.
1. Dossier contenant le code Python que vous exécutez.
1. « Chemin de recherche du module », comme défini par la variable d’environnement applicable. (Consultez les sections [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Chemin de recherche de module) et [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables d’environnement) dans la documentation Python principale.)

Visual Studio ignore la variable d’environnement de chemin de recherche, même si elle a été définie pour l’ensemble du système. En fait, elle est ignorée *car* elle est définie pour l’ensemble du système et génère donc certaines questions qui ne peuvent pas être traitées automatiquement : Les modules auxquels il est fait référence sont-ils destinés à Python 2.7 ou Python 3.3 ? Vont-ils remplacer les modules de bibliothèque standard ? Le développeur est-il informé de ce comportement ou s’agit-il d’une tentative de piratage ?

Visual Studio fournit ainsi un moyen permettant de spécifier les chemins de recherche directement dans les environnements et les projets. Le code que vous exécutez ou déboguez dans Visual Studio reçoit les chemins de recherche dans la valeur de `PYTHONPATH` (et autres variables équivalentes). En ajoutant des chemins de recherche, Visual Studio inspecte les bibliothèques de ces emplacements et génère des bases de données IntelliSense pour celles-ci (la construction de la base de données peut prendre un certain temps en fonction du nombre de bibliothèques).

Pour ajouter un chemin de recherche, cliquez avec le bouton droit sur l’élément **Chemins de recherche** dans l’Explorateur de solutions, sélectionnez **Add Folder to Search Path...** (Ajouter un dossier au chemin de recherche...), puis sélectionnez le dossier à inclure. Ce chemin d’accès est utilisé pour n’importe quel environnement associé au projet. (Vous pouvez voir des erreurs si l’environnement est basé sur Python 3 et que vous essayez d’ajouter un chemin de recherche à des modules Python 2.7.)

Les fichiers avec une extension `.zip` ou `.egg` peuvent également être ajoutés en tant que chemins de recherche en sélectionnant **Add Zip Archive to Search Path...** (Ajouter une archive zip au chemin de recherche...). À l’instar des dossiers, le contenu de ces fichiers est analysé et mis à disposition d’IntelliSense.

Si vous utilisez régulièrement les mêmes chemins de recherche et si le contenu ne change pas souvent, il peut être plus efficace de l’installer dans votre dossier site-packages. Analysé et stocké ensuite dans la base de données IntelliSense, le chemin de recherche est toujours associé à l’environnement souhaité et aucun chemin de recherche ne doit être ajouté à chaque projet.
