---
title: Options et paramètres pour Python
description: Document de référence pour les différents paramètres dans Visual Studio concernant des projets et du code Python.
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 08501d71400a0df139022f04e68573d0dd1449d1
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409913"
---
# <a name="options-for-python-in-visual-studio"></a>Options pour Python dans Visual Studio

Pour afficher les options relatives à Python, utilisez la commande de menu **Outils** > **Options**, vérifiez que la case **Afficher tous les paramètres** est cochée, puis accédez à **Python** :

::: moniker range="vs-2017"
![Boîte de dialogue Options pour Python, onglet Général](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Boîte de dialogue Options pour Python, onglet Général](media/options-general-2019.png)
::: moniker-end

Il existe également des options supplémentaires spécifiques à Python sous l’onglet **Éditeur de texte** > **Python** > **Avancé**, ainsi que sous l’onglet **Environnement** > **Polices et couleurs** dans le groupe **Éditeur de texte**.

> [!Note]
> Le groupe **Expérimental** contient des options pour des fonctionnalités encore en cours de développement qui ne sont pas décrites ici. Celles-ci sont souvent décrites dans les posts du [blog sur l’ingénierie Python chez Microsoft](https://devblogs.microsoft.com/python/).

## <a name="general-options"></a>Options générales

(Onglet **Outils** > **Options** > **Python**.)

| Option | Default | Description |
| --- | --- | --- |
| **Afficher la fenêtre Sortie pendant la création d’environnements virtuels**| Il en va | Désactivez-la pour empêcher la fenêtre **Sortie** de s’afficher. |
| **Afficher la fenêtre Sortie pendant l’installation ou la suppression des packages** | Il en va | Désactivez-la pour empêcher la fenêtre **Sortie** de s’afficher. |
| **Afficher la barre de notification pour créer des environnements** | Il en va | *Visual Studio 2019 uniquement.* Lorsque cette option est définie et que l’utilisateur ouvre un projet qui contient un fichier *requirements.txt* ou *environment.yml*, Visual Studio affiche une barre d’informations avec des suggestions pour créer un environnement virtuel ou un environnement conda, respectivement, au lieu d’utiliser l’environnement global par défaut. |
| **Afficher la barre de notification pour installer des packages** | Il en va | *Visual Studio 2019 uniquement.* Lorsque cette option est définie et que l’utilisateur ouvre un projet qui contient un fichier *requirements.txt* (et n’utilise pas l’environnement global par défaut), Visual Studio compare ces exigences avec les packages installés dans l’environnement actuel. Si des packages sont manquants, Visual Studio affiche une invite pour installer ces dépendances. |
| **Toujours exécuter des Gestionnaires de package en tant qu’administrateur** | Off | Élève toujours les privilèges de `pip install` et d’opérations de gestionnaire de package similaires pour tous les environnements. Au moment de l’installation des packages, Visual Studio demande des privilèges d’administrateur, si l’environnement se trouve dans une zone protégée du système de fichiers, par exemple *c:\Program Files*. Dans cette invite, vous pouvez choisir de toujours élever les privilèges de la commande d’installation pour cet environnement uniquement. Consultez [Onglet packages](python-environments-window-tab-reference.md#packages-tab). |
| **Générer automatiquement la base de données de saisie semi-automatique à la première utilisation** | Il en va | *S’applique à Visual Studio 2017 version 15.5, versions antérieures et versions ultérieures lorsque vous utilisez une base de données IntelliSense.* Donne la priorité à l’achèvement de la base de données pour une bibliothèque quand vous écrivez du code qui l’utilise. Pour plus d’informations, voir [Onglet IntelliSense](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab). |
| **Ignorer les variables PYTHONPATH à l’échelle du système** | Il en va | PYTHONPATH est ignoré par défaut, car Visual Studio fournit un moyen plus direct de spécifier des chemins de recherche dans les projets et environnements. Consultez la page [Chemins de recherche](search-paths.md) pour plus d’informations. |
| **Mettre à jour les chemins de recherche lors de l’ajout de fichiers liés** | Il en va | Quand cette option est définie, l’ajout d’un [fichier lié](managing-python-projects-in-visual-studio.md#linked-files) à un projet met à jour les [Chemins de recherche](search-paths.md) afin qu’IntelliSense puisse inclure le contenu du dossier du fichier lié dans sa base de données de saisie semi-automatique. Désactivez cette option pour exclure ce contenu de la base de données de saisie semi-automatique. |
| **Avertir quand le module importé est introuvable** | Il en va | Désactivez cette option pour supprimer les avertissements quand vous savez qu’un module importé n’est actuellement pas disponible, mais n’affecte pas par ailleurs le fonctionnement du code. |
| **Signaler une indentation incohérente comme** | **Avertissements** | Comme l’interpréteur Python dépend fortement d’une mise en retrait appropriée pour déterminer la portée, Visual Studio émet par défaut des avertissements quand il détecte des mises en retrait incohérentes pouvant indiquer des erreurs de codage. Option définie sur **Erreurs** pour être encore plus stricte, ce qui entraîne la fermeture du programme dans ces cas. Pour désactiver complètement ce comportement, sélectionnez **Ne pas le faire**. |
| **Rechercher des enquêtes/actualités** | **Une fois par semaine** | *Visual Studio 2017 et versions antérieures.* Définit la fréquence à laquelle vous permettez à Visual Studio d’ouvrir une fenêtre contenant une page web avec des enquêtes et des actualités liées à Python, le cas échéant. Les options sont **Jamais**, **Une fois par jour**, **Une fois par semaine** et **Une fois par mois**. |
| Bouton **Réinitialiser toutes les boîtes de dialogue masquées définitivement** | n/a | Différentes boîtes de dialogue fournissent des options telles que **Ne plus afficher ce message**. Utilisez ce bouton pour effacer ces options et entraîner le retour des boîtes de dialogue. |

::: moniker range="vs-2017"
![Boîte de dialogue Options pour Python, onglet Général](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Boîte de dialogue Options pour Python, onglet Général](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Options de Conda

(**Outils** > **options** > onglet **Conda** de **python** >.)

| Option | Default | Description |
| --- | --- | --- |
| **Chemin de l’exécutable Conda** | (vide) | Spécifie un chemin d’accès exact à l’exécutable *conda.exe* au lieu de compter sur l’installation Miniconda par défaut qui est fournie avec la charge de travail Python. Si un autre chemin d’accès est indiqué ici, il est prioritaire sur l’installation par défaut et les autres exécutables conda.exe spécifiés dans le Registre. Vous pouvez modifier ce paramètre si vous installez manuellement une version plus récente d’Anaconda ou de Miniconda, ou si vous souhaitez utiliser une distribution 32 bits au lieu de la distribution 64 bits par défaut. |

![Boîte de dialogue Options de Python, onglet Serveur de langage](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Options de débogage

(Onglet **Outils** > **Options** > **Python** > **Débogage**.)

| Option | Default | Description |
| --- | --- | --- |
| **Demander avant d’exécuter en présence d’erreurs** | Il en va | Quand cette option est définie, vous êtes invité à confirmer que vous souhaitez exécuter le code qui contient des erreurs. Désactivez cette option pour désactiver l’avertissement. |
| **Attendre une entrée quand le processus quitte de manière inhabituelle**<br/><br/>**Attendre une entrée quand le processus quitte de manière habituelle** | Activées (toutes deux) | Un programme Python démarré à partir de Visual Studio s’exécute dans sa propre fenêtre de console. Par défaut, la fenêtre attend que vous appuyiez sur une touche avant de se fermer, quelle que soit la façon dont le programme se termine. Pour supprimer cette invite et fermer la fenêtre automatiquement, désactivez l’une de ces options, ou les deux. |
| **Sortie du programme Tee dans la fenêtre Sortie du débogage** | Il en va | Affiche la sortie du programme dans une fenêtre de console distincte et la fenêtre **Sortie** de Visual Studio. Désactivez cette option pour afficher la sortie uniquement dans la fenêtre de console distincte. |
| **Arrêter en cas d’exception SystemExit avec le code de sortie zéro** | Off | Si cette option est définie, arrête le débogueur sur cette exception. Quand elle est désactivée, le débogueur se ferme sans s’arrêter. |
| **Activer le débogage de la bibliothèque Python standard** | Off | Permet d’effectuer un pas à pas détaillé dans le code source de la bibliothèque standard pendant le débogage, mais augmente le temps nécessaire au démarrage du débogueur.|
| **Montrer la valeur de retour de la fonction** | Il en va | *Visual Studio 2019 uniquement.* Affiche les valeurs renvoyées de fonction dans la fenêtre **Variables locales** lors du survol d’un appel de fonction dans le débogueur (F10) |
| **Utiliser le débogueur hérité** | Off | *Visual Studio 2019 uniquement.* Indique à Visual Studio d’utiliser le débogueur hérité par défaut. Pour plus d’informations, consultez [Débogage - Utiliser le débogueur hérité](debugging-python-in-visual-studio.md#use-the-legacy-debugger). |

::: moniker range="vs-2017"
![Boîte de dialogue Options pour Python, onglet Débogage](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Boîte de dialogue Options pour Python, onglet Débogage](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Options des diagnostics

(Onglet **Outils** > **Options** > **Python** > **Diagnostics**.)

| Option | Default | Description |
| --- | --- | --- |
| **Inclure les journaux d’analyse** | Il en va | Inclut des journaux détaillés relatifs à l’analyse des environnements Python installés lors de l’enregistrement des diagnostics dans un fichier ou en les copiant dans le Presse-papiers à l’aide des boutons. Cette option peut augmenter considérablement la taille du fichier généré, mais elle est souvent nécessaire pour diagnostiquer les problèmes IntelliSense. |
| Bouton **Enregistrer le diagnostic dans un fichier** | n/a | Demande un nom de fichier, puis enregistre le journal dans un fichier texte. |
| Bouton **Copier le diagnostic dans le Presse-papiers** | n/a | Copie l’intégralité du journal dans le Presse-papiers ; cette opération peut prendre un certain temps, en fonction de la taille du journal. |

![Boîte de dialogue Options pour Python, onglet Diagnostics](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Options des fenêtres interactives

(Onglet **Outils** > **Options** > **Python** > **Fenêtres interactives**.)

| Option | Default | Description |
| --- | --- | --- |
| **Scripts** | n/a | Spécifie un dossier général pour les scripts de démarrage à appliquer aux fenêtres **interactives** pour tous les environnements. Consultez [Scripts de démarrage](python-environments-window-tab-reference.md#startup-scripts). Notez, toutefois, que cette fonctionnalité ne fonctionne pas pour l’instant. |
| **Les flèches Haut/Bas permettent de naviguer dans l’historique** | Il en va | Utilise les touches de direction pour naviguer dans l’historique de la fenêtre **Interactive**. Désactivez ce paramètre afin d’utiliser les touches de direction pour naviguer dans la sortie de la fenêtre **Interactive** à la place. |
| **Mode de saisie semi-automatique** | **Évaluer uniquement les expressions sans appel de fonction** | Le processus permettant de déterminer les membres disponibles sur une expression dans la fenêtre **Interactive** peut nécessiter l’évaluation de l’expression inachevée, ce qui peut aboutir à des effets secondaires ou des fonctions appelées à plusieurs reprises. Le paramètre par défaut, **Évaluer uniquement les expressions sans appel de fonction**, exclut les expressions qui apparaissent pour appeler une fonction, mais évalue les autres expressions. Par exemple, il évalue `a.b` mais pas `a().b`.  **Ne jamais évaluer les expressions** empêche tous les effets secondaires, en utilisant uniquement le moteur IntelliSense normal pour obtenir des suggestions. **Évaluer toutes les expressions** évalue l’expression complète pour obtenir des suggestions, indépendamment des effets secondaires. |
| **Masquer les suggestions d’analyse statique** | Off | Quand cette option est définie, n’affiche que les suggestions obtenues en évaluant l’expression. Si cette option est associée à la valeur **Ne jamais évaluer les expressions** de l’option **Mode de saisie semi-automatique**, aucune saisie semi-automatique utile ne s’affiche dans la fenêtre **Interactive**. |

![Boîte de dialogue Options pour Python, onglet Fenêtres interactives](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Options Serveur de langage

(**Outils** > **options** > l’onglet **serveur de langage** **python** >.)

| Option | Default | Description |
| --- | --- | --- |
| **Désactiver les complétions de Typeshed** | Off | Visual Studio IntelliSense utilise généralement une version groupée de Typeshed (un ensemble de fichiers *.pyi*) pour rechercher des indicateurs de type de bibliothèque standard et de bibliothèques tierces pour Python 2 et Python 3. La définition de cette option désactive le comportement TypeShed groupé. |
| **Chemin Typeshed personnalisé** | (vide) | Si cette option est définie, Visual Studio utilise les fichiers Typeshed de ce chemin au lieu de sa version groupée. Ignorez si l’option **Désactiver les complétions de Typeshed** est définie. |

![Boîte de dialogue Options de Python, onglet Serveur de langage](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Options avancées de l’éditeur Python

(Onglet **Outils** > **Options** > **Éditeur de texte** > **Python** > **Avancé**.)

### <a name="completion-results"></a>Résultats de la saisie semi-automatique

| Option | Default | Description |
| --- | --- | --- |
| **La saisie semi-automatique des membres affiche l’intersection des membres** | Off | Quand cette option est définie, affiche uniquement les saisies semi-automatiques qui sont prises en charge par tous les types possibles. |
| **Liste de filtres basée sur une chaîne de recherche** | Il en va | Applique le filtrage des suggestions de saisie semi-automatique quand vous tapez (activée par défaut). |
| **Afficher automatiquement la saisie semi-automatique pour tous les identificateurs** | Il en va | Désactivez cette option pour désactiver les complétions dans la fenêtre de l’éditeur et la fenêtre **Interactive**. |

### <a name="selection-in-completion-list"></a>Sélection dans la liste de saisie semi-automatique

| Option | Default | Description |
| --- | --- | --- |
| **Validé en tapant les caractères suivants** | **{}\[\]().,:;+-*/%&&#124;^~=<>#@\\** | Comme ces caractères suivent généralement un identificateur qui peut être sélectionné dans une liste de saisie semi-automatique, il est pratique de valider la saisie semi-automatique simplement en tapant un caractère. Vous pouvez supprimer ou ajouter des caractères spécifiques dans la liste si vous le souhaitez.  |
| **Entrée valide la saisie semi-automatique actuelle** | Il en va | Quand cette option est définie, la touche **Entrée** permet de choisir et d’appliquer la complétion sélectionnée, comme avec les caractères ci-dessus (mais, bien entendu, il n’existe pas de caractère pour la touche **Entrée** pouvant être intégré directement dans cette liste !). |
| **Ajouter une ligne avec entrée après le mot complet tapé** | Off | Par défaut, si vous tapez le mot entier qui s’affiche dans la fenêtre contextuelle de saisie semi-automatique, et si vous appuyez sur **Entrée**, vous validez cette complétion. En définissant cette option, vous validez de manière effective les complétions quand vous avez fini de taper l’identificateur. Ainsi, **Entrée** permet d’insérer une nouvelle ligne. |

### <a name="miscellaneous-options"></a>Options diverses

| Option | Default | Description |
| --- | --- | --- |
| **Passer en mode Plan à l’ouverture des fichiers** | Il en va | Activez automatiquement la fonctionnalité de mode Plan de Visual Studio dans l’éditeur lors de l’ouverture d’un fichier de code Python. |
| **Le collage supprime les invites REPL** | Il en va | Supprime **>>>** et **...** du texte collé, ce qui permet de transférer facilement le code de la fenêtre **Interactive** vers l’éditeur. Désactivez cette option si vous devez conserver ces caractères lors du collage à partir d’autres sources. |
| **Noms de couleur basés sur les types** | Il en va | Active les couleurs de syntaxe dans le code Python. |

![Boîte de dialogue Options de l’éditeur Python, onglet Avancé](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Options Polices et couleurs

(Onglet **Environnement** > **Polices et couleurs** dans le groupe **Éditeur de texte**.)

Les noms des options Python sont toutes précédées de **Python** et sont explicites. La police par défaut pour tous les thèmes de couleurs Visual Studio est 10 pt Consolas regular (non gras). Les couleurs par défaut varient selon le thème. En règle générale, vous modifiez une police ou une couleur si vous la lecture du texte est difficile avec les paramètres par défaut.

![Options de police et de couleur Python](media/options-fonts-and-colors.png)
