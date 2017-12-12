---
title: Boucle REPL interactive Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 80b53ca4a4ada7374d0d62101b00b8ed1a9ca335
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="working-with-the-python-interactive-window"></a>Utilisation de la fenêtre interactive Python

Visual Studio intègre une fenêtre REPL (read-evaluate-print loop) interactive pour chacun de vos environnements Python, qui améliore la boucle REPL que vous obtenez avec `python.exe` sur la ligne de commande. La fenêtre interactive (ouverte avec les commandes de menu **Affichage > Autres fenêtres > &lt;environnement&gt; Interactif**) vous permet d’entrer le code Python arbitraire et de voir immédiatement les résultats. Ce mode de codage vous aide à étudier et à tester des API et des bibliothèques, mais aussi à développer de manière interactive du code opérationnel à inclure dans vos projets.

![Fenêtre interactive Python](media/interactive-window.png)

Visual Studio propose plusieurs modes REPL Python au choix :

| REPL | Description | Modification | Débogage | Images |
| --- | --- | --- | --- | --- |
| Standard | REPL par défaut, communique directement avec Python | Modification standard (multiligne, etc.). | Oui, via `$attach` | Non |
| Débogage | REPL par défaut, communique avec le processus Python débogué | Modification standard | Débogage uniquement | Non |
| IPython | REPL qui communique avec le serveur principal IPython | Commandes IPython, avantages de Pylab | Non | Oui, inline dans REPL |
| IPython sans Pylab | REPL qui communique avec le serveur principal IPython | IPython standard | Non | Oui, fenêtre distincte | 

Cette rubrique décrit les modes REPL **Standard** et **Débogage**. Pour plus d’informations sur les modes IPython, consultez [Using the IPython REPL](interactive-repl-ipython.md) (Utilisation de la boucle REPL IPython).

Pour obtenir une procédure pas à pas détaillée avec des exemples, notamment les interactions avec l’éditeur comme Ctrl+Entrée, consultez [Didacticiel - Étape 3 : Utilisation de la fenêtre REPL interactive](vs-tutorial-01-03.md). Pour une présentation vidéo, consultez [Python Interactive Window](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567) (Microsoft Virtual Academy, 2 minutes 22 secondes ).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567]

## <a name="opening-an-interactive-window"></a>Ouverture d’une fenêtre interactive

Il existe plusieurs manières d’ouvrir la fenêtre interactive pour un environnement.

Tout d’abord, basculez vers la fenêtre Environnements Python (**Affichage > Autres fenêtres > Environnements Python** ou Ctrl+K, Ctrl+`) et sélectionnez la commande ou le bouton **Ouvrir une fenêtre interactive** pour l’environnement choisi.

![Lien vers la fenêtre interactive dans la fenêtre des environnements Python](media/interactive-window-opening.png)

Ensuite, près du bas du menu **Affichage > Autres fenêtres**, figure une commande **Fenêtre interactive Python** pour votre environnement par défaut, ainsi qu’une commande pour basculer vers la fenêtre des environnements :

![Éléments de menu de la fenêtre interactive dans View > Other Windows (Affichage > Autres fenêtres)](media/interactive-window-menu.png)

Vous pouvez alors ouvrir une fenêtre interactive sur le fichier de démarrage dans votre projet, ou pour un fichier autonome, en sélectionnant la commande de menu **Déboguer > Exécuter [Projet | Fichier] en mode interactif Python** (Maj+Alt+F5) :

![Exécution du projet dans le menu Python Interactive](media/interactive-execute-project.png)

Enfin, vous pouvez sélectionner du code dans un fichier et utiliser la [commande d’envoi de code vers la fenêtre interactive](#send-code-to-interactive-command) décrite ci-dessous.

## <a name="interactive-window-options"></a>Options de la fenêtre interactive

Vous pouvez contrôler différents aspects de la fenêtre interactive via la commande **Outils > Options > Python Tools > Fenêtres interactives** (consultez [Options](options.md)) :

![Options de la fenêtre interactive Python](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>Utilisation de la fenêtre interactive

Une fois que la fenêtre interactive est ouverte, vous pouvez commencer à entrer du code ligne par ligne à l’invite `>>>`. La fenêtre interactive exécute chaque ligne que vous entrez, qui comprend l’importation de modules, la définition de variables, etc :

![Fenêtre interactive Python](media/interactive-window.png)

L’exception se produit quand des lignes de code supplémentaires sont nécessaires pour élaborer une instruction complète, par exemple quand une instruction `for` se termine par un signe deux-points, comme illustré ci-dessus. Dans ces cas, l’invite de ligne affiche `...` pour vous signaler que vous devez saisir des lignes supplémentaires pour le bloc, comme illustré sur les quatrième et cinquième lignes de la capture ci-dessus. Quand vous appuyez sur Entrée sur une ligne vide, la fenêtre interactive ferme le bloc et l’exécute dans l’interpréteur.

> [!Tip]
> La fenêtre interactive améliore l’expérience habituelle de la fonctionnalité REPL de la ligne de commande Python en mettant automatiquement en retrait les instructions attachées à une portée voisine. Son historique (rappelé avec la flèche vers le haut) fournit également des éléments multilignes, tandis que la fonctionnalité REPL de la ligne de commande fournit uniquement des lignes uniques.

<a name="meta-commands"></a> La fenêtre interactive prend également en charge plusieurs métacommandes. Toutes les métacommandes commencent par `$` ; vous pouvez taper `$help` pour obtenir la liste des métacommandes et `$help <command>` pour obtenir des détails relatifs à l’utilisation d’une commande spécifique.

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

## <a name="switching-scopes"></a>Changement de portées

Par défaut, la fenêtre interactive d’un projet est limitée au fichier de démarrage du projet comme si vous l’aviez exécuté à partir de l’invite de commandes. Pour un fichier autonome, elle se limite à ce fichier. Vous pouvez cependant modifier la portée à tout moment pendant votre session REPL à l’aide du menu déroulant situé en haut de la fenêtre interactive :

![Portées de la fenêtre interactive](media/interactive-scopes.png)

Une fois que vous importez un module, par exemple en tapant `import importlib`, des options s’affichent dans la liste déroulante et vous permettent de basculer vers n’importe quelle portée de ce module. Un message dans la fenêtre interactive indique également la nouvelle portée, ce qui vous permet de savoir comment vous avez atteint un état donné au cours de votre session.

Si vous entrez `dir()` dans une portée, vous obtenez les identificateurs valides dans cette portée, notamment les noms des fonctions, les classes et les variables. Par exemple, si vous utilisez `import importlib` suivi de `dir()`, vous obtenez les informations suivantes :

![Fenêtre interactive dans la portée importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>Envoi de code à la commande interactive

En plus de pouvoir travailler directement dans la fenêtre interactive, vous pouvez sélectionner du code dans l’éditeur, cliquer avec le bouton droit, puis choisir **Envoyer vers Interactive** ou appuyer sur Ctrl+Entrée.

![Commande de menu Envoyer vers Interactive](media/interactive-send-to.png)

Cette commande est utile dans le cadre du développement de code itératif ou évolutionnaire, car elle permet notamment de tester votre code à mesure que vous le développez. Par exemple, une fois que vous avez envoyé un élément de code dans la fenêtre interactive et que vous avez vu sa sortie, vous pouvez appuyer sur la flèche du bas pour afficher de nouveau le code, le modifier et le tester rapidement à l’aide des touches Ctrl + Entrée. (Appuyez sur Entrée à la fin d'une entrée pour l’exécuter, ou appuyez sur Entrée au milieu d'une entrée pour insérer une nouvelle ligne.) Une fois que vous obtenez le code que vous souhaitez, vous pouvez facilement le copier dans votre fichier projet.

> [!Tip]
> Par défaut, Visual Studio supprime >>> et ... REPL affiche une invite lors du collage de code à partir de la fenêtre interactive dans l’éditeur. Vous pouvez changer ce comportement sur l’onglet **Outils > Options > Éditeur de texte > Python > Avancé** à l’aide de l’option **Le collage supprime les invites REPL**. Consultez [Options - Options diverses](options.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

Quand vous utilisez un fichier de code comme bloc-notes, vous avez souvent un petit bloc de code que vous souhaitez envoyer en une seule fois. Pour regrouper le code, marquez-le comme *cellule de code* en ajoutant un commentaire commençant par `#%%` au début de la cellule, ce qui met fin à la précédente. Les cellules de code peuvent être développées et réduites, et l’utilisation de Ctrl+Entrée à l’intérieur d’une cellule de code permet d’envoyer l’intégralité de la cellule dans la fenêtre interactive et de passer à la suivante.

Visual Studio détecte également les cellules de code commençant par des commentaires du type `# In[1]:`, qui est le format que vous obtenez lors de l’exportation d’un bloc-notes Jupyter sous forme de fichier Python. Cette détection facilite l’exécution d’un bloc-notes à partir d’[Azure Notebooks](https://notebooks.azure.com/) en le téléchargeant sous la forme d’un fichier Python, en l’ouvrant dans Visual Studio et en utilisant Ctrl+Entrée pour exécuter chaque cellule.

![Cellules de code interactif](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Comportement IntelliSense

La fenêtre interactive inclut la fonctionnalité IntelliSense basée sur les objets dynamiques, contrairement à l’éditeur de code dans lequel la fonctionnalité IntelliSense repose uniquement sur l’analyse du code source. Ces suggestions sont plus appropriées dans la fenêtre interactive, en particulier avec un code généré dynamiquement. L’inconvénient est que les fonctions qui comportent des effets secondaires (par exemple, la journalisation des messages) peuvent affecter votre expérience de développement.

Si ce comportement pose problème, modifiez les paramètres sous **Outils > Options > Python Tools > Fenêtres interactives** dans le groupe **Mode de saisie semi-automatique**, comme décrit dans [Options - Options des fenêtres interactives](options.md#interactive-windows-options).
