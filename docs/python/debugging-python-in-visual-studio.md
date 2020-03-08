---
title: Déboguer du code Python
description: Visual Studio fournit de riches fonctionnalités de débogage du code Python, y compris la définition de points d’arrêt, l’exécution pas à pas, l’inspection des valeurs, la gestion des exceptions et le débogage dans la fenêtre interactive.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 4678e3508c16b38fec2a10cdeb79bc499eaf15fd
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409983"
---
# <a name="debug-your-python-code"></a>Déboguer votre code Python

Visual Studio offre une expérience de débogage complète pour Python, comprenant notamment l’attachement à des processus en cours d’exécution, l’évaluation d’expressions dans les Fenêtres **Espion** et **Exécution**, l’inspection de variables locales, les points d’arrêt, les instructions de pas à pas détaillé/sortant/principal, la **définition de l’instruction suivante**, etc.

Consultez également les articles ci-après concernant le débogage propre à un scénario :

- [Débogage à distance Linux](debugging-python-code-on-remote-linux-machines.md)
- [Débogage Python/C++ en mode mixte](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symboles de débogage en mode mixte](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python dans Visual Studio prend en charge le débogage sans projet. Après avoir ouvert un fichier Python autonome, cliquez avec le bouton droit dans l’éditeur, puis sélectionnez **Démarrer avec débogage**. Visual Studio lance alors le script avec l’environnement global par défaut (voir [Environnements Python](managing-python-environments-in-visual-studio.md)) sans aucun argument. Mais vous bénéficiez désormais d’une prise en charge complète du débogage.
>
> Pour contrôler l’environnement et les arguments, créez un projet pour le code. Vous pouvez facilement effectuer cette opération à l’aide du modèle de projet [À partir de code Python existant](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files).

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Bases du débogage

Le flux de travail de débogage de base implique la définition de points d’arrêt, l’exécution de code pas à pas, l’inspection de valeurs et la gestion des exceptions, comme décrit dans les sections suivantes.

Une session de débogage est initialisée par la commande **Débogage** > **Démarrer le débogage**, le bouton **Démarrer** de la barre d’outils ou la touche **F5**. Ces opérations lancent le fichier de démarrage de votre projet (indiqué en gras dans **l’Explorateur de solutions**) avec l’environnement actif du projet et tous les arguments de ligne de commande ou chemins de recherche qui ont été spécifiés dans **Propriétés du projet** (consultez la section [Options de débogage d’un projet](#project-debugging-options)). Visual Studio 2017 version 15.6 et ultérieures vous avertit si vous n’avez pas de fichier de démarrage défini ; les versions antérieures peuvent ouvrir une fenêtre de sortie avec l’interpréteur Python en cours d’exécution, ou la fenêtre de sortie s’affiche brièvement et disparaît. Dans tous les cas, cliquez avec le bouton droit sur le fichier approprié et sélectionnez **Définir comme fichier de démarrage**.

> [!Note]
> Le débogueur démarre toujours avec l’environnement Python actif associé au projet. Pour changer d’environnement, activez-en un autre en suivant les instructions de la page [Sélectionner un environnement Python pour un projet](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Points d’arrêt

Les points d’arrêt arrêtent l’exécution du code au niveau d’un point marqué, ce qui vous permet d’inspecter l’état du programme. Pour définir des points d’arrêt, cliquez dans la marge gauche de l’éditeur de code ou cliquez avec le bouton droit sur une ligne de code et sélectionnez **Point d’arrêt** > **Insérer un point d’arrêt**. Un point rouge apparaît sur chaque ligne comportant un point d’arrêt.

![Points d’arrêt qui apparaissent dans Visual Studio](media/debugging-breakpoints.png)

Pour supprimer un point d’arrêt, cliquez sur le point rouge, ou cliquez avec le bouton droit sur la ligne de code et sélectionnez **Point d’arrêt** > **Supprimer le point d’arrêt**. Vous pouvez également désactiver le point d’arrêt sans le supprimer en utilisant la commande **Point d’arrêt** > **Désactiver le point d’arrêt**.

> [!Note]
> Certains points d’arrêt dans Python peuvent surprendre les développeurs habitués à d’autres langages de programmation. Dans Python, l’intégralité du fichier correspond à du code exécutable, de sorte que Python exécute le fichier lorsqu’il est chargé pour traiter n’importe quelle définition de fonction ou de classe de niveau supérieur. Si un point d’arrêt a été défini, il est possible que le débogueur marque un arrêt à mi-chemin d’une déclaration de classe. Même s’il peut sembler surprenant, ce comportement est correct.

Vous pouvez personnaliser les conditions de déclenchement d’un point d’arrêt, par exemple en demandant l’arrêt uniquement quand une variable est définie sur une certaine valeur ou plage de valeurs. Pour définir des conditions, cliquez avec le bouton droit sur le point rouge du point d’arrêt, sélectionnez **Condition**, puis créez des expressions à l’aide d’un code Python. Pour plus d’informations sur cette fonctionnalité dans Visual Studio, consultez la section [Conditions de point d’arrêt](../debugger/using-breakpoints.md#breakpoint-conditions).

Lorsque vous définissez des conditions, vous pouvez également définir **Action** et créer un message à consigner dans la fenêtre de sortie, tout en demandant éventuellement la poursuite automatique de l’exécution. La journalisation d’un message crée un *point de trace* sans l’ajout d’un code de journalisation directement dans votre application :

![Création d’un point de trace avec un point d’arrêt](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Exécuter le code pas à pas

Une fois arrêté au niveau d’un point d’arrêt, vous disposez de différentes méthodes pour exécuter le code pas à pas ou pour exécuter des blocs de code avant de marquer un nouvel arrêt. Ces commandes sont disponibles à divers emplacements, notamment la barre d’outils de débogage supérieure, le menu **Débogage**, le menu contextuel dans l’éditeur de code et certains raccourcis clavier (même si certaines de ces commandes ne sont pas disponibles à tous ces emplacements) :

| Fonctionnalité | Séquence de touches | Description |
| --- | --- | --- |
| **Continuer** | **F5** | Exécute le code jusqu’au point d’arrêt suivant. |
| **Pas à pas détaillé** | **F11** | Exécute l’instruction suivante et s’arrête. Si l’instruction suivante correspond à l’appel d’une fonction, le débogueur s’arrête à la première ligne de la fonction appelée. |
| **Pas à pas principal** | **F10** | Exécute l’instruction suivante, y compris l’appel d’une fonction (en exécutant la totalité de son code) et l’application de toute valeur renvoyée. Le mode pas à pas principal vous permet d’ignorer facilement les fonctions que vous n’avez pas besoin de déboguer. |
| **Pas à pas sortant** | **Maj**+**F11** | Exécute le code jusqu’à la fin de la fonction actuelle, puis procède à une exécution pas à pas jusqu’à l’instruction appelante.  Cette commande est utile quand vous n’avez pas besoin de déboguer le reste de la fonction actuelle. |
| **Exécuter jusqu’au curseur** | **Ctrl**+**F10** | Exécute le code jusqu’à l’emplacement du signe insertion dans l’éditeur. Cette commande vous permet d’ignorer facilement un segment de code que vous n’avez pas besoin de déboguer. |
| **Définir l’instruction suivante** | **Ctrl**+**Maj**+**F10** | Redéfinit le point d’exécution actuel dans le code sur l’emplacement du signe insertion. Cette commande vous permet d’omettre totalement l’exécution d’un segment de code donné, par exemple quand vous savez que le code est défectueux ou qu’il produit un effet indésirable. |
| **Afficher l'instruction suivante** | **Alt**+**num** **&#42;**| Vous renvoie à la prochaine instruction à exécuter. Cette commande est utile si vous avez parcouru votre code et que vous ne vous souvenez pas de l’endroit où le débogueur s’est arrêté. |

### <a name="inspect-and-modify-values"></a>Inspecter et modifier les valeurs

Lorsque vous êtes arrêté dans le débogueur, vous pouvez inspecter et modifier les valeurs des variables. Vous pouvez également utiliser la Fenêtre **Espion** pour surveiller des variables spécifiques, ainsi que des expressions personnalisées. (Pour obtenir des informations générales, consultez la section [Inspect Variables](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) (Inspecter des variables).)

Pour visualiser une valeur à l’aide des **DataTips**, il vous suffit de positionner le pointeur de la souris sur une variable quelconque dans l’éditeur. Vous pouvez alors cliquer sur cette valeur si vous souhaitez la modifier :

![DataTips affichés dans le débogueur Visual Studio](media/debugging-quick-tips.png)

La fenêtre **Automatique** (**Débogage** > **Fenêtres** > **Automatique**) contient les variables et expressions qui sont proches de l’instruction actuelle. Vous pouvez double-cliquer sur la colonne Valeur ou sélectionner une valeur et appuyer sur **F2** pour la modifier :

![Fenêtre Automatique dans le débogueur Visual Studio](media/debugging-autos-window.png)

La fenêtre **Variables locales** (**Débogage** > **Fenêtres** > **Variables locales**) affiche toutes les variables qui se trouvent dans la portée actuelle et que vous pouvez modifier :

![Fenêtre Variables locales dans le débogueur Visual Studio](media/debugging-locals-window.png)

Pour plus d’informations sur l’utilisation des fenêtres **Automatique** et **Variables locales**, consultez l’article [Inspecter les variables dans les fenêtres Automatique et Variables locales](../debugger/autos-and-locals-windows.md).

Les Fenêtres **Espion** (**Débogage** > **Fenêtres** > **Espion** > **Espion 1-4**) vous permettent d’entrer des expressions Python arbitraires et d’en visualiser les résultats. Les expressions sont réévaluées pour chaque étape :

![Fenêtre Espion dans le débogueur Visual Studio](media/debugging-watch-window.png)

Pour plus d’informations sur l’utilisation de la fonctionnalité **Espion**, consultez l’article [Définir un espion sur les variables à l’aide des Fenêtres Espion et Espion express](../debugger/watch-and-quickwatch-windows.md).

Pendant l’inspection d’une valeur de chaîne (`str`, `unicode`, `bytes` et `bytearray` sont toutes considérées comme des chaînes dans ce but), une icône Loupe apparaît à droite de la valeur. Quand vous cliquez sur l’icône, la valeur de chaîne sans guillemets s’affiche dans une boîte de dialogue contextuelle, avec retour à la ligne et défilement, ce qui est utile pour les chaînes longues. En outre, la sélection de la flèche déroulante vers le bas en regard de l’icône vous permet de sélectionner des visualisations aux formats texte brut, HTML, XML et JSON :

![Visualiseurs de chaîne dans le débogueur Visual Studio](media/debugging-string-visualizers.png)

Les visualisations HTML, XML et JSON apparaissent dans des fenêtres contextuelles distinctes avec des arborescences et mise en surbrillance de la syntaxe.

### <a name="exceptions"></a>Exceptions

Si une erreur survient dans votre programme lors du débogage, mais que vous ne disposez pas d’un gestionnaire d’exceptions à cet effet, le débogueur s’arrête au niveau de l’exception :

![Fenêtre contextuelle d’exceptions dans le débogueur Visual Studio](media/debugging-exception-popup.png)

À ce stade, vous pouvez inspecter l’état du programme, y compris la pile des appels. Toutefois, si vous essayez d’exécuter le code pas à pas, l’exception continue d’être levée jusqu’à ce qu’elle soit gérée ou que votre programme se ferme.

La commande de menu **Débogage** > **Fenêtres** > **Paramètres d’exception** affiche une fenêtre vous permettant de développer **Python Exceptions** (Exceptions Python) :

![Fenêtre d’exceptions dans le débogueur Visual Studio](media/debugging-exception-settings.png)

La case à cocher de chaque exception détermine si le débogueur s’arrête *systématiquement* lorsque l’exception est déclenchée. Cochez cette case si vous souhaitez que le débogueur s’arrête plus souvent pour une exception spécifique.

Par défaut, le débogueur s’arrête pour la plupart des exceptions quand aucun gestionnaire d’exceptions ne figure dans le code source. Pour modifier ce comportement, cliquez avec le bouton droit sur une exception et modifiez l’option **Continuer en cas d’exception non gérée dans le code utilisateur**. Si vous préférez que le débogueur s’arrête moins souvent pour une exception donnée, décochez cette case.

Pour configurer une exception absente de cette liste, ajoutez-la en cliquant sur le bouton **Ajouter**. Indiquez un nom correspondant au nom complet de l’exception.

## <a name="project-debugging-options"></a>Options de débogage d’un projet

Par défaut, le débogueur démarre votre programme avec le lanceur Python standard, sans aucun argument de ligne de commande et aucun autre chemin d’accès ni condition spéciaux. Les options de démarrage sont modifiées par le biais des propriétés de débogage du projet accessibles en cliquant avec le bouton droit sur votre projet dans **l’Explorateur de solutions**, en sélectionnant **Propriétés**, puis l’onglet **Débogage**.

![Propriétés de débogage du projet dans le débogueur Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Options du mode de lancement

| Option | Description |
| --- | --- |
| **Lanceur Python standard** | Utilise le code de débogage écrit en Python portable qui est compatible avec CPython, IronPython et des variantes telles que Python Stackless. Cette option offre la meilleure expérience en matière de débogage de code Python pure. Quand vous effectuez un attachement à un processus *python.exe* en cours d’exécution, ce lanceur est utilisé. Ce lanceur fournit également un [débogage en mode mixte](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) pour CPython, ce qui vous permet d’exécuter un pas à pas détaillé alternant en toute transparence entre du code C/C++ et du code Python. |
| **Lanceur web** | Démarre votre navigateur par défaut au lancement et active le débogage des modèles. Pour plus d’informations, consultez la section consacrée au [débogage de modèles web](python-web-application-project-templates.md#debugging). |
| **Lanceur web Django** | Identique au lanceur web et uniquement affiché pour des raisons de compatibilité descendante. |
| **Lanceur IronPython (.NET)** | Utilise le débogueur .NET, qui fonctionne uniquement avec IronPython, mais autorise l’exécution d’un pas à pas détaillé sur n’importe quel projet en langage .NET, y compris C# et VB. Ce lanceur est utilisé si vous effectuez un attachement à un processus .NET en cours d’exécution hébergeant IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Options d’exécution (chemins de recherche, arguments de démarrage et variables d’environnement)

| Option | Description |
| --- | --- |
| **Chemins de recherche** | Ces valeurs correspondent à celles qui apparaissent dans le nœud **Chemins de recherche** du projet dans l’**Explorateur de solutions**. Vous pouvez modifier cette valeur à cet emplacement, mais il est plus facile d’utiliser **l’Explorateur de solutions** qui vous permet de parcourir les dossiers et convertit automatiquement les chemins sous leur forme relative. |
| **Arguments de script** | Ces arguments sont ajoutés à la commande utilisée pour lancer votre script, apparaissant après le nom de fichier du script. Le premier argument spécifié à cet emplacement est disponible pour votre script sous la forme `sys.argv[1]`, le deuxième argument apparaît sous la forme `sys.argv[2]`, etc. |
| **Arguments d’interpréteur** | Ces arguments sont ajoutés à la ligne de commande du lanceur avant le nom de votre script. Les arguments couramment indiqués à cet emplacement sont `-W ...` pour contrôler les avertissements, `-O` pour optimiser légèrement votre programme et `-u` pour utiliser des E/S non mises en mémoire tampon. Les utilisateurs IronPython utilisent généralement ce champ pour transmettre des options `-X`, telles que `-X:Frames` ou `-X:MTA`. |
| **Chemin d’interpréteur** | Remplace le chemin d’accès associé à l’environnement actuel. La valeur peut être utile pour lancer votre script avec un interpréteur non standard. |
| **Variables d’environnement** | Dans cette zone de texte multiligne, ajoutez des entrées sous la forme \<NOM>=\<VALEUR>. Dans la mesure où ce paramètre est appliqué en dernier, après toutes les variables d’environnement globales existantes et après avoir défini `PYTHONPATH` en fonction du paramètre **Chemins de recherche**, vous pouvez l’utiliser pour remplacer manuellement ces autres variables. |

## <a name="immediate-and-interactive-windows"></a>Fenêtres Exécution et Interactive

Dans le cadre d’une session de débogage, vous pouvez utiliser deux fenêtres interactives : la fenêtre **Exécution** Visual Studio standard et la fenêtre **interactive de débogage Python**.

La fenêtre **Exécution** (**Débogage** > **Fenêtres** > **Exécution**) est utilisée pour une évaluation rapide des expressions Python et pour l’inspection ou l’affectation de variables au sein du programme en cours d’exécution. Pour plus d’informations, consultez l’article général [Fenêtre Exécution](../ide/reference/immediate-window.md).

La **fenêtre interactive de débogage Python** (**Débogage** > **Fenêtres** > **Fenêtre interactive de débogage Python**) est plus élaborée, car elle offre une expérience [REPL interactive](python-interactive-repl-in-visual-studio.md) complète au cours du débogage, notamment pour l’écriture et l’exécution de code. Elle se connecte automatiquement à tout processus démarré dans le débogueur à l’aide du lanceur Python standard (dont les processus attachés par le biais de la commande **Débogage** > **Attacher au processus**). Toutefois, cette fenêtre n’est pas disponible en cas d’utilisation du débogage C/C++ en mode mixte.

![Fenêtre de débogage Python interactive](media/debugging-interactive.png)

Outre les **commandes REPL standard**, la fenêtre de [débogage interactive](python-interactive-repl-in-visual-studio.md#meta-commands) prend en charge des méta commandes spéciales :

| Commande | Arguments | Description |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Démarre l’exécution du programme à partir de l’instruction actuelle. |
| `$down`, `$d` | Abaisse le frame actuel d’un niveau dans la trace de la pile. |
| `$frame` | | Affiche l’ID du frame actuel.
| `$frame` | frame id | Remplace le frame actuel par l’ID de frame spécifié.
| `$load` | Charge les commandes d’un fichier et s’exécute jusqu’à la fin. |
| `$proc` |  | Affiche l’ID du processus actuel. |
| `$proc` | process id | Remplace le processus actuel par l’ID de processus spécifié. |
| `$procs` | | Répertorie les processus en cours de débogage. |
| `$stepin`, `$step`, `$s` | Effectue un pas à pas détaillé dans l'appel de fonction suivant, si possible. |
| `$stepout`, `$return`, `$r` | Sort de la fonction active. |
| `$stepover`, `$until`, `$unt` | Passe à l'appel de fonction suivant. |
| `$thread` | | Affiche l’ID du thread actuel. |
| `$thread` | thread ID | Remplace le thread actuel par l’ID de thread spécifié. |
| `$threads` | | Répertorie les threads en cours de débogage. |
| `$up`, `$u` | | Remonte le frame actuel d’un niveau dans la trace de la pile. |
| `$where`, `$w`, `$bt` | Répertorie les frames du thread actuel. |

Notez que les fenêtres du débogueur standard telles que **Processus**, **Threads** et **Pile des appels** ne sont pas synchronisées avec la **Fenêtre interactive de débogage**. La modification du processus, du thread ou du frame actifs dans la **fenêtre interactive de débogage** n’affecte pas les autres fenêtres du débogueur. De même, la modification du processus, du thread ou du frame actifs dans les autres fenêtres du débogueur n’affecte pas la **fenêtre interactive de débogage**.

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Utiliser le débogueur hérité

Visual Studio 2017 version 15.8 et les versions ultérieures utilisent un débogueur basé sur ptvsd version 4.1+. Cette version de ptvsd est compatible avec Python 2.7 et Python 3.5+. Si vous utilisez Python 2.6, 3.1 à 3.4, ou IronPython, Visual Studio affiche l’erreur, **Le débogueur ne prend pas en charge cet environnement Python** :

![Le débogueur ne prend pas en charge cette erreur d’environnement Python quand il est utilisé](media/debugging-experimental-incompatible-error.png)

Dans les cas de figure de ce type, vous devez utiliser l’ancien débogueur (ce qui correspond à la valeur par défaut dans Visual Studio 2017 versions 15.7 et antérieures). Sélectionnez la commande de menu **Outils** > **Options**, accédez à **Python** > **Débogage**, puis sélectionnez l’option **Utiliser le débogueur hérité**.

Si vous avez installé une ancienne version de ptvsd dans l’environnement actuel (par exemple une ancienne version 4.0.x ou une version 3.x nécessaire au débogage à distance), Visual Studio peut afficher une erreur ou un avertissement.

L’erreur **Impossible de charger le package du débogueur** s’affiche quand vous avez installé ptvsd 3.x :

![Erreur « Impossible de charger le package du débogueur » durant l’utilisation du débogueur](media/debugging-experimental-version-error.png)

Dans ce cas, sélectionnez **Utiliser le débogueur hérité** pour définir l’option **Utiliser le débogueur hérité**, puis redémarrez le débogueur.

L’avertissement **Le package du débogueur est obsolète** s’affiche quand vous avez installé une ancienne version 4.x de ptvsd :

![Avertissement « Le package du débogueur est obsolète » durant l’utilisation du débogueur](media/debugging-experimental-version-warning.png)

> [!Important]
> Bien que vous puissiez choisir d’ignorer l’avertissement pour certaines versions de ptvsd, Visual Studio peut ne pas fonctionner correctement.

Pour gérer votre installation de ptvsd :

1. Accédez à l’onglet **Packages** de la fenêtre **Environnements Python**.

1. Entrez « ptvsd » dans le champ de recherche, puis examinez la version installée de ptvsd :

    ![Vérification de la version de ptvsd dans la fenêtre Environnements Python](media/debugging-experimental-check-ptvsd.png)

1. Si la version est inférieure à 4.1.1a9 (la version groupée avec Visual Studio), sélectionnez le **X** à droite du package pour désinstaller l’ancienne version. Visual Studio utilise alors sa version groupée. (Vous pouvez également la désinstaller à l’aide de PowerShell via `pip uninstall ptvsd`.)

1. Autre possibilité : vous pouvez mettre à jour le package ptvsd (dernière version) en suivant les instructions de la section [Résolution des problèmes](#troubleshooting).

## <a name="troubleshooting"></a>Dépannage

Si vous rencontrez des problèmes avec le débogueur, commencez par mettre à niveau votre version de ptvsd :

1. Accédez à l’onglet **Packages** de la fenêtre **Environnements Python**.

1. Entrez `ptvsd --upgrade` dans la zone de recherche, puis sélectionnez **Exécuter la commande : pip install ptvsd --upgrade**. (Vous pouvez également utiliser la même commande à partir de PowerShell.)

    ![Commande de mise à niveau ptvsd dans la fenêtre Environnements Python](media/debugging-experimental-upgrade-ptvsd.png)

Si les problèmes persistent, signalez-les dans le [référentiel GitHub PTVS](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Activer la journalisation du débogueur

Au cours d’une enquête sur un problème de débogueur, Microsoft est susceptible de vous demander d’activer et de recueillir les journaux de débogage, qui facilitent le diagnostic.

Les étapes suivantes permettent le débogage dans la session active de Visual Studio :

1. Ouvrez une Fenêtre Commande dans Visual Studio avec la commande de menu **Affichage** > **Autres fenêtres** > **Fenêtre Commande**.

1. Entrez la commande suivante :

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Commencez le débogage et suivez toutes les étapes nécessaires pour reproduire votre problème. Pendant ce temps, les journaux de débogage s’affichent dans la Fenêtre **Sortie** sous **Journaux de l’hôte d’adaptateur de débogage**. Vous pouvez alors copier les journaux de cette fenêtre et les coller dans un problème GitHub, un e-mail, etc.

    ![Sortie de la journalisation du débogueur dans la Fenêtre Sortie](media/debugger-logging-output.png)

1. Si Visual Studio se bloque ou que vous ne parvenez pas à accéder à la Fenêtre **Sortie**, redémarrez Visual Studio, ouvrez une Fenêtre Commande et entrez la commande suivante :

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Commencez le débogage et reproduisez votre problème. Les journaux du débogueur se trouvent dans `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur le débogueur Visual Studio, consultez l’article [Débogage dans Visual Studio](../debugger/debugger-feature-tour.md).
