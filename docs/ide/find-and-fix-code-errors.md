---
title: Corriger les erreurs d’un programme et améliorer le code
description: Cet article décrit certaines fonctionnalités de base de Visual Studio qui peuvent vous aider à trouver et à résoudre les problèmes présents dans votre code, notamment les erreurs de génération, l’analyse du code, les outils de débogage et les tests unitaires.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5af76de5dbcc7a70722acf0ee01cfed93dbad761
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308257"
---
# <a name="make-code-work-in-visual-studio"></a>Faire fonctionner le code dans Visual Studio

Visual Studio intègre un ensemble puissant d’outils de génération et de débogage de projets. Dans cet article, vous découvrez comment Visual Studio peut vous aider à trouver les problèmes présents dans votre code avec la sortie de la génération, l’analyse du code, les outils de débogage et les tests unitaires.

Vous avez compris comment fonctionne l’éditeur et vous venez de créer du code. Vous voulez maintenant vérifier que le code fonctionne correctement. Dans Visual Studio, comme dans la plupart des environnements de développement intégrés (IDE), vérifier le bon fonctionnement du code se fait en deux phases : la génération du code, pour détecter et résoudre les erreurs liées au projet et au compilateur, puis l’exécution du code pour trouver les erreurs dynamiques et d’exécution.

## <a name="build-your-code"></a>Générer votre code

Il existe deux types de base de configurations de build : **Debug** et **Release**. La configuration **Debug** produit un fichier exécutable plus lent et plus grand, qui rend l’expérience de débogage à l’exécution plus riche et interactive. L’exécutable **Debug** ne doit jamais être publié. La configuration **Release** génère un fichier exécutable plus rapide et optimisé, qui peut être livré (au moins du point de vue du compilateur). La configuration de build par défaut est **Debug**.

Le moyen le plus simple de générer votre projet est d’appuyer sur **F7**, mais vous pouvez aussi démarrer la génération en sélectionnant **Générer** > **Générer la solution** dans le menu principal.

![Sélection du menu de génération du projet Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Vous pouvez observer le processus de génération dans la fenêtre **Sortie**, qui se trouve dans la partie inférieure de l’interface utilisateur de Visual Studio. Les erreurs, avertissements et opérations de génération sont affichés ici. Si vous avez des erreurs (ou si vous recevez des avertissements au-delà d’un niveau configuré), votre build échoue. Vous pouvez cliquer sur une erreur ou sur un avertissement pour accéder à la ligne à l'origine du problème. Regénérez votre projet en réappuyant sur **F7** (pour recompiler seulement les fichiers avec des erreurs) ou en appuyant sur **Ctrl**+**Alt**+**F7** (pour une regénération complète).

Vous pouvez voir deux fenêtres à onglets dans la fenêtre de résultats sous l’éditeur : la fenêtre **Sortie**, qui contient la sortie brute du compilateur (notamment les messages d’erreur), et la fenêtre **Liste d’erreurs**, qui fournit une liste de l’ensemble des erreurs et des avertissements, que vous pouvez trier et filtrer.

Quand la build réussit, des résultats similaires à ceux-ci apparaissent dans la fenêtre **Sortie** :

![Sortie de génération réussie Visual Studio](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Examiner la Liste d’erreurs

À moins que vous n’ayez apporté aucune modification au code précédemment compilé avec succès, une erreur s’est probablement produite. Si vous codez depuis peu, il y en a peut-être beaucoup. Si certaines erreurs sont évidentes, comme une simple erreur de syntaxe ou un nom de variable incorrect, d’autres sont parfois plus ardues à comprendre. Et ce n’est pas le code obscur associé à celles-ci qui va davantage vous aider. Pour obtenir une vue plus claire des problèmes, accédez au bas de la fenêtre **sortie** de la génération, puis cliquez sur l’onglet **liste d’erreurs** . Vous accédez ainsi à une vue plus organisée des erreurs et des avertissements pour votre projet et vous offre également des options supplémentaires.

![Sortie et liste d’erreurs de Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Cliquez sur la ligne de l’erreur dans la fenêtre **Liste d’erreurs** pour accéder directement à la ligne où l’erreur s’est produite. (Ou activez les numéros de ligne en appuyant sur **CTRL** + **Q**, en tapant les **numéros de ligne**, puis en choisissant l' **option Activer ou désactiver les numéros de ligne** dans les résultats. C’est le moyen le plus rapide d’obtenir la boîte de dialogue **Options** qui vous permet d’activer les numéros de ligne.)

![Éditeur Visual Studio avec des numéros de ligne](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Option des numéros de ligne Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Appuyez sur **CTRL** + **G** pour accéder rapidement au numéro de ligne où l’erreur s’est produite.

L’erreur est identifiée par un trait de soulignement rouge ondulé. Pointez dessus pour obtenir plus d'informations. Apportez la correction nécessaire pour faire disparaître ce trait. Notez toutefois que vous risquez d'introduire une nouvelle erreur. (Cela s’appelle une « régression ».)

![Pointage d'erreur Visual Studio](../ide/media/vs_ide_gs_debug_error_hover1.png)

Passez en revue la liste d'erreurs et corrigez toutes les erreurs dans votre code.

![Fenêtre d'erreurs de débogage Visual Studio](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Examiner les erreurs en détail

De nombreuses erreurs, exprimées selon les termes du compilateur, peuvent vous paraître incompréhensibles. Dans ces cas-là, vous avez besoin d’informations supplémentaires. Dans la fenêtre **Liste d’erreurs**, vous pouvez effectuer une recherche Bing automatique pour plus d’informations sur l’erreur ou l’avertissement. Cliquez avec le bouton droit sur la ligne d’entrée correspondante, puis sélectionnez **Afficher l’aide sur l’erreur** dans le menu contextuel, ou cliquez sur le lien hypertexte avec la valeur du code d’erreur dans la colonne **Code** de la **Liste d’erreurs**.

![Recherche Bing de liste d'erreurs Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

En fonction de vos paramètres, votre navigateur web affiche les résultats de la recherche pour le code et le texte de l’erreur, ou un onglet s’ouvre dans Visual Studio et montre les résultats de la recherche Bing. Les résultats provenant de sources diverses sur Internet, certains peuvent s'avérer inutiles.

## <a name="use-code-analysis"></a>Utiliser l’analyse du code

Les analyseurs de code recherchent les problèmes de code courants qui peuvent conduire à des erreurs d’exécution ou à des problèmes dans la gestion du code.

### <a name="c-and-visual-basic-code-analysis"></a>Analyse du code C# et Visual Basic

Visual Studio comprend un ensemble prédéfini d’[analyseurs .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) qui examinent le code C# et Visual Basic au fur et à mesure que vous l’écrivez. Vous pouvez installer des analyseurs supplémentaires sous la forme d’une extension Visual Studio ou d’un package NuGet. Si des violations de règle sont détectées, elles sont signalées dans l’Liste d’erreurs et dans l’éditeur de code sous la forme d’un tilde sous le code incriminé.

### <a name="c-code-analysis"></a>Analyse du code C++

Pour analyser du code C++, exécutez une [analyse statique du code](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Prenez l’habitude d’effectuer cette analyse après avoir résolu les erreurs évidentes qui font obstacle à la génération, et consacrez du temps au traitement des avertissements qu’elle peut produire. Cela vous épargnera quelques maux de tête, et vous pouvez même apprendre quelques techniques relatives au style du code.

Appuyez sur **ALT** + **F11** (ou sélectionnez **analyser**  >  **exécuter l’analyse du code sur la solution** dans le menu supérieur) pour démarrer l’analyse statique du code.

![Élément de menu Analyse du code de Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Les avertissements nouveaux ou mis à jour apparaissent sous l’onglet **Liste d’erreurs** dans la partie inférieure de l’IDE. Cliquez sur les avertissements pour accéder à la ligne correspondante dans le code.

![Liste d’erreurs de Visual Studio avec des avertissements](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Utiliser les actions rapides pour corriger ou refactoriser du code

Les [actions rapides](../ide/quick-actions.md), disponibles à partir de l’icône d’ampoule ou de tournevis, permettent de refactoriser le code inline. Elles vous permettent de résoudre facilement et rapidement des avertissements courants dans du code C#, C++ et Visual Basic. Pour y accéder, cliquez avec le bouton droit sur le trait de soulignement ondulé d’un avertissement et sélectionnez **Actions rapides et refactorisations**. Ou, lorsque le curseur se trouve sur la ligne avec le tilde de couleur, appuyez sur **CTRL** + **.** ou sélectionnez l’icône d’ampoule, d’ampoule d’erreur ou de tournevis dans la marge. Vous voyez alors une liste des corrections ou des refactorisations possibles que vous pouvez appliquer à cette ligne de code.

![Aperçu d’une ampoule dans Visual Studio](../ide/media/quick-actions-options.png)

Vous pouvez utiliser des actions rapides là où les analyseurs de code déterminent que votre code peut être corrigé, refactorisé ou amélioré. Cliquez sur n’importe quelle ligne de code, cliquez avec le bouton droit pour ouvrir le menu contextuel, puis sélectionnez **Actions rapides et refactorisations**. Si des options de refactorisation ou d’amélioration sont disponibles, elles sont affichées. Sinon, le message **Aucune action rapide disponible ici** apparaît en bas à gauche de l’IDE.

![Texte « Aucune action rapide disponible »](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Avec l’expérience, vous pouvez rapidement utiliser les touches de direction et **CTRL** + **.** pour vérifier les opportunités de refactorisation simples et nettoyer votre code.

::: moniker range=">=vs-2019"

## <a name="run-code-cleanup"></a>Exécuter le nettoyage du code

Visual Studio fournit la [mise en forme à la demande de votre fichier de code C#](code-styles-and-code-cleanup.md#apply-code-styles), y compris les préférences de style de code, via le bouton **nettoyage de code** en bas de l’éditeur.

![Bouton de nettoyage du code dans Visual Studio 2019](media/execute-code-cleanup.png)

Outre la mise en forme de votre fichier pour les espaces, les retraits et les etc, le **nettoyage du code** applique également un ensemble de conventions de style de code que vous définissez. Vos préférences pour chaque style de code sont lues à partir du [fichier EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), si vous en avez un pour le projet, ou à partir des [paramètres de style de code](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) dans la boîte de dialogue **Options**.

::: moniker-end

## <a name="debug-your-running-code"></a>Déboguer votre code en cours d’exécution

Maintenant que vous avez généré votre code et procédé à quelques tâches de nettoyage, exécutez-le en appuyant sur **F5** ou en sélectionnant **Déboguer** > **Démarrer le débogage**. Votre application démarre dans un environnement de débogage dans lequel vous pouvez observer son comportement en détail. Pendant l’exécution de votre application, l’IDE de Visual Studio subit des modifications. Ainsi, la fenêtre **Sortie** est remplacée par deux nouvelles fenêtres (dans la configuration des fenêtres par défaut) : une fenêtre avec les onglets **Automatique/Variables locales/Espion** et une autre avec les onglets **Pile des appels/Points d’arrêt/Paramètres d’exception/Sortie**. Ces fenêtres ont plusieurs onglets qui vous permettent d’inspecter et d’évaluer les variables, threads, piles d’appels et différents autres comportements de votre application à mesure qu’elle s’exécute.

![Fenêtres Automatique et Pile des appels de Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Arrêtez votre application en appuyant sur **MAJ** + **F5** ou en cliquant sur le bouton **arrêter** . Vous pouvez aussi fermer la fenêtre principale de l’application (ou la boîte de dialogue de ligne de commande).

Si votre code s'exécute parfaitement et exactement comme prévu, félicitations ! Toutefois, s’il cesse de répondre ou s’est bloqué, ou a donné des résultats étranges, vous devez rechercher la source de ces problèmes et résoudre les bogues.

### <a name="set-simple-breakpoints"></a>Définir des points d’arrêt simples

Les [points d’arrêt](../debugger/using-breakpoints.md) constituent la fonctionnalité la plus élémentaire et la plus essentielle pour un débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. Vous n’avez pas besoin de regénérer un projet après avoir défini et supprimé des points d’arrêt.

Définissez un point d’arrêt en cliquant à l’extrémité de la marge de la ligne où vous souhaitez arrêter le code, ou appuyez sur **F9** pour définir un point d’arrêt sur la ligne de code actuelle. Quand vous exécutez votre code, celui-ci s’interrompt (ou *s’arrête*) avant d’exécuter les instructions contenues dans cette ligne de code.

![Point d'arrêt Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Parmi les utilisations courantes des points d'arrêt, citons les suivantes :

- Pour limiter la source d’un programme de blocage ou de non-réponse, vous pouvez faire circuler des points d’arrêt dans le code de l’appel de méthode, ce qui est à l’origine de l’échec. À mesure que vous exécutez le code dans le débogueur, supprimez les points d’arrêt, puis rapprochez-les les uns des autres jusqu’à identifier la ligne de code incriminée. Pour découvrir comment exécuter du code dans le débogueur, consultez la section suivante.

- Quand vous introduisez du nouveau code, définissez un point d’arrêt au début de celui-ci, puis exécutez le code pour vérifier qu’il se comporte comme prévu.

- Si vous avez implémenté un comportement complexe, définissez des points d’arrêt dans le code de l’algorithme, pour pouvoir inspecter les valeurs des variables et des données quand le programme s’arrête.

- Si vous écrivez du code C ou C++, utilisez des points d’arrêt pour arrêter le code pour pouvoir inspecter les valeurs d’adresse (rechercher NULL) et les nombres de références lors du débogage des échecs liés à la mémoire.

Pour plus d’informations sur l’utilisation des points d’arrêt, consultez [Utilisation des points d’arrêt](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Inspecter le code au moment de l’exécution

Quand votre code atteint un point d’arrêt et s’interrompt, la ligne de code marquée en jaune (l’instruction en cours) n’a pas encore été exécutée. À ce stade, vous souhaiterez peut-être exécuter l’instruction en cours, puis inspecter les valeurs modifiées. Vous pouvez utiliser plusieurs commandes d’analyse *pas à pas* pour exécuter le code dans le débogueur. Si le code marqué est un appel de méthode, vous pouvez effectuer un pas à pas détaillé en appuyant sur **F11**. Vous pouvez également *exécuter pas à pas* la ligne de code en appuyant sur **F10**. Pour plus d’informations sur les commandes supplémentaires et sur la façon de parcourir le code, consultez [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

![Capture d’écran de la fenêtre de Visual Studio code. Un point rouge dans la marge de gauche indique un point d’arrêt sur la ligne de code marquée en jaune.](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Dans l’illustration précédente, vous pouvez avancer d’une instruction dans le débogueur en appuyant sur **F10** ou **F11** (comme il n’y a ici aucun appel de méthode, les deux commandes ont le même résultat).

Quand le débogueur est suspendu, vous pouvez inspecter les variables et les piles des appels pour déterminer ce qui se passe. Les valeurs sont-elles comprises dans les plages attendues ? Les appels sont-ils effectués dans le bon ordre ?

![Capture d’écran de la fenêtre de Visual Studio code. À la ligne de code marquée en jaune, une variable est sélectionnée et une liste déroulante affiche sa valeur actuelle et ses références.](../ide/media/vs_ide_gs_debug_inspect_value.png)

Placez le curseur sur une variable pour voir sa valeur actuelle et ses références. Si vous remarquez une valeur inattendue, vous avez probablement un bogue dans les lignes de code précédentes ou dans le code appelant. Pour plus d’informations sur le débogage, consultez [cet article](../debugger/debugger-feature-tour.md) sur l’utilisation du débogueur.

Par ailleurs, Visual Studio affiche la fenêtre **Outils de diagnostic**. Celle-ci vous permet d’observer l’utilisation au fil du temps de l’UC et de la mémoire par votre application. Ultérieurement lors du développement de vos applications, vous pourrez utiliser ces outils pour rechercher les utilisations du processeur ou les allocations de mémoire importantes et imprévues. Utilisez-les conjointement avec la fenêtre **Espion** et les points d’arrêt pour déterminer le problème à l’origine d’une utilisation élevée inattendue ou de la non-libération de ressources. Pour plus d’informations, consultez [Visite guidée des fonctionnalités de profilage](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

Les tests unitaires sont votre première ligne de défense contre les bogues du code car, exécutés correctement, ils testent une seule « unité » de code, généralement une seule fonction, et leur débogage est généralement plus facile que celui du programme complet. Visual Studio installe les infrastructures de tests unitaires Microsoft pour le code managé et le code natif. Utilisez une infrastructure de test unitaire pour créer des tests unitaires, les exécuter et signaler les résultats de ces tests. Réexécutez les tests unitaires quand vous apportez des modifications pour vérifier que votre code fonctionne toujours correctement. Avec Visual Studio Enterprise Edition, vous pouvez exécuter automatiquement des tests après chaque build.

Pour commencer, consultez [Générer des tests unitaires pour votre code avec IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Pour plus d’informations sur les tests unitaires dans Visual Studio et comment ils peuvent vous aider à créer du code de meilleure qualité, consultez [Concepts de base des tests unitaires](../test/unit-test-basics.md).

## <a name="see-also"></a>Voir aussi

- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [En savoir plus sur l’utilisation du débogueur](../debugger/index.yml)
- [Générer et corriger du code](../ide/code-generation-in-visual-studio.md)
