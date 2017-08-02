---
title: Boucle REPL interactive Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: ca444dbe9fea25b205ae2060d462f23957368496
ms.lasthandoff: 04/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>Utilisation de la fenêtre interactive Python

Visual Studio intègre une fenêtre REPL (read-evaluate-print loop) interactive pour chacun de vos environnements Python, qui améliore la boucle REPL que vous obtenez avec `python.exe` sur la ligne de commande. La fenêtre interactive (accessible depuis les commandes de menu **View (Affichage) > Other Windows (Autres fenêtres) > &lt;environnement&gt; Interactive (Interactif)** vous permet d’entrer du code Python arbitraire et de voir immédiatement les résultats pour vous aider à apprendre et à tester des API, mais aussi à développer de manière interactive du code opérationnel à inclure dans vos projets.

![Fenêtre interactive Python](~/docs/python/media/interactive-window.png)

Visual Studio propose plusieurs modes REPL Python au choix :

| REPL | Description | Modification | Débogage | Images |
| --- | --- | --- | --- | --- |
| Standard | REPL par défaut, communique directement avec Python | Modification standard (multiligne, etc.). | Oui, via `$attach` | Non |
| Débogage | REPL par défaut, communique avec le processus Python débogué | Modification standard | Débogage uniquement | Non |
| IPython | REPL qui communique avec le serveur principal IPython | Commandes IPython, avantages de Pylab | Non | Oui, inline dans REPL |
| IPython sans Pylab | REPL qui communique avec le serveur principal IPython | IPython standard | Non | Oui, fenêtre distincte | 

Cette rubrique décrit les modes REPL **Standard** et **Débogage**. Pour plus d’informations sur les modes IPython, consultez [Using the IPython REPL](interactive-repl-ipython.md) (Utilisation de la boucle REPL IPython).

Pour une présentation de la fenêtre interactive Python, visionnez la vidéo [Getting Started with Python in Visual Studio, Part 5: Interactive REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Prise en main de Python dans Visual Studio, Partie 5 : REPL interactive) (youtube.com, 2 minutes 51 secondes).

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>Ouverture d’une fenêtre interactive

Il existe plusieurs manières d’ouvrir la fenêtre interactive pour un environnement.

Tout d’abord, basculez vers la fenêtre des environnements Python (**View > Other Windows > Python Environments** (Affichage > Autres fenêtres > Environnements Python) ou Ctrl-K, Ctrl-`) et sélectionnez la commande ou le bouton **Open Interactive Window** (Ouvrir une fenêtre interactive) pour l’environnement choisi.

![Lien vers la fenêtre interactive dans la fenêtre des environnements Python](~/docs/python/media/interactive-window-opening.png)

Le menu **View > Other Windows** (Affichage > Autres fenêtres) comporte des commandes **interactives** pour chacun de vos environnements, généralement affichées en bas du menu :

![Éléments de menu de la fenêtre interactive dans View > Other Windows (Affichage > Autres fenêtres)](~/docs/python/media/interactive-window-menu.png)

Vous pouvez ouvrir une fenêtre interactive sur le fichier de démarrage dans votre projet, ou pour un fichier autonome, en sélectionnant **Debug > Execute [Project | File] (Déboguer > Exécuter [Projet | Fichier] dans la commande de menu Python Interactive** (Maj + Alt + F5) :

![Exécution du projet dans le menu Python Interactive](~/docs/python/media/interactive-execute-project.png)

Enfin, vous pouvez sélectionner un code dans un fichier et utiliser la [commande d’envoi de code vers la fenêtre interactive](#send-code-to-interactive-command) décrite ci-dessous.

## <a name="interactive-window-options"></a>Options de la fenêtre interactive

Vous pouvez contrôler divers aspects de la fenêtre interactive via la commande **Configure interactive window** (Configurer la fenêtre interactive) dans la fenêtre des environnements Python, ou via le menu **Tools > Options > Python Tools > Interactive Windows** (Outils > Options > Outils Python > Fenêtres interactives) :

![Options de la fenêtre interactive Python](media/interactive-window-options.png)

Notez qu’il existe également un autre ensemble d’options pour la commande **Debug Interactive Window** (Déboguer la fenêtre Interactive), qui contrôlent le comportement pendant une session de débogage :

![Options de débogage de la fenêtre interactive Python](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>Utilisation de la fenêtre interactive

Une fois que la fenêtre interactive est ouverte, vous pouvez commencer à entrer du code ligne par ligne à l’invite `>>>`. La fenêtre interactive exécute chaque ligne que vous entrez, qui comprend l’importation de modules, la définition de variables, etc. Vous pouvez le voir dans les deux premières lignes indiquées dans l’illustration ci-dessous :

![Fenêtre interactive Python](~/docs/python/media/interactive-window.png)

La fenêtre interactive se comporte différemment lorsqu’une instruction se termine par un signe deux-points, comme dans l’instruction `for` ci-dessus, car elle sait qu’elle a besoin de lignes de code supplémentaires pour pouvoir exécuter correctement le bloc de code. Dans ce cas, l’invite de ligne affiche `...` pour vous signaler que vous devez saisir des lignes supplémentaires pour le bloc, comme illustré sur les quatrième et cinquième lignes de la capture ci-dessus. Lorsque vous appuyez sur Entrée sur une ligne vide, la fenêtre interactive ferme le bloc et l’exécute dans l’interpréteur.

> [!Tip]
> La fenêtre interactive améliore l’expérience habituelle de la fonctionnalité REPL de la ligne de commande Python en mettant automatiquement en retrait les instructions attachées à une portée voisine. Son historique (rappelé avec la flèche vers le haut) fournit également des éléments multilignes, tandis que la fonctionnalité REPL de la ligne de commande fournit uniquement des lignes uniques.

La fenêtre interactive est un excellent moyen de tester une nouvelle bibliothèque. Vous pouvez importer la bibliothèque et inspecter les sous-packages, classes et fonctions.  Pour obtenir toutes ces informations, utilisez la fonction `help()` de Python.  La prise en charge de Python dans Visual Studio vous donne également des suggestions et de la documentation basées sur la modélisation de code utilisée dans l’éditeur, et ce sans même exécuter la bibliothèque.  Quand vous exécutez du code, Visual Studio utilise les informations du runtime Python pour améliorer ces suggestions.  

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

Les commandes sont également extensibles à l’aide de MEF (Managed Extensibility Framework pour .NET).

## <a name="switching-scopes"></a>Changement de portées

Par défaut, la fenêtre interactive d’un projet est limitée au fichier de démarrage du projet comme si vous l’aviez exécuté à partir de l’invite de commandes. Pour un fichier autonome, elle se limite à ce fichier. Vous pouvez cependant modifier la portée à tout moment pendant votre session REPL à l’aide du menu déroulant situé en haut de la fenêtre interactive :

![Portées de la fenêtre interactive](~/docs/python/media/interactive-scopes.png)

Une fois que vous importez un module, par exemple en tapant `import os`, vous obtenez dans la liste déroulante des options permettant de basculer vers n’importe quelle portée de ce module. Vous voyez également dans la fenêtre interactive un message indiquant la nouvelle portée, ce qui vous permet de savoir comment vous avez atteint un état donné au cours de votre session.

Si vous entrez `dir()` dans une portée, vous obtenez les identificateurs valides dans cette portée, notamment les noms des fonctions, les classes et les variables. Par exemple, si vous utilisez `$mod importlib` suivi de `dir()`, vous obtenez les informations suivantes :

![Fenêtre interactive dans la portée importlib](~/docs/python/media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>Envoi de code à la commande interactive

En plus de pouvoir travailler directement dans la fenêtre interactive, vous pouvez sélectionner du code dans l’éditeur, cliquer avec le bouton droit, puis choisir **Envoyer vers Interactive** :

![Commande de menu Envoyer vers Interactive](~/docs/python/media/interactive-send-to.png)

Cette commande est utile dans le cadre du développement de code itératif ou évolutionnaire, car elle permet notamment de tester votre code à mesure que vous le développez. Par exemple, une fois que vous avez envoyé un élément de code dans la fenêtre interactive et que vous avez vu sa sortie, vous pouvez appuyer sur la flèche du bas pour afficher de nouveau le code, le modifier et le tester rapidement à l’aide des touches Ctrl + Entrée. (Appuyez sur Entrée à la fin d'une entrée pour l’exécuter, ou appuyez sur Entrée au milieu d'une entrée pour insérer une nouvelle ligne.) Une fois que vous obtenez le code que vous souhaitez, vous pouvez facilement le copier dans votre fichier projet.

Vous pouvez également sélectionner le code, cliquer dessus avec le bouton droit, puis sélectionner **Send to Defining Module** (Envoyer vers le module de définition) pour rechercher dans le processus interactif le module qui correspond au fichier en cours de modification. Si la commande trouve le module correct, elle utilise la métacommande `$mod` pour basculer vers ce module (qui est alors intégré dans l’historique de session de la fenêtre interactive) et coller la sélection dans la fenêtre interactive afin de l’évaluer. Ceci permet d’accélérer le processus qui consiste à copier du code dans l’éditeur, à changer de portée dans la fenêtre interactive et à coller manuellement la sélection.

## <a name="intellisense-behavior"></a>Comportement IntelliSense

La fenêtre interactive inclut la fonctionnalité IntelliSense basée sur les objets dynamiques, contrairement à l’éditeur de code dans lequel la fonctionnalité IntelliSense repose uniquement sur l’analyse du code source. Ceci permet d’afficher dans la fenêtre interactive des suggestions plus appropriées, en particulier avec un code généré dynamiquement. L’inconvénient est que les fonctions qui comportent des effets secondaires (par exemple la journalisation des messages) peuvent affecter votre expérience de développement.

Si cela pose problème, modifiez les paramètres sous **Tools > Options > Python Tools > Interactive Windows** (Outils > Options > Outils Python > Fenêtres interactives), dans le groupe **Completion Mode** (Mode de saisie semi-automatique) :

- **Never evaluate expressions** (Ne jamais évaluer les expressions) : utilise le moteur IntelliSense normal pour formuler des suggestions.
- **Never evaluate expressions containing calls** (Ne jamais évaluer les expressions contenant des appels) (par défaut) : les expressions simples telles que `a.b` sont évaluées, mais les expressions impliquant des appels, telles que `a().b`, utilisent le moteur normal.
- **Always evaluate expressions** (Toujours évaluer les expressions) : exécute l’expression complète pour obtenir des suggestions, indépendamment des risques d’effets secondaires.
