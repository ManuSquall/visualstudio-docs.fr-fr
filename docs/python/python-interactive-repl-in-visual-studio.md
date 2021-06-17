---
title: Fenêtre interactive Python (REPL)
description: Utilisez la fenêtre interactive (REPL) pour développer rapidement du code Python dans Visual Studio.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 21115673a41e26b2f1685442d2ed0ad93a147990
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254886"
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

Pour obtenir une procédure pas à pas détaillée avec des exemples, notamment les interactions avec l’éditeur comme **CTRL** + **entrée**, consultez [le didacticiel étape 3 : utiliser la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Ouvrir une fenêtre interactive

Il existe plusieurs façons d’ouvrir la fenêtre **interactive** pour un environnement.

Tout d’abord, basculez vers la fenêtre environnements Python (**Afficher** d'  >  **autres**  >  **environnements Windows python** ou **CTRL** + **K**  >  **CTRL** + **`** ) et sélectionnez la commande ou le bouton **ouvrir une fenêtre interactive** pour un environnement choisi.

![Lien vers la fenêtre interactive dans la fenêtre des environnements Python](media/interactive-window-opening.png)

Deuxièmement, près du bas du menu **Afficher** les  >  **autres fenêtres** , il existe une commande de **fenêtre interactive Python** pour votre environnement par défaut, ainsi qu’une commande pour basculer vers la fenêtre **environnements** :

![Éléments de menu de la fenêtre interactive dans View > Other Windows (Affichage > Autres fenêtres)](media/interactive-window-menu.png)

Troisièmement, vous pouvez ouvrir une fenêtre **interactive** sur le fichier de démarrage de votre projet, ou pour un fichier autonome, en sélectionnant la commande de menu **Déboguer**  >  **exécuter \<Project | File> dans python interactive** (**MAJ** + **ALT** + **F5**) :

![Exécution du projet dans le menu Python Interactive](media/interactive-execute-project.png)

Enfin, sélectionnez le code dans le fichier, et utilisez la commande [**Envoyer vers Interactive**](#send-to-interactive-command) décrite ci-dessous.

## <a name="interactive-window-options"></a>Options de la fenêtre interactive

Vous pouvez contrôler différents aspects de la fenêtre **Interactive** via **Outils** > **Options** > **Python** > **Fenêtres interactives** (consultez [Options](python-support-options-and-settings-in-visual-studio.md)) :

![Options de la fenêtre interactive Python](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Utiliser la fenêtre interactive

Une fois la fenêtre **interactive** ouverte, vous pouvez commencer à entrer le code ligne par ligne à l' **\>\>\>** invite de commandes. La fenêtre **interactive** exécute chaque ligne au fur et à mesure de son entrée, ce qui comprend l’importation de modules, la définition de variables, etc. :

![Fenêtre interactive Python](media/interactive-window.png)

L’exception se produit quand des lignes de code supplémentaires sont nécessaires pour élaborer une instruction complète, par exemple quand une instruction `for` se termine par un signe deux-points, comme illustré ci-dessus. Dans ce cas, l’invite de ligne devient **...** pour vous indiquer que vous devez entrer des lignes supplémentaires pour le bloc, comme illustré sur la quatrième et la cinquième ligne de la capture ci-dessus. Lorsque vous appuyez sur **entrée** sur une ligne vide, la fenêtre **interactive** ferme le bloc et l’exécute dans l’interpréteur.

> [!Tip]
> La fenêtre **interactive** améliore l’expérience de réplication de ligne de commande python habituelle en mettant automatiquement en retrait les instructions qui appartiennent à une portée environnante. Son historique (rappelé avec la flèche vers le haut) fournit également des éléments multilignes, tandis que la fonctionnalité REPL de la ligne de commande fournit uniquement des lignes uniques.

<a name="meta-commands"></a> La fenêtre **interactive** prend également en charge plusieurs commandes meta. Toutes les métacommandes commencent par `$` ; vous pouvez taper `$help` pour obtenir la liste des métacommandes et `$help <command>` pour obtenir des détails relatifs à l’utilisation d’une commande spécifique.

:::moniker range="<=vs-2017"

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

:::moniker-end

:::moniker range=">=vs-2019"

| Métacommande | Description |
| --- | --- |
| `$$` | Insère un commentaire, utile pour commenter le code dans votre session. |
| `$cls`, `$clear` | Efface le contenu de la fenêtre de l’éditeur, en laissant intacts l’historique et le contexte d’exécution. |
| `$help` | Affiche une liste de commandes ou une aide sur une commande spécifique. |
| `$load` | Charge les commandes d’un fichier et s’exécute jusqu’à la fin. |
| `$mod` | Remplace la portée actuelle par le nom de module spécifié. |
| `$reset` | Réinitialise l’environnement d’exécution à l’état initial, tout en conservant l’historique. |
| `$wait` | Respecte un temps d’attente correspondant au minimum au nombre de millisecondes spécifié. |

:::moniker-end

Les commandes peuvent également être étendues par les extensions Visual Studio en implémentant et en exportant `IInteractiveWindowCommand` ([exemple](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Changer d’étendue

Par défaut, la fenêtre **interactive** pour un projet est limitée au fichier de démarrage du projet comme si vous l’exécutiez à partir de l’invite de commandes. Pour un fichier autonome, elle se limite à ce fichier. Toutefois, vous pouvez changer l’étendue à tout moment pendant votre session REPL à l’aide du menu déroulant situé en haut de la fenêtre **Interactive** :

![Portées de la fenêtre interactive](media/interactive-scopes.png)

Une fois que vous importez un module, par exemple en tapant `import importlib`, des options s’affichent dans la liste déroulante et vous permettent de basculer vers n’importe quelle portée de ce module. Un message dans la fenêtre **interactive** indique également la nouvelle étendue, ce qui vous permet d’effectuer le suivi de la façon dont vous avez atteint un certain état au cours de votre session.

Si vous entrez `dir()` dans une portée, vous obtenez les identificateurs valides dans cette portée, notamment les noms des fonctions, les classes et les variables. Par exemple, si vous utilisez `import importlib` suivi de `dir()`, vous obtenez les informations suivantes :

![Fenêtre interactive dans la portée importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Commande Envoyer vers Interactive

En plus de travailler directement dans la fenêtre **interactive** , vous pouvez sélectionner du code dans l’éditeur, cliquer avec le bouton droit, puis choisir **Envoyer vers interactive** ou appuyer sur **CTRL** + **entrée**.

![Commande de menu Envoyer vers Interactive](media/interactive-send-to.png)

Cette commande est utile dans le cadre du développement de code itératif ou évolutionnaire, car elle permet notamment de tester votre code à mesure que vous le développez. Par exemple, une fois que vous avez envoyé un morceau de code à la fenêtre **interactive** et que vous avez vu sa sortie, vous pouvez appuyer sur la flèche vers le haut pour afficher à nouveau le code, le modifier et le tester rapidement en appuyant sur **CTRL** + **entrée**. (Appuyez sur **entrée** à la fin de l’entrée pour l’exécuter, mais Appuyez sur **entrée** au milieu de l’entrée insère un saut de ligne.) Une fois que vous avez le code souhaité, vous pouvez le copier à nouveau dans votre fichier projet.

> [!Tip]
> Par défaut, Visual Studio supprime **>>>** et **...** Réplication des invites lors du collage du code à partir de la fenêtre **interactive** dans l’éditeur. Vous pouvez modifier ce comportement dans l’onglet **Outils**  >  **options** de l'  >  **éditeur de texte**  >  **python**  >  **avancé** en utilisant l’option **coller supprime les invites de réplication** . Consultez [options-options diverses](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Utiliser les cellules de code

Vous pouvez utiliser les cellules de code dans l’analyse de données. Elles sont prises en charge par divers éditeurs de texte.

Par exemple, quand vous utilisez un fichier de code en tant que bloc-notes, vous avez souvent un petit bloc de code que vous souhaitez envoyer en une seule fois. Pour regrouper le code, marquez-le comme *cellule de code* en ajoutant un commentaire commençant par `#%%` au début de la cellule, ce qui met fin à la précédente. Les cellules de code peuvent être réduites et développées, et l’utilisation de la **touche Ctrl** + **entrée** à l’intérieur d’une cellule de code envoie la cellule entière à la fenêtre **interactive** et passe au suivant.

Visual Studio détecte également les cellules de code commençant par des commentaires du type `# In[1]:`, qui est le format que vous obtenez lors de l’exportation d’un bloc-notes Jupyter sous forme de fichier Python. Cette détection facilite l’exécution d’un bloc-notes à partir de [Azure Notebooks](https://notebooks.azure.com/) en le téléchargeant sous forme de fichier Python, en l’ouvrant dans Visual Studio et en utilisant **CTRL** + **entrée** pour exécuter chaque cellule.

![Cellules de code interactif](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Comportement IntelliSense

La fenêtre **interactive** comprend IntelliSense basé sur les objets actifs, contrairement à l’éditeur de code dans lequel IntelliSense est basé uniquement sur l’analyse du code source. Ces suggestions sont plus correctes dans la fenêtre **interactive** , en particulier avec le code généré dynamiquement. L’inconvénient est que les fonctions qui comportent des effets secondaires (par exemple, la journalisation des messages) peuvent affecter votre expérience de développement.

Si ce comportement est un problème, modifiez les paramètres sous **Outils**  >  **options**  >  **python**  >  **interactive Windows** dans le groupe **mode de saisie semi-automatique** , comme décrit dans [options-options Windows interactives](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
