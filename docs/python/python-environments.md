---
title: Environnements Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8876f8c1-4770-44dc-97d8-bf0035ae8196
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: f73c0c7c40d1edd18cccb1ba69424c4e34472c33
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---

# <a name="python-environments"></a>Environnements Python

Python dans Visual Studio simplifie la gestion de plusieurs environnements Python et le basculement entre ceux-ci pour différents projets. 

Remarque : Si vous êtes un nouvel utilisateur de Python dans Visual Studio, consultez tout d’abord les rubriques suivantes, car cette discussion repose sur ces dernières :

- [Utilisation de Python dans Visual Studio](python-in-visual-studio.md)
- [Installation de la prise en charge de Python dans Visual Studio](installation.md)

Un *environnement* Python, dans lequel vous exécutez toujours le code Python, comprend un interpréteur, une bibliothèque (généralement la bibliothèque Python standard) et un ensemble de packages installés. Tous ces composants déterminent quelles sont les constructions de langage et la syntaxe valides, les fonctionnalités du système d’exploitation auxquelles vous pouvez accéder et quels packages utiliser.

Dans Visual Studio, un environnement inclut également une base de données IntelliSense pour les bibliothèques d’un environnement, de sorte que la saisie d’une instruction comme `import` dans l’éditeur Visual Studio affiche automatiquement une liste des bibliothèques disponibles, ainsi que les modules dans ces bibliothèques.

Souvent, les développeurs utilisent uniquement un environnement Python global. D’autres développeurs, toutefois, doivent gérer plusieurs environnements globaux, des environnements spécifiques au projet et des environnements virtuels, comme expliqué dans cette rubrique :

- [Sélection et installation des interpréteurs Python](#selecting-and-installing-python-interpreters)
- [Gestion des environnements Python dans Visual Studio](#managing-python-environments-in-visual-studio)
- [Environnements globaux](#global-environments)
- [Environnements spécifiques au projet](#project-specific-environments)
- [Environnements virtuels](#virtual-environments)
- [Gestion des packages requis](#managing-required-packages)
- [Chemins de recherche](#search-paths)

Pour une présentation vidéo, visionnez [Deep Dive: Python Interpreters](https://youtu.be/KY1GEOo3qy0) (Expérience approfondie : Interpréteurs Python ; youtube.com, 13 min27 s).

> [!VIDEO https://www.youtube.com/embed/KY1GEOo3qy0]

## <a name="selecting-and-installing-python-interpreters"></a>Sélection et installation des interpréteurs Python

À l’exception de Visual Studio 2017, la prise en charge de Python ne comprend pas d’interpréteur Python. Vous devrez donc installer l’un des interpréteurs ci-dessous pour exécuter votre code. En général, Visual Studio détecte automatiquement les interpréteurs nouvellement installés et configure un environnement qui leur est destiné. Si ce n’est pas le cas, consultez la section [Création d’un environnement pour un interpréteur existant](#creating-an-environment-for-an-existing-interpreter) ci-dessous.

| Interpréteur | Description | 
| --- | --- | 
| [CPython](https://www.python.org/) | Interpréteur « natif » et le plus couramment utilisé, disponible en versions 32 bits et 64 bits (version 32 bits recommandée). Il inclut les dernières fonctionnalités du langage, une compatibilité des packages Python maximale, la prise en charge complète du débogage et l’interopérabilité avec [IPython](http://ipython.org/). Consultez aussi : [Should I use Python 2 or Python 3 for my development activity?](http://wiki.python.org/moin/Python2orPython3) (Dois-je utiliser Python 2 ou Python 3 pour mon activité de développement ?). |
| [IronPython](https://github.com/IronLanguages/main) | Implémentation .NET de Python, disponible en versions 32 bits et 64 bits, fournissant une interopérabilité C#/F#/Visual Basic, un accès aux API .NET, le débogage Python standard (mais pas le débogage en mode mixte C++) et le débogage mixte IronPython/C#. Toutefois, IronPython, ne prend pas en charge les environnements virtuels. | 
| [Anaconda](https://www.continuum.io) | Une plateforme de science des données ouverte alimentée par Python, qui inclut la dernière version de CPython et la plupart des packages difficiles à installer. Nous vous la recommandons si vous ne pouvez pas décider autrement. |
| [PyPy](http://www.pypy.org/) | Une implémentation JIT de suivi hautes performances de Python qui convient aux programmes longs et aux situations dans lesquelles vous identifiez des problèmes de performances, mais que vous ne trouvez pas d’autres solutions. Fonctionne avec Visual Studio, mais avec une prise en charge limitée des fonctionnalités de débogage avancées. |
| [Jython](http://www.jython.org/) | Une implémentation de Python sur la Machine virtuelle Java (JVM). Similaire à IronPython, le code s’exécutant dans Jython peut interagir avec les bibliothèques et les classes Java, mais n’est peut-être pas en mesure d’utiliser de nombreuses bibliothèques destinées à CPython. Fonctionne avec Visual Studio, mais avec une prise en charge limitée des fonctionnalités de débogage avancées. |

Pour les développeurs qui souhaitent créer de nouvelles formes de détection pour les environnements Python, consultez [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Détection d’environnement PTVS ; github.com).

## <a name="managing-python-environments-in-visual-studio"></a>Gestion des environnements Python dans Visual Studio

Vous pouvez ouvrir la fenêtre Environnements Python de l’une des façons suivantes :

1. Sélectionnez la commande de menu **Affichage > Other Windows (Autres fenêtres) > Environnements Python**.
1. Cliquez avec le bouton droit sur **Environnements Python** pour un projet dans l’Explorateur de solutions et sélectionnez **View All Python Environments** (Afficher tous les environnements Python) :

    ![Commande Afficher tous les environnements dans l’Explorateur de solutions](media/environments-view-all.png)
    
Dans les deux cas, la fenêtre Environnements Python s’affiche en tant qu’onglet frère de l’Explorateur de solutions :

![Fenêtre Environnements Python](media/environments-default-view.png)

L’exemple ci-dessus indique que Python 3.4 (CPython 32 bits) est installé avec les versions 32 bits et 64 bits d’IronPython 2.7. Dans ce cas, l’environnement par défaut en gras est Python 3.4, qui est utilisé pour tous les nouveaux projets. Si aucun environnement n’est répertorié, cela signifie que vous avez installé Python Tools pour Visual Studio dans Visual Studio 2015 ou version antérieure, mais que vous n’avez pas installé d’interpréteur Python (consultez la section [Sélection et installation des interpréteurs Python](#selecting-and-installing-python-interpreters) ci-dessus). 

> [!Tip]
> Quand la fenêtre **Environnements Python** est étroite, comme illustré ci-dessus, les environnements apparaissent en haut et les différents onglets en bas. Si vous développez la fenêtre suffisamment, toutefois, vous avez un affichage plus large que vous pouvez trouver plus pratique à utiliser.
>
> ![Affichage développé de la fenêtre Environnements Python](media/environments-expanded-view.png)

> [!Note]
> Bien que Visual Studio respecte l’option system-site-packages, il ne fournit pas de moyen permettant de la modifier à partir de Visual Studio.

### <a name="creating-an-environment-for-an-existing-interpreter"></a>Création d’un environnement pour un interpréteur existant

Visual Studio localise normalement un interpréteur Python installé en consultant le Registre, mais peut ne pas le trouver si l’interpréteur est installé de manière non standard. Dans ce genre de situation, vous pouvez orienter Visual Studio directement vers l’interpréteur comme suit :

1. Sélectionnez **+ Personnalisé...** dans la fenêtre Environnements Python, ce qui crée un environnement et ouvre [ l’onglet **Configurer**](#configure-tab) décrit ci-dessous.

    ![Affichage par défaut pour un nouvel environnement personnalisé](media/environments-custom-1.png)

1. Entrez un nom pour l’environnement dans le champ **Description**.
1. Entrez ou recherchez le chemin d’accès de l’interpréteur dans le champ **Prefix path** (Chemin du préfixe).
1. Sélectionnez **Détecter automatiquement** pour que Visual Studio renseigne les champs restants ou renseignez-les manuellement.
1. Sélectionnez **Appliquer** pour enregistrer l’environnement.
1. Si vous devez supprimer l’environnement, sélectionnez la commande **Supprimer** sur l’onglet **Configurer**.

### <a name="overview-tab"></a>Onglet Vue d’ensemble

Fournit des commandes et des informations de base pour l’environnement :

![Onglet Vue d’ensemble, Environnements Python](media/environments-overview-tab.png)

| Commande | Description |
| --- | --- |
| Make this environment the default for new projects (Définir cet environnement par défaut pour les nouveaux projets) | Définit l’environnement actif, ce qui risque d’interrompre brièvement le fonctionnement de Visual Studio lors du chargement de la base de données IntelliSense. Les environnements avec de nombreux packages peuvent être interrompus pendant plus longtemps. |
| Visit the distributor’s website (Visiter le site web du serveur de distribution) | Dans un navigateur, ouvre l’URL fournie par la distribution Python. Python 3.x, par exemple, accède à python.org. |
| Ouvrir une fenêtre interactive | Ouvre la [fenêtre (REPL) interactive](interactive-repl.md) pour cet environnement au sein de Visual Studio, en appliquant tous les [scripts de démarrage (voir ci-dessous)](#startup-scripts). |
| Utiliser le mode interactif IPython | Quand cette option est définie, ouvre la fenêtre interactive avec IPython par défaut. Cela permet d’activer les tracés inline ainsi que la syntaxe IPython étendue comme `name?` pour afficher l’aide et `!command` pour les commandes de l’interpréteur de commandes. Cette option est recommandée lors de l’utilisation d’une distribution Anaconda, car elle nécessite des packages supplémentaires. Pour plus d’informations, consultez [Utilisation d’IPython dans la fenêtre interactive](interactive-repl-ipython.md). |
| Ouvrir dans PowerShell | Démarre l’interpréteur dans une fenêtre Commande PowerShell. |
| (Liens du dossier) | Vous fournissent un accès rapide au dossier d’installation de l’environnement, à l’interpréteur python.exe et à l’interpréteur pythonw.exe. Le premier s’ouvre dans l’Explorateur Windows et les deux autres ouvrent une fenêtre de console. |

#### <a name="startup-scripts"></a>Scripts de démarrage

Quand vous utilisez des fenêtres interactives dans votre flux de travail quotidien, vous développez probablement des fonctions d’assistance que vous utilisez régulièrement. Par exemple, vous pouvez créer une fonction qui ouvre une tramedonnées dans Excel, puis enregistrer ce code comme un script de démarrage afin qu’il soit toujours disponible dans la fenêtre interactive.

Les scripts de démarrage contiennent du code que la fenêtre interactive charge et exécute automatiquement, dont les importations, les définitions de fonctions et, littéralement, tout autre élément. Ces scripts sont référencés de deux manières :

1. Quand vous installez un environnement, Visual Studio crée un dossier `Documents\Visual Studio 2017\Python Scripts\<environment>` où &lt;environnement&gt' correspond au nom de l’environnement. Vous pouvez facilement accéder au dossier spécifique à l’environnement avec la commande **Explorer les scripts interactifs**. Quand vous démarrez la fenêtre interactive pour cet environnement, elle charge et exécute tous les fichiers `.py` qui s’y trouvent dans l’ordre alphabétique.

1. Le contrôle **Scripts** dans l’onglet **Outils > Options > Python Tools > Fenêtres interactives** (consultez [Options des fenêtres interactives](options.md#interactive-windows-options)) est destiné à spécifier un dossier supplémentaire pour les scripts de démarrage qui sont chargés et exécutés dans tous les environnements. Toutefois, cette fonctionnalité ne fonctionne pas actuellement.


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

Dans ce même onglet d’options, vous pouvez également sélectionner **Toujours exécuter pip comme administrateur** pour supprimer la boîte de dialogue pour tous les environnements. Consultez [Options - Onglet Général](options.md#general-options).


### <a name="intellisense-tab"></a>Onglet IntelliSense

Affiche l’état actuel de la base de données de saisie semi-automatique IntelliSense :

![Onglet IntelliSense, Environnements Python](media/environments-intellisense-tab.png)

La base de données contient des métadonnées pour toutes les bibliothèques de l’environnement, améliore la vitesse d’IntelliSense et réduit l’utilisation de la mémoire. Lorsque Visual Studio détecte un nouvel environnement (ou que vous en ajoutez un), il commence automatiquement à compiler la base de données en analysant les fichiers source de la bibliothèque. Ce processus peut prendre entre une minute et plus d’une heure, selon ce qui est installé. (Anaconda, par exemple, est fourni avec de nombreuses bibliothèques et la compilation de la base de données prend un certain temps). Une fois ce processus terminé, vous obtenez la base de données IntelliSense détaillée et n’avez pas à actualiser une nouvelle fois la base de données (avec le bouton **Refresh DB** (Actualiser base de données)) jusqu’à ce que vous installiez d’autres bibliothèques.

Les bibliothèques pour lesquelles les données n’ont pas été compilées sont marquées d’un **!** ; si la base de données d’un environnement n’est pas complète, un **!** apparaît également en regard de celle-ci dans la liste principale des environnements.

## <a name="global-environments"></a>Environnements globaux

Les environnements globaux (ou du système) sont disponibles pour tous vos projets sur un ordinateur. Visual Studio détecte généralement les environnements globaux de façon automatique, et ceux-ci peuvent être affichés dans la fenêtre Environnements Python. Si ce n’est pas le cas, vous pouvez ajouter un environnement manuellement, comme décrit précédemment dans la section [Gestion des environnements Python dans Visual Studio](#managing-python-environments-in-visual-studio).

Visual Studio utilise l’environnement par défaut pour tous les nouveaux projets, afin de mener les opérations d’exécution, de débogage, de vérification de la syntaxe, d’affichage des saisies semi-automatiques de membres et des importations et d’autres tâches qui requièrent un environnement. Une modification de l’environnement par défaut affecte tous les projets pour lesquels un [environnement spécifique au projet](#project-specific-environments) n’a pas été ajouté, comme décrit ci-après.

## <a name="project-specific-environments"></a>Environnements spécifiques au projet

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


## <a name="virtual-environments"></a>Environnements virtuels

Puisque les packages installés dans un environnement global sont disponibles pour tous les projets qui les utilisent, des conflits peuvent survenir lorsque deux projets nécessitent des packages incompatibles ou différentes versions du même package. Pour éviter ce type de conflit, Visual Studio offre la possibilité de créer des *environnements virtuels*, qui sont généralement spécifiques à un projet.

Comme tout autre environnement Python, un environnement virtuel comprend un interpréteur Python, une bibliothèque et un ensemble de packages. Dans ce cas, cependant, l’environnement virtuel utilise l’interpréteur et la bibliothèque de l’un de vos environnements globaux (sous réserve qu’il prenne en charge les environnements virtuels), mais ses packages sont séparés et isolés de l’environnement global et de tous les autres environnements virtuels. Là encore, cette isolation évite les conflits et réduit l’encombrement de l’environnement virtuel à la taille approximative de ses packages. 

Pour créer un environnement virtuel :

1. Cliquez avec le bouton droit sur **Environnements Python** dans l’Explorateur de solutions, puis sélectionnez **Add Virtual Environment...** (Ajouter un environnement virtuel...), qui affiche ce qui suit :

    ![Création d’un environnement virtuel](media/environments-add-virtual-1.png)

1. Spécifiez un nom pour créer l’environnement virtuel dans votre chemin du projet, ou un chemin d’accès complet pour le créer ailleurs. (Pour assurer une compatibilité maximale avec d’autres outils, utilisez uniquement des chiffres et des lettres dans le nom.)

1. Sélectionnez un environnement global comme interpréteur de base et cliquez sur **Créer**. Si les packages `pip` et `virtualenv` ou `venv` ne sont pas disponibles, ils sont téléchargés et installés.

    Si le chemin fourni est un environnement virtuel existant, l’interpréteur de base est détecté et le bouton Créer est modifié en bouton **Ajouter** :

    ![Ajout d’un environnement virtuel existant](media/environments-add-virtual-2.png)

Un environnement virtuel existant peut également être ajouté en cliquant avec le bouton droit sur **Environnements Python** dans l’Explorateur de solutions et en sélectionnant **Add Existing Virtual Environment...** (Ajouter un environnement virtuel existant...). Visual Studio détecte automatiquement l’interpréteur de base à l’aide du fichier `orig-prefix.txt` dans le répertoire `lib` de l’environnement.

Après avoir été ajouté à votre projet, l’environnement virtuel apparaît dans la fenêtre **Environnements Python** et vous pouvez l’activer comme tout autre environnement, ainsi que gérer ses packages. Le fait de cliquer avec le bouton droit sur celui-ci et de sélectionner **Supprimer** supprime la référence à l’environnement ou supprime l’environnement et tous ses fichiers sur le disque (mais pas l’interpréteur de base).

Notez que les environnements virtuels présentent l’inconvénient de contenir des chemins d’accès aux fichiers codés en dur et sont donc plus difficiles à partager ou à transférer vers d’autres ordinateurs de développement. Heureusement, vous pouvez utiliser le fichier `requirements.txt` comme décrit dans la section suivante.

## <a name="managing-required-packages"></a>Gestion des packages requis

Si vous partagez un projet avec d’autres utilisateurs, à l’aide d’un système de génération, ou si vous envisagez de [le publier sur Microsoft Azure](template-azure-cloud-service.md), vous devez spécifier les packages externes qu’il requiert. L’approche recommandée consiste à utiliser un [fichier requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) qui contient une liste de commandes pour pip qui installe les versions requises des packages dépendants.

Techniquement, tout filename peut être utilisé pour suivre les spécifications (à l’aide de `-r <full path to file>` lors de l’installation d’un package), mais Visual Studio fournit une prise en charge spécifique pour `requirements.txt` :

- Si vous avez chargé un projet contenant `requirements.txt` et si vous souhaitez installer tous les packages répertoriés dans ce fichier, cliquez avec le bouton droit sur le projet et sélectionnez **Install from requirements.txt** (Installer à partir de requirements.txt) :

    ![Installer à partir de requirements.txt](media/environments-requirements-txt-install.png)

- Lorsque vous disposez de tous les packages nécessaires installés dans un projet, vous pouvez cliquer avec le bouton droit sur le projet dans l’Explorateur de solutions et sélectionner **Generate requirements.txt** (Générer requirements.txt) pour créer le fichier nécessaire. Si le fichier existe déjà, une invite s’affiche sur le mode de mise à jour :

    ![Options de mise à jour pour requirements.txt](media/environments-requirements-txt-replace.png)

    - **Replace entire file** (Remplacer l’intégralité du fichier) supprime tous les éléments, commentaires et options qui existent.
    - **Actualiser les entrées existantes** détecte les spécifications du package et met à jour les spécificateurs de version pour qu’ils correspondent à la version actuellement installée.
    - **Update and add entries** (Mettre à jour et ajouter des entrées) actualise les spécifications trouvées et ajoute tous les autres packages à la fin du fichier.

Les fichiers `requirements.txt` étant destinés à figer les spécifications de votre projet, tous les packages installés sont écrits avec les versions précises. L’utilisation de versions précises vous assure une reproduction simple de votre environnement sur un autre ordinateur. Les packages sont inclus même s’ils ont été installés avec une plage de versions, en tant que dépendance d’un autre package, ou avec un programme d’installation autre que pip.

Si un fichier ` requirements.txt` existe quand vous ajoutez un nouvel environnement virtuel, la boîte de dialogue **Ajouter un environnement virtuel** affiche une option pour installer les packages automatiquement, ce qui vous permet de recréer facilement un environnement sur un autre ordinateur :

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

Dans le cadre de l’utilisation typique de Python, la variable d’environnement `PYTHONPATH` (ou `IRONPYTHONPATH`, etc.) fournit le chemin de recherche par défaut pour les fichiers de module. Autrement dit, lorsque vous utilisez une instruction `import <name>`, Python recherche d’abord un nom correspondant dans ses modules intégrés, puis recherche le dossier contenant le code Python que vous exécutez et le « chemin de recherche de module » tel que défini par la variable d’environnement applicable. (Consultez les sections [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Chemin de recherche de module) et [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables d’environnement) dans la documentation Python principale.)

La variable d’environnement de chemin de recherche est cependant ignorée par Visual Studio, même si elle a été définie pour l’ensemble du système. En fait, elle est ignorée *car* elle est définie pour l’ensemble du système et génère donc certaines questions qui ne peuvent pas être traitées automatiquement : Les modules auxquels il est fait référence sont-ils destinés à Python 2.7 ou Python 3.3 ? Vont-ils remplacer les modules de bibliothèque standard ? Le développeur est-il informé de ce comportement ou s’agit-il d’une tentative de piratage ?

La prise en charge de Python dans Visual Studio fournit ainsi un moyen permettant de spécifier les chemins de recherche directement dans les environnements et les projets. Les chemins de recherche sont transmis sous la forme d’une valeur de `PYTHONPATH` (ou similaire) quand vous déboguez ou exécutez votre script depuis Visual Studio. En ajoutant des chemins de recherche, Visual Studio inspecte les bibliothèques de ces emplacements et génère des bases de données IntelliSense pour celles-ci (la construction de la base de données peut prendre un certain temps en fonction du nombre de bibliothèques).

Pour ajouter un chemin de recherche, cliquez avec le bouton droit sur l’élément **Chemins de recherche** dans l’Explorateur de solutions, sélectionnez **Add Folder to Search Path...** (Ajouter un dossier au chemin de recherche...), puis sélectionnez le dossier à inclure. Ce chemin d’accès est utilisé pour n’importe quel environnement associé au projet.

Les fichiers avec une extension `.zip` ou `.egg` peuvent également être ajoutés en tant que chemins de recherche en sélectionnant **Add Zip Archive to Search Path...** (Ajouter une archive zip au chemin de recherche...). À l’instar des dossiers, le contenu de ces fichiers est analysé et mis à disposition d’IntelliSense.

> [!Note]
> Il est possible d’ajouter un chemin de recherche aux modules Python 2.7 pendant que vous utilisez Python 3.3, et vous pouvez voir des erreurs en conséquence.

Si vous utilisez régulièrement les mêmes chemins de recherche et si le contenu ne change pas souvent, il peut être plus efficace de l’installer dans votre dossier site-packages. Il est ensuite analysé et stocké dans la base de données IntelliSense, il est toujours associé à l’environnement souhaité et aucun chemin de recherche ne doit être ajouté pour chaque projet.

