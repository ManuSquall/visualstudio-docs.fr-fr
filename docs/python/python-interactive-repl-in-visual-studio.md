---
title: Fenêtre interactive Python (REPL)
description: Guide pratique pour utiliser la fenêtre interactive (REPL) pour le code Python dans Visual Studio pour un développement de code rapide.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 2eeffea641fd6d571b8b682aebab7f7d0ff83a41
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499066"
---
# <a name="work-with-the-python-interactive-window"></a>Utiliser la fenêtre interactive Python

Visual Studio intègre une fenêtre REPL (read-evaluate-print loop) interactive pour chacun de vos environnements Python, ce qui permet d’améliorer le REPL obtenu avec *python.exe* sur la ligne de commande. La fenêtre **Interactive** (ouverte avec les commandes de menu **Affichage** > **Autres fenêtres** > **&lt;environnement&gt; Interactif**) vous permet d’entrer du code Python arbitraire et de voir immédiatement les résultats. Ce mode de codage vous aide à étudier et à tester des API et des bibliothèques, mais aussi à développer de manière interactive du code opérationnel à inclure dans vos projets.

![Fenêtre interactive Python](media/interactive-window.png)

Visual Studio propose plusieurs modes REPL Python au choix :

| REPL | Description | Modification | Débogage | Images |
| --- | --- | --- | --- | --- |
| Standard | REPL par défaut, communique directement avec Python | Modification standard (multiligne, etc.). | Oui, via `$attach` | Non |
| Débogage | REPL par défaut, communique avec le processus Python débogué | Modification standard | Débogage uniquement | Non |
| IPython | REPL qui communique avec le serveur principal IPython | Commandes IPython, avantages de Pylab | Non | Oui, inline dans REPL |
| IPython sans Pylab | REPL qui communique avec le serveur principal IPython | IPython standard | Non | Oui, fenêtre distincte | 

Cet article décrit les modes REPL **Standard** et **Débogage**. Pour plus d’informations sur les modes IPython, consultez [Utiliser IPython REPL](interactive-repl-ipython.md).

Pour obtenir une procédure pas à pas détaillée avec des exemples, notamment les interactions avec l’éditeur **Ctrl**+**Entrée**, consultez [Tutoriel - Étape 3 : Utiliser la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md). 

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | [Regarder une vidéo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567) sur la fenêtre **Interactive** (2 min 22 s).|

## <a name="open-an-interactive-window"></a>Ouvrir une fenêtre interactive

Il existe plusieurs manières d’ouvrir la fenêtre **Interactive** pour un environnement.

En premier lieu, passez à la fenêtre Environnements Python (**Affichage** > **Autres fenêtres** > **Environnements Python** ou **Ctrl**+**K** > **Ctrl**+**`**), puis sélectionnez la commande ou le bouton **Ouvrir une fenêtre interactive** pour l’environnement choisi.

![Lien vers la fenêtre interactive dans la fenêtre des environnements Python](media/interactive-window-opening.png)

En deuxième lieu, quasiment au bas du menu **Affichage** > **Autres fenêtres**, vous trouverez une commande **Fenêtre interactive Python** pour votre environnement par défaut, ainsi qu’une commande pour passer à la fenêtre **Environnements** :

![Éléments de menu de la fenêtre interactive dans View > Other Windows (Affichage > Autres fenêtres)](media/interactive-window-menu.png)

En troisième lieu, ouvrez une fenêtre **Interactive** sur le fichier de démarrage de votre projet, ou pour un fichier autonome, en sélectionnant la commande de menu **Déboguer** > **Exécuter \<Projet | Fichier> en mode interactif Python**  (**Maj**+**Alt**+**F5**) :

![Exécution du projet dans le menu Python Interactive](media/interactive-execute-project.png)

Enfin, sélectionnez le code dans le fichier, et utilisez la commande [**Envoyer vers Interactive**](#send-to-interactive-command) décrite ci-dessous.

## <a name="interactive-window-options"></a>Options de la fenêtre interactive

Vous pouvez contrôler différents aspects de la fenêtre **Interactive** via **Outils** > **Options** > **Python Tools** > **Fenêtres interactives** (consultez [Options](python-support-options-and-settings-in-visual-studio.md)) :

![Options de la fenêtre interactive Python](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Utiliser la fenêtre interactive

Une fois que la fenêtre **Interactive** est ouverte, vous pouvez commencer à entrer du code ligne par ligne, à l’invite **\>\>\>**. La fenêtre **Interactive** exécute chaque ligne que vous entrez, ce qui inclut l’importation de modules, la définition de variables, etc. :

![Fenêtre interactive Python](media/interactive-window.png)

L’exception se produit quand des lignes de code supplémentaires sont nécessaires pour élaborer une instruction complète, par exemple quand une instruction `for` se termine par un signe deux-points, comme illustré ci-dessus. Dans ce cas, l’invite de ligne devient **...** pour vous indiquer que vous devez entrer des lignes supplémentaires pour le bloc, comme illustré sur la quatrième et la cinquième ligne de la capture ci-dessus. Quand vous appuyez sur **Entrée** sur une ligne vide, la fenêtre **Interactive** ferme le bloc et l’exécute dans l’interpréteur.

> [!Tip]
> La fenêtre **Interactive** améliore l’expérience utilisateur classique de l’environnement en ligne de commande REPL de Python en mettant automatiquement en retrait les instructions qui font partie d’une étendue environnante. Son historique (rappelé avec la flèche vers le haut) fournit également des éléments multilignes, tandis que la fonctionnalité REPL de la ligne de commande fournit uniquement des lignes uniques.

<a name="meta-commands"></a> La fenêtre **Interactive** prend également en charge plusieurs métacommandes. Toutes les métacommandes commencent par `$` ; vous pouvez taper `$help` pour obtenir la liste des métacommandes et `$help <command>` pour obtenir des détails relatifs à l’utilisation d’une commande spécifique.

| Métacommande | Description |
| --- | --- |
| `$$` | Insère un commentaire, utile pour commenter le code dans votre session. |
| `$attach` | Attache le débogueur Visual Studio au processus de fenêtre REPL pour activer le débogage. |
| `$cls`, `$clear` | Efface le contenu de la fenêtre de l’éditeur, en laissant intacts l’historique et le contexte d’exécution. |
| `$help` | Affiche une liste de commandes ou une aide sur une commande spécifique. |
| `$load` | Charge les commandes d’un fichier et s’exécute jusqu’à la fin. |
| `$mod` | Remplace la portée actuelle par le nom de module spécifié. |
| `$reset` | Réinitialise l’environnement d’exécution à l’état initial, tout en conservant l’historique. |
| `$wait` | Respecte un temps d’attente correspondant au minimum au nombre de millisecondes spécifié. |

Les commandes peuvent également être étendues par les extensions Visual Studio en implémentant et en exportant `IInteractiveWindowCommand` ([exemple](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Changer d’étendue

Par défaut, la fenêtre **Interactive** d’un projet se limite au fichier de démarrage du projet, comme si vous l’aviez exécutée à partir de l’invite de commandes. Pour un fichier autonome, elle se limite à ce fichier. Toutefois, vous pouvez changer l’étendue à tout moment pendant votre session REPL à l’aide du menu déroulant situé en haut de la fenêtre **Interactive** :

![Portées de la fenêtre interactive](media/interactive-scopes.png)

Une fois que vous importez un module, par exemple en tapant `import importlib`, des options s’affichent dans la liste déroulante et vous permettent de basculer vers n’importe quelle portée de ce module. Un message dans la fenêtre **Interactive** indique également la nouvelle étendue, ce qui vous permet de suivre votre progression vers un état spécifique dans une session.

Si vous entrez `dir()` dans une portée, vous obtenez les identificateurs valides dans cette portée, notamment les noms des fonctions, les classes et les variables. Par exemple, si vous utilisez `import importlib` suivi de `dir()`, vous obtenez les informations suivantes :

![Fenêtre interactive dans la portée importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Commande Envoyer vers Interactive

En plus de pouvoir travailler directement dans la fenêtre **Interactive**, vous pouvez sélectionner du code dans l’éditeur, cliquer avec le bouton droit, puis choisir **Envoyer vers Interactive**, ou appuyer sur **Ctrl**+**Entrée**.

![Commande de menu Envoyer vers Interactive](media/interactive-send-to.png)

Cette commande est utile dans le cadre du développement de code itératif ou évolutionnaire, car elle permet notamment de tester votre code à mesure que vous le développez. Par exemple, une fois que vous avez envoyé du code dans la fenêtre **Interactive** et que vous avez vu sa sortie, vous pouvez appuyer sur la touche Haut pour afficher de nouveau le code, le modifier et le tester rapidement à l’aide des touches **Ctrl**+**Entrée**. (Appuyez sur **Entrée** à la fin d’une entrée pour l’exécuter, ou appuyez sur **Entrée** au milieu d’une entrée pour insérer une nouvelle ligne.) Une fois que vous obtenez le code que vous souhaitez, vous pouvez facilement le copier dans votre fichier projet.

> [!Tip]
> Par défaut, Visual Studio supprime **>>>** et **...** REPL affiche une invite quand vous collez du code de la fenêtre **Interactive** dans l’éditeur. Vous pouvez changer ce comportement sous l’onglet **Outils** > **Options** > **Éditeur de texte** > **Python** > **Avancé** à l’aide de l’option **Le collage supprime les invites REPL**. Consultez [Options - Options diverses](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

Quand vous utilisez un fichier de code comme bloc-notes, vous avez souvent un petit bloc de code que vous souhaitez envoyer en une seule fois. Pour regrouper le code, marquez-le comme *cellule de code* en ajoutant un commentaire commençant par `#%%` au début de la cellule, ce qui met fin à la précédente. Les cellules de code peuvent être développées et réduites. L’utilisation de **Ctrl**+**Entrée** à l’intérieur d’une cellule de code permet d’envoyer l’intégralité de la cellule dans la fenêtre **Interactive** et de passer à la suivante.

Visual Studio détecte également les cellules de code commençant par des commentaires du type `# In[1]:`, qui est le format que vous obtenez lors de l’exportation d’un bloc-notes Jupyter sous forme de fichier Python. Cette détection facilite l’exécution d’un bloc-notes à partir d’[Azure Notebooks](https://notebooks.azure.com/) en le téléchargeant sous la forme d’un fichier Python, en l’ouvrant dans Visual Studio et en utilisant **Ctrl**+**Entrée** pour exécuter chaque cellule.

![Cellules de code interactif](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Comportement IntelliSense

La fenêtre **Interactive** inclut la fonctionnalité IntelliSense basée sur les objets dynamiques, contrairement à l’éditeur de code dans lequel la fonctionnalité IntelliSense repose uniquement sur l’analyse du code source. Ces suggestions sont plus appropriées dans la fenêtre **Interactive**, en particulier avec du code généré dynamiquement. L’inconvénient est que les fonctions qui comportent des effets secondaires (par exemple, la journalisation des messages) peuvent affecter votre expérience de développement.

Si ce comportement pose problème, changez les paramètres sous **Outils** > **Options** > **Python Tools** > **Fenêtres interactives** dans le groupe **Mode de saisie semi-automatique**, comme indiqué dans [Options - Options des fenêtres interactives](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
