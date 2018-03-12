---
title: "Bien démarrer avec le débogage dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c75b5508cd23a2131bcdd64cf52aacc1486d2713
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="get-started-with-debugging-in-visual-studio"></a>Bien démarrer avec le débogage dans Visual Studio
Visual Studio intègre un ensemble puissant d’outils de génération et de débogage de projets. Dans cette rubrique, vous allez apprendre à utiliser l’ensemble des fonctionnalités de base de l’interface utilisateur de débogage.  

## <a name="my-code-doesnt-work-help-me-visual-studio"></a>Mon code ne fonctionne pas. Comment obtenir de l’aide dans Visual Studio ?  
 Vous avez compris comment fonctionne l’éditeur et vous venez de créer du code. Vous devez à présent déboguer ce code. Dans Visual Studio, comme dans la plupart des environnements de développement intégrés (IDE), le débogage comprend deux phases : la génération du code pour intercepter et résoudre les erreurs liées au projet et au compilateur, puis l’exécution du code dans l’environnement pour intercepter et résoudre les erreurs dynamiques et d’exécution.  

### <a name="build-your-code"></a>Générer votre code  
 Il existe deux types de base de configurations de build : **Debug** et **Release**. La première configuration produit un fichier exécutable plus volumineux et moins rapide. S'il ne doit jamais être publié, il rend l'expérience de débogage à l'exécution plus riche et interactive. La seconde configuration génère un fichier exécutable plus rapide et optimisé qu’il est possible de publier (tout du moins du point de vue du compilateur). La configuration de build par défaut est **Debug**.

Le moyen le plus simple de générer votre projet consiste à appuyer sur **F7**, mais vous pouvez aussi démarrer la build en sélectionnant **Générer > Générer la solution** dans le menu principal.  

 ![Sélection du menu de génération du projet Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png "Vs_ide_gs_debug_build_menu_item")  

 Vous pouvez observer le processus de génération dans la fenêtre d’état **Sortie** située dans la partie inférieure de l’interface utilisateur de Visual Studio. Les erreurs, avertissements et opérations de génération sont affichés ici. En cas d'erreurs (ou si vous recevez des avertissements au-delà d'un niveau configuré), votre build échoue. Vous pouvez cliquer sur une erreur ou sur un avertissement pour accéder à la ligne à l'origine du problème. Régénérez votre projet. Pour cela, appuyez sur **F7** (pour recompiler uniquement les fichiers avec des erreurs) ou sur **Ctrl+Alt+F7** (pour une nouvelle régénération complète).  

 Deux fenêtres à onglets apparaissent dans la fenêtre de résultats sous l’éditeur : la fenêtre **Sortie**, qui contient la sortie brute du compilateur (y compris les messages d’erreur), et la fenêtre **Liste d’erreurs**, qui fournit une liste pouvant être triée et filtrée de l’ensemble des erreurs et des avertissements.  

 En cas de réussite, des résultats semblable à ceux-ci apparaissent dans la fenêtre **Sortie**.  

 ![Sortie de génération réussie Visual Studio](../ide/media/vs_ide_gs_debug_success_build.PNG "vs_ide_gs_debug_success_build")  

### <a name="review-the-error-list"></a>Examiner la Liste d’erreurs  
 À moins que vous n’ayez apporté aucune modification au code précédemment compilé avec succès, une erreur s’est probablement produite. Si vous codez depuis peu, il y en a peut-être beaucoup. Si certaines erreurs sont évidentes, comme une simple erreur de syntaxe ou un nom de variable incorrect, d’autres sont parfois plus ardues à comprendre. Et ce n’est pas le code obscur associé à celles-ci qui va davantage vous aider. Pour obtenir une vue plus conviviale des problèmes, accédez à la partie inférieure de la fenêtre **Sortie** de la build, puis cliquez sur l’onglet **Liste d’erreurs**. Vous disposez non seulement d'une vue mieux organisée des erreurs et des avertissements liés à votre projet, mais aussi d'options supplémentaires.  

 ![Liste d’erreurs et sortie de Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.PNG "Vs_ide_gs_debug_bad_build_error_list")  

 Cliquez sur la ligne d’erreur dans la fenêtre **Liste d’erreurs** pour accéder directement à la ligne à l’origine de l’erreur. (Vous pouvez aussi activer les numéros de ligne en cliquant dans la barre **Lancement rapide** située dans l’angle supérieur droit, en tapant « numéros de ligne » dans celle-ci, puis en appuyant sur Entrée. C’est le moyen le plus rapide d’arriver à l’entrée de la fenêtre **Options** qui vous permet d’activer les numéros de ligne. En vous familiarisant avec la barre **Lancement rapide**, vous économiserez un grand nombre de clics dans l’interface utilisateur !)  

 ![Éditeur Visual Studio avec des numéros de ligne](../ide/media/vs_ide_gs_debug_line_numbers.png "Vs_ide_gs_debug_line_numbers")  

 ![Option des numéros de ligne Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png "Vs_ide_gs_debug_options_line_numbers")  

 Utilisez **Ctrl+G** pour accéder rapidement au numéro de ligne où l’erreur s’est produite.  

 L’erreur est identifiée par un trait de soulignement rouge ondulé. Pointez dessus pour obtenir plus d'informations. Apportez la correction nécessaire pour faire disparaître ce trait. Notez toutefois que vous risquez d'introduire une nouvelle erreur. (Cela s’appelle une « régression ».)  

 ![Pointage d’erreur Visual Studio](../ide/media/vs_ide_gs_debug_error_hover1.png "Vs_ide_gs_debug_error_hover1")  

 Passez en revue la liste d'erreurs et corrigez toutes les erreurs dans votre code.  

 ![Fenêtre d’erreurs de débogage Visual Studio](../ide/media/vs_ide_gs_debug_error_list.PNG "Vs_ide_gs_debug_error_list")  

### <a name="review-errors-in-detail"></a>Examiner les erreurs en détail  
 De nombreuses erreurs, exprimées selon les termes du compilateur, peuvent vous paraître incompréhensibles. Dans ces cas-là, vous avez besoin d'informations supplémentaires. La fenêtre **Liste d’erreurs** vous permet de lancer une recherche automatique dans Bing pour obtenir plus d’informations sur l’erreur (ou l’avertissement). Pour cela, cliquez avec le bouton droit sur la ligne d’entrée correspondante, puis sélectionnez **Afficher l’aide sur l’erreur** dans le menu contextuel.  

 ![Recherche Bing de liste d’erreurs Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png "Vs_ide_gs_debug_error_list_error_help")  

 Cette opération lance un onglet dans Visual Studio qui présente les résultats d’une recherche Bing portant sur le code et le texte de l’erreur. Les résultats provenant de sources diverses sur Internet, certains peuvent s'avérer inutiles.  

 Vous pouvez également cliquer sur la valeur du code d’erreur, qui se présente sous la forme d’un lien hypertexte, dans la colonne **Code** de la **Liste d’erreurs**. Cette action lance une recherche dans Bing portant uniquement sur le code d'erreur.  

### <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Utiliser des ampoules pour corriger ou refactoriser du code  
 Les ampoules sont une nouvelle fonctionnalité de Visual Studio qui vous permettent de refactoriser le code en mode inline. Grâce aux ampoules, vous pouvez facilement et rapidement résoudre les avertissements courants. Pour y accéder, cliquez sur le trait de soulignement ondulé d’un avertissement (ou appuyez sur **Ctrl+**. tout en pointant sur le trait de soulignement ondulé), puis sélectionnez **Actions rapide**.  

 ![Options rapides d’ampoule dans Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb1.png "Vs_ide_gs_debug_light_bulb1")  

 La liste des corrections ou des refactorisations que vous pouvez appliquer à cette ligne de code s'affiche.  

 ![Aperçu d’ampoule dans Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb_preview_changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  

 Vous pouvez utiliser les ampoules chaque fois que les analyseurs de code déterminent que votre code peut être corrigé, refactorisé ou amélioré. Cliquez sur n’importe quelle ligne de code, cliquez avec le bouton droit pour ouvrir le menu contextuel , puis sélectionnez **Options rapide** (ou, pour aller plus vite, appuyez sur **Ctrl+**.). Si des options de refactorisation ou d’amélioration sont disponibles, elles sont affichées ; dans le cas contraire, le message `No quick options available here` apparaît dans le cadre de l’angle inférieur gauche de l’IDE.  

 ![Texte « aucune option » d’ampoule Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb_no_options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  

 Si vous êtes plus expérimenté, vous pouvez utiliser les touches de direction et **Ctrl+**. pour vérifier rapidement les opportunités de refactorisation des options rapides et nettoyer votre code.  

 Pour plus d’informations sur les ampoules, consultez [Effectuer des actions rapides avec des ampoules](../ide/perform-quick-actions-with-light-bulbs.md).  

### <a name="debug-your-running-code"></a>Déboguer votre code en cours d’exécution  
 Après avoir généré votre code et procédé à quelques tâches de nettoyage, exécutez-le en appuyant sur **F5** ou en sélectionnant **Déboguer > Démarrer le débogage**. Votre application démarre dans un environnement de débogage dans lequel vous pouvez observer son comportement en détail. Pendant l’exécution de votre application, l’IDE de Visual Studio subit des modifications. Ainsi, la fenêtre **Sortie** est remplacée par deux nouvelles fenêtres (dans la configuration des fenêtres par défaut) : une fenêtre avec les onglets **Automatique/Variables locales/Espion** et une autre avec les onglets **Pile des appels/Points d’arrêt/Paramètres d’exception/Sortie**. Ces fenêtres à onglets vous permettent d’inspecter et d’évaluer les variables, threads, piles d’appels et autres comportements de votre application à mesure qu’elle s’exécute.  

 ![Fenêtres Automatique et Pile des appels de Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  

 Vous pouvez arrêter votre application en appuyant sur **Maj+F5** ou en cliquant sur le bouton **Arrêter**. Vous pouvez aussi simplement fermer la fenêtre principale de l’application (ou la boîte de dialogue de la ligne de commande).  

 Si votre code s'exécute parfaitement et exactement comme prévu, félicitations ! Toutefois, si votre code se bloque, qu’il s’arrête ou qu’il produit des résultats inattendus, vous devez rechercher la source de ces problèmes et résoudre les bogues.  

### <a name="set-simple-breakpoints"></a>Définir des points d’arrêt simples  
 Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. Il est INUTILE de régénérer un projet après la définition et la suppression de points d'arrêt.  

 Définissez un point d’arrêt en cliquant à l’extrémité de la marge de la ligne où vous souhaitez arrêter le code, ou appuyez sur **F9** pour définir un point d’arrêt sur la ligne de code actuelle. Quand vous exécutez votre code, celui-ci s’interrompt (ou *s’arrête*) avant d’exécuter les instructions contenues dans cette ligne de code.  

 ![Point d’arrêt Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png "Vs_ide_gs_debug_breakpoint1")   

 Parmi les utilisations courantes des points d'arrêt, citons les suivantes :  

1.  Pour cibler la source d'un incident ou d'un blocage, disséminez des points d'arrêt à l'intérieur et tout autour du code de l'appel de méthode qui semble être à l'origine de l'échec. À mesure que vous exécutez le code dans le débogueur, supprimez les points d’arrêt, puis rapprochez-les les uns des autres jusqu’à identifier la ligne de code incriminée.  Pour découvrir comment exécuter du code dans le débogueur, consultez la section suivante.

2.  Quand vous introduisez une nouvelle section de code, définissez un point d’arrêt au début de celle-ci, puis exécutez le code pour vous assurer qu’il se comporte comme prévu.

3.  Si vous avez implémenté un comportement complexe, définissez un ou plusieurs points d'arrêt dans le code algorithmique de manière à inspecter les valeurs des variables et des données quand le programme s'arrête.  

4.  Si vous écrivez du code en C ou C++, utilisez des points d'arrêt pour arrêter le code de manière à inspecter les valeurs d'adresse (recherchez NULL) et les compteurs de références lors du débogage d'échecs liés à la mémoire.  

 Pour plus d’informations sur l’utilisation des points d’arrêt, consultez [Utilisation des points d’arrêt](../debugger/using-breakpoints.md).  

### <a name="inspect-your-code-at-run-time"></a>Inspecter le code au moment de l’exécution  
 Quand votre code atteint un point d’arrêt et s’interrompt, la ligne de code marquée en jaune (l’instruction en cours) n’a pas encore été exécutée. À ce stade, vous souhaiterez peut-être exécuter l’instruction en cours, puis inspecter les valeurs modifiées. Vous pouvez utiliser plusieurs commandes d’analyse *pas à pas* pour exécuter le code dans le débogueur. Si le code marqué est un appel de méthode, vous pouvez effectuer un pas à pas détaillé en appuyant sur **F11**. Vous pouvez également *exécuter pas à pas* la ligne de code en appuyant sur **F10**. Pour plus d’informations sur les commandes supplémentaires et sur la façon de parcourir le code, consultez [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

 ![Inspection de valeur d’exécution dans Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.PNG "vs_ide_gs_debug_inspect_value") 

 Dans l’illustration précédente, vous pouvez avancer d’une instruction dans le débogueur en appuyant sur **F10** ou **F11** (comme il n’y a ici aucun appel de méthode, les deux commandes ont le même résultat).

 Quand le débogueur est suspendu, vous pouvez inspecter les variables et les piles des appels pour déterminer ce qui se passe. Les valeurs sont-elles comprises dans les plages attendues ? Les appels sont-ils effectués dans le bon ordre ?  

 ![Inspection de valeur d’exécution dans Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.PNG "vs_ide_gs_debug_inspect_value")  

 Pointez sur une variable pour afficher la ou les valeurs et références qu'elle contient actuellement. Si vous remarquez une valeur à laquelle vous ne vous attendiez pas, vous avez probablement un bogue dans les lignes de code précédentes ou d’appel.  Pour en savoir plus sur l’utilisation du débogueur, consultez [cet article](../debugger/getting-started-with-the-debugger.md). 

 Par ailleurs, Visual Studio affiche la fenêtre Outils de diagnostic. Celle-ci vous permet d’observer l’utilisation de l’UC et de la mémoire de votre application au fil du temps. Ultérieurement lors du développement de vos applications, vous pourrez utiliser ces outils pour rechercher les utilisations du processeur ou les allocations de mémoire importantes et imprévues. Utilisez-les conjointement avec la fenêtre **Espion** et les points d’arrêt pour déterminer le problème à l’origine d’une utilisation élevée inattendue ou de la non-libération de ressources.  Pour plus d’informations, consultez [Visite guidée des fonctionnalités de profilage](../profiling/profiling-feature-tour.md).

### <a name="run-unit-tests"></a>Exécuter des tests unitaires  
 Les tests unitaires sont votre première ligne de défense contre les bogues de code car, exécutés correctement, ils testent une seule « unité » de code, généralement une seule fonction, et leur débogage est généralement beaucoup plus simple que le débogage du programme complet. Visual Studio installe les infrastructures de tests unitaires Microsoft pour le code managé et le code natif. Utilisez une infrastructure de test unitaire pour créer des tests unitaires, les exécuter et signaler les résultats de ces tests. Réexécutez des tests unitaires quand vous apportez des modifications pour vérifier que votre code fonctionne toujours correctement. Quand vous utilisez Visual Studio Enterprise Edition, vous pouvez exécuter automatiquement des tests après chaque génération.  

 Pour commencer, consultez [Générer des tests unitaires pour votre code avec IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).  

 Pour en savoir plus sur les tests unitaires dans Visual Studio et sur la façon dont ils peuvent vous aider à créer du code de meilleure qualité, consultez [Concepts de base des tests unitaires](../test/unit-test-basics.md).  

### <a name="perform-static-code-analysis"></a>Effectuer une analyse statique du code  
 L’analyse statique du code désigne simplement la procédure de vérification automatique du code en vue d’identifier des problèmes courants susceptibles d’entraîner des erreurs d’exécution ou des problèmes de gestion du code. Après avoir résolu les erreurs évidentes qui font obstacle à la génération, prenez la bonne habitude d’exécuter cette analyse et consacrez du temps au traitement des avertissements qu’elle peut produire. Cela vous épargnera quelques maux de tête à l’avenir, et vous apprendrez par la même occasion quelques techniques en matière de style de code.  

 Appuyez sur **Alt+F11** (ou sélectionnez **Analyser > Exécuter l’analyse du code sur la solution** dans le menu supérieur) pour démarrer l’analyse statique du code. Si vous avez beaucoup de code, cette opération peut prendre du temps.  

 ![Élément de menu Analyse du code dans Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png "Vs_ide_gs_debug_run_code_analysis")  

 Les nouveaux avertissements et ceux mis à jour sont recensés sous l’onglet **Liste d’erreurs** dans la partie inférieure de l’IDE. Cliquez sur les avertissements pour y accéder.  

 ![Liste d’erreurs Visual Studio avec des avertissements](../ide/media/vs_ide_gs_debug_code_analysis_warning_error_list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")  

 Les avertissements sont identifiés par un trait de soulignement jaune-vert ondulé (s'il est de couleur rouge, il désigne une erreur). Vous pouvez pointer sur ce trait pour afficher plus de détails ou cliquer dessus avec le bouton droit pour accéder à un menu contextuel proposant de l'aide sur les corrections ou les options de refactorisation.  

 ![Pointage de l’avertissement dans Analyse du code de Visual Studio](../ide/media/vs_ide_gs_debug_code_analysis_warning_hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  

## <a name="see-also"></a>Voir aussi  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)  
 [En savoir plus sur l’utilisation du débogueur](../debugger/getting-started-with-the-debugger.md)
