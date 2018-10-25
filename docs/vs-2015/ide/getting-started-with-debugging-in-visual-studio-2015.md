---
title: Mise en route avec le débogage dans Visual Studio 2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fe051a37c610fcfd3c99f2ab762982065c5caf56
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824436"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Prise en main du débogage dans Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 intègre un ensemble puissant d'outils de génération et de débogage de projets. Dans cette rubrique, vous allez apprendre à utiliser l'ensemble des fonctionnalités de base de l'interface utilisateur de débogage.  
  
 Remarque : vous trouverez des liens vers des fonctionnalités plus avancées et des rubriques spécifiques à certaines plateformes ou fonctionnalités en bas de cette page.  
  
## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Mon code ne fonctionne pas. Comment obtenir de l'aide dans Visual Studio 2015 ?  
 Vous avez compris comment fonctionne l'éditeur et vous venez de créer du code. Vous devez à présent déboguer ce code. Dans Visual Studio 2015, comme dans la plupart des environnements de développement intégrés (IDE), le débogage comprend deux phases : la génération du code pour intercepter et résoudre les erreurs liées au projet et au compilateur, puis l'exécution du code dans l'environnement pour intercepter et résoudre les erreurs dynamiques et d'exécution.  
  
### <a name="configuring-a-build"></a>Configuration d'une build  
 Il existe deux types de base de configurations de build : **Debug** et **Release**. La première configuration produit un fichier exécutable plus volumineux et moins rapide. S'il ne doit jamais être publié, il rend l'expérience de débogage à l'exécution plus riche et interactive. La seconde configuration génère un fichier exécutable plus rapide et optimisé qu'il est possible de publier (tout du moins du point de vue du compilateur).  
  
 La configuration de build par défaut est **Debug**.  
  
 ![Bouton de version Debug Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")  
  
 Vous pouvez également cibler une plateforme de génération spécifique, telle que **x86** (processeurs Intel 32 bits), **x64** (processeurs Intel 64 bits) et **ARM** (processeurs ARM uniquement pris en charge pour certains types d’applications). La valeur par défaut est **x86** pour les projets managés et natifs. Pour modifier cette valeur, cliquez sur la liste déroulante Plateforme de génération, puis sélectionnez une autre plateforme ou **Gestionnaire de configurations**.  
  
 ![Fenêtre Gestionnaire de fichiers de configuration Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")  
  
 Vous pouvez spécifier une configuration de build ciblée à l’aide du **Gestionnaire de configurations**. Pour cela, lancez-le, cliquez sur la liste déroulante **Configuration** ou **UC**, puis sélectionnez **Nouveau** pour créer une build ou une plateforme.  
  
 ![Fenêtre Gestionnaire de configurations Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")  
  
 Pour commencer, utilisez simplement **Debug** comme configuration de build et **x86** comme plateforme. Une fois le codage et le débogage terminés, passez à la configuration **Release** et ciblez une plateforme spécifique. (Les anciennes versions de Visual Studio proposent une plateforme par défaut **AnyCPU** pour les projets de code .Net.)  
  
 Remarque : quand vous générez votre projet, les valeurs de configuration et de plateforme servent également à déterminer le chemin d’accès au répertoire du projet à créer pour stocker le fichier exécutable. En général, il s’agit de **\<chemin_projet>\\<nom_projet>\\<configuration\>\\<plateforme\>**. Par exemple, un projet avec une configuration `Debug` et une plateforme `x86` se trouve sous `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Cela peut être utile si vous utilisez vos propres outils ou scripts pour gérer ces fichiers exécutables générés.  
  
### <a name="building-your-code"></a>Génération de code  
 Une fois votre build configurée, il est temps de passer à la génération de votre projet. Le moyen le plus simple consiste à appuyer sur F7, mais vous pouvez aussi démarrer la build en sélectionnant **Générer->Générer la solution** dans le menu principal.  
  
 ![Sélection du menu de génération du projet Visual Studio](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")  
  
 Vous pouvez observer le processus de génération dans la fenêtre d’état **Sortie** située dans la partie inférieure de l’interface utilisateur de Visual Studio. Les erreurs, avertissements et opérations de génération sont affichés ici. En cas d'erreurs (ou si vous recevez des avertissements au-delà d'un niveau configuré), votre build échoue. Vous pouvez cliquer sur une erreur ou sur un avertissement pour accéder à la ligne à l'origine du problème. Régénérez votre projet. Pour cela, appuyez sur **F7** (pour recompiler uniquement les fichiers avec des erreurs) ou sur **Ctrl+Alt+F7** (pour une nouvelle régénération complète).  
  
 Deux fenêtres à onglets apparaissent dans la fenêtre de résultats sous l’éditeur : la fenêtre **Sortie**, qui contient la sortie brute du compilateur (y compris les messages d’erreur), et la fenêtre **Liste d’erreurs**, qui fournit une liste pouvant être triée et filtrée de l’ensemble des erreurs et des avertissements.  
  
 En cas de réussite, des résultats semblable à ceux-ci apparaissent dans la fenêtre **Sortie**.  
  
 ![Sortie de génération réussie Visual Studio](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")  
  
### <a name="reviewing-the-error-list"></a>Revue de la liste d’erreurs  
 À moins que vous n'ayez apporté aucune modification à du code précédemment compilé avec succès, il y a de grandes chances qu'une erreur se produise. Et si vous codez depuis peu, il est même probable que vous receviez un grand nombre d'erreurs. Si certains erreurs sont évidentes, comme une simple erreur de syntaxe ou un nom de variable incorrect, d'autres sont parfois plus ardues à comprendre. Et ce n'est pas le code obscur associé à celles-ci qui va davatange vous aider. Pour obtenir une vue plus conviviale des problèmes, accédez à la partie inférieure de la fenêtre **Sortie** de la build, puis cliquez sur l’onglet **Liste d’erreurs**. Vous disposez non seulement d'une vue mieux organisée des erreurs et des avertissements liés à votre projet, mais aussi d'options supplémentaires.  
  
 ![Sortie de Visual Studio 2015 et liste d’erreurs](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")  
  
 Cliquez sur la ligne d’erreur dans la fenêtre **Liste d’erreurs** pour accéder directement à la ligne à l’origine de l’erreur. (Ou activez les numéros de ligne en cliquant dans la barre **Lancement rapide** située dans l’angle supérieur droit, en tapant « numéros de ligne » dans celle-ci, puis en appuyant sur Entrée. C’est le moyen le plus rapide d’arriver à l’entrée de la fenêtre **Options** qui vous permet d’activer les numéros de ligne. En vous familiarisant avec la barre **Lancement rapide**, vous économiserez un grand nombre de clics dans l’interface utilisateur !)  
  
 ![Éditeur Visual Studio avec des numéros de ligne](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")  
  
 ![Option des numéros de ligne Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")  
  
 Utilisez Ctrl+G pour accéder rapidement au numéro de ligne où l’erreur s’est produite.  
  
 L'erreur est identifiée par un trait de soulignement rouge ondulé. Pointez dessus pour obtenir plus d'informations. Apportez la correction nécessaire pour faire disparaître ce trait. Notez toutefois que vous risquez d'introduire une nouvelle erreur. (C'est ce que l'on appelle une « régression »).  
  
 ![Pointage d’erreur Visual Studio](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")  
  
 Passez en revue la liste d'erreurs et corrigez toutes les erreurs dans votre code.  
  
 ![Fenêtre d’erreurs de débogage Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")  
  
### <a name="reviewing-errors-in-detail"></a>Revue des erreurs en détail  
 De nombreuses erreurs, exprimées selon les termes du compilateur, peuvent vous paraître incompréhensibles. Dans ces cas-là, vous avez besoin d'informations supplémentaires. La fenêtre **Liste d’erreurs** vous permet de lancer une recherche automatique dans Bing pour obtenir plus d’informations sur l’erreur (ou l’avertissement). Pour cela, cliquez avec le bouton droit sur la ligne d’entrée correspondante, puis sélectionnez **Afficher l’aide sur l’erreur** dans le menu contextuel.  
  
 ![Recherche Bing de liste d’erreurs Visual Studio](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")  
  
 Cette opération lance un onglet dans Visual Studio 2015 qui présente les résultats d'une recherche Bing portant sur le code et le texte de l'erreur. Les résultats provenant de sources diverses sur Internet, certains peuvent s'avérer inutiles.  
  
 Vous pouvez également cliquer sur la valeur du code d’erreur, qui se présente sous la forme d’un lien hypertexte, dans la colonne **Code** de la **Liste d’erreurs**. Cette action lance une recherche dans Bing portant uniquement sur le code d'erreur.  
  
### <a name="performing-static-code-analysis"></a>Analyse statique du code  
 L'analyse statique du code désigne simplement la procédure de vérification automatique du code en vue d'identifier des problèmes courants susceptibles d'entraîner des erreurs d'exécution ou des problèmes de gestion du code. Après avoir résolu les erreurs évidentes qui font obstacle à la génération, prenez la bonne habitude d'exécuter cette analyse et consacrez du temps au traitement des avertissements qu'elle peut produire. Cela vous épargnera quelques maux de tête à l'avenir, et vous apprendrez par la même occasion quelques techniques en matière de style de code.  
  
 Appuyez sur Alt+F11 (ou sélectionnez **Analyze->Exécuter l’analyse du code sur la solution** dans le menu supérieur) pour démarrer l’analyse statique du code. Si vous avez beaucoup de code, cette opération peut prendre du temps.  
  
 ![Élément de menu de Visual Studio 2015 Code Analysis](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")  
  
 Les nouveaux avertissements et ceux mis à jour sont recensés sous l’onglet **Liste d’erreurs** dans la partie inférieure de l’IDE. Cliquez sur les avertissements pour y accéder.  
  
 ![Liste d’erreurs Visual Studio 2015 avec avertissements](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")  
  
 Les avertissements sont identifiés par un trait de soulignement jaune-vert ondulé (s'il est de couleur rouge, il désigne une erreur). Vous pouvez pointer sur ce trait pour afficher plus de détails ou cliquer dessus avec le bouton droit pour accéder à un menu contextuel proposant de l'aide sur les corrections ou les options de refactorisation.  
  
 ![Pointage de l’avertissement dans Analyse du code de Visual Studio](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  
  
### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Utilisation des ampoules pour corriger ou refactoriser du code  
 Introduites dans Visual Studio 2015, les ampoules vous permettent de refactoriser le code en mode inline. Grâce aux ampoules, vous pouvez facilement et rapidement résoudre les avertissements courants. Pour y accéder, cliquez sur le trait de soulignement ondulé d’un avertissement (ou appuyez sur Ctrl+. tout en pointant sur le trait de soulignement ondulé), puis sélectionnez **Actions rapide**.  
  
 ![Options rapides de Visual Studio 2015 ampoule](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")  
  
 La liste des corrections ou des refactorisations que vous pouvez appliquer à cette ligne de code s'affiche.  
  
 ![Visual Studio 2015 ampoule aperçu](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  
  
 Vous pouvez utiliser les ampoules chaque fois que les analyseurs de code déterminent que votre code peut être corrigé, refactorisé ou amélioré. Cliquez sur n’importe quelle ligne de code, cliquez avec le bouton droit pour ouvrir le menu contextuel , puis sélectionnez **Options rapide** (ou, pour aller plus vite, appuyez sur Ctrl+.). Si des options de refactorisation ou d’amélioration sont disponibles, elles sont affichées ; dans le cas contraire, le message `No quick options available here` apparaît dans le cadre de l’angle inférieur gauche de l’IDE.  
  
 ![Ampoule Visual Studio 2015 « aucune option » texte](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  
  
 Si vous êtes plus expérimenté, vous pouvez utiliser les touches de direction et Ctrl+. pour vérifier rapidement les opportunités de refactorisation des options rapides et nettoyer votre code.  
  
 Pour plus d’informations sur les ampoules, consultez [Effectuer des actions rapides avec des ampoules](../ide/perform-quick-actions-with-light-bulbs.md).  
  
### <a name="debugging-your-running-code"></a>Débogage de votre code en cours d'exécution  
 Après avoir généré votre code et procédé à quelques tâches de nettoyage, exécutez-le en appuyant sur F5 ou en sélectionnant **Déboguer->Démarrer le débogage**. Votre application démarre dans un environnement de débogage dans lequel vous pouvez observer son comportement en détail. L’IDE de Visual Studio 2015 modifie alors que votre application est en cours d’exécution : le **sortie** fenêtre est remplacée par deux nouvelles fenêtres (dans la configuration de fenêtre par défaut), le **automatique/variables locales/Modules/espion** fenêtre à onglets et le **Appeler des points d’arrêt/pile/Exception paramètres/sortie** fenêtre à onglets. Ces fenêtres à onglets vous permettent d'inspecter et d'évaluer les variables, threads, piles d'appels et autres comportements de votre application à mesure qu'elle s'exécute.  
  
 ![VS2015 Automatique et appel de pile Windows](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  
  
 Essayez différentes actions avec votre application et observez les changements qui se produisent. Si quelque chose vous semble anormale, interrompez l’application en appuyant sur Ctrl + Alt + Attn (ou cliquez sur le bouton **Pause**).  
  
 ![Bouton Interrompre tout Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")  
  
 Appuyez sur F5 pour continuer l’exécution de l’application (ou cliquez sur le bouton **Continuer**).  
  
 ![Bouton de poursuite du débogage Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")  
  
 Vous pouvez arrêter votre application en appuyant sur Maj + F5 ou en cliquant sur le bouton **Arrêter**. Vous pouvez aussi simplement fermer la fenêtre principale de l'application (ou la boîte de dialogue de la ligne de commande).  
  
 Si votre code s'exécute parfaitement et exactement comme prévu, félicitations ! Faites passer votre build en configuration **Release** et régénérez-la en vue de son déploiement. (Si vous êtes un professionnel, passez à la section consacrée aux tests unitaires à la fin de cette rubrique.) Toutefois, si votre code se bloque, qu'il s'arrête ou qu'il produit des résultats inattendus, vous devez rechercher la source de ces problèmes et résoudre les bogues.  
  
### <a name="setting-simple-breakpoints"></a>Définition de points d'arrêt simples  
 Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. Il est INUTILE de régénérer un projet après la définition et la suppression de points d'arrêt.  
  
 Pour définir un point d’arrêt, cliquez à l’extrémité de la marge de la ligne où vous souhaitez arrêter le code, ou sélectionnez la ligne de code et appuyez sur F9. Quand vous exécutez votre code, celui-ci s'arrête avant d'exécuter les instructions contenues dans cette ligne de code.  
  
 ![Point d’arrêt Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")  
  
 Quand le code s'arrête, la ligne de code indiquée n'est pas encore exécutée. À ce stade, vous pouvez exécuter les instructions de la ligne de code indiquée par le point d'arrêt et inspecter les valeurs modifiées. C'est ce qui s'appelle « effectuer un pas à pas détaillé » dans le code. Si le code indiqué est un appel de méthode, vous pouvez effectuer un pas à pas détaillé en appuyant sur F11. Vous pouvez également « effectuer un pas à pas principal » dans la ligne de code en appuyant sur F10. Pour plus d’informations sur les actions d’étape de point d’arrêt, consultez [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).  
  
 Parmi les utilisations courantes des points d'arrêt, citons les suivantes :  
  
1. Pour cibler la source d'un incident ou d'un blocage, disséminez des points d'arrêt à l'intérieur et tout autour du code de l'appel de méthode qui semble être à l'origine de l'échec. À mesure que vous effectuez un pas à pas dans le code, supprimez les points d'arrêt, puis rapprochez-les les uns des autres jusqu'à ce que vous identifiiez la ligne de code incriminée.  
  
2. Quand vous introduisez une nouvelle section de code, définissez un point d'arrêt au début de celle-ci, puis effectuez un pas à pas dans le code pour vous assurer qu'il se comporte comme prévu.  
  
3. Si vous avez implémenté un comportement complexe, définissez un ou plusieurs points d'arrêt dans le code algorithmique de manière à inspecter les valeurs des variables et des données quand le programme s'arrête.  
  
4. Si vous écrivez du code en C ou C++, utilisez des points d'arrêt pour arrêter le code de manière à inspecter les valeurs d'adresse (recherchez NULL) et les compteurs de références lors du débogage d'échecs liés à la mémoire.  
  
   Pour plus d’informations sur l’utilisation des points d’arrêt, consultez [Utilisation des points d’arrêt](../debugger/using-breakpoints.md).  
  
### <a name="setting-conditional-breakpoints"></a>Définition de points d'arrêt conditionnels  
 Si vous avez défini un point d'arrêt dans une boucle ou une récurrence, ou si vous effectuez fréquemment un pas à pas dans du code contenant un grand nombre de points d'arrêt, utilisez un point d'arrêt conditionnel pour vous assurer que votre code s'interrompt UNIQUEMENT quand certaines conditions sont remplies. Sinon, vous allez devoir appuyer sur F11 sans relâche.  
  
 Pour définir un point d'arrêt conditionnel et interrompre votre code quand une variable est définie avec une valeur donnée ou qu'elle dépasse d'un certain seuil, cliquez dans la marge pour définir un point d'arrêt, puis sélectionnez la « roue dentée » dans le menu sensitif qui s'affiche.  
  
 ![Paramètres de point d’arrêt Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")  
  
 Dans la boîte de dialogue qui s'affiche, semblable à celle-ci, vous pouvez définir des conditions spécifiques au déclenchement de l'arrêt.  
  
 ![Visual Studio 2015 conditionnel point d’arrêt](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")  
  
 Pour plus d’informations sur la façon de déclarer les expressions utilisées pour évaluer des points d’arrêt conditionnels, visionnez la vidéo de Channel 9 [expérience de Configuration de point d’arrêt dans Visual Studio 2015](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).  
  
### <a name="inspecting-your-code-at-run-time"></a>Inspection du code au moment de l'exécution  
 Quand votre code en cours d'exécution arrive à un point d'arrêt et qu'il s'arrête, vous pouvez inspecter les variables et les piles des appels pour déterminer ce qui se passe. Les valeurs sont-elles comprises dans les plages attendues ? Les appels sont-ils effectués dans le bon ordre ?  
  
 ![Visual Studio 2015 exécuter&#45;inspection des valeurs de temps](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")  
  
 Pointez sur une variable pour afficher la ou les valeurs et références qu'elle contient actuellement. Si vous remarquez une valeur à laquelle vous ne vous attendiez pas, vous avez probablement un bogue dans les lignes de code précédentes ou d'appel. Déplacez les points d'arrêt vers le haut ou ajoutez des conditions aux points d'arrêt existants pour affiner votre recherche.  
  
 Par ailleurs, Visual Studio 2015 affiche la fenêtre Outils de diagnostic. Celle-ci vous permet d'observer l'utilisation de l'UC et de la mémoire de votre application au fil du temps. Inspectez ces valeurs pour identifier toute hausse inattendue de l'utilisation de l'UC ou de l'allocation de la mémoire. Utilisez-les conjointement avec la fenêtre **Espion** et les points d’arrêt pour déterminer le problème à l’origine d’une utilisation élevée inattendue ou de la non-libération de ressources.  
  
 ![Fenêtre de Visual Studio 2015 Diagnostic Tools](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")  
  
### <a name="running-unit-tests"></a>Exécution de tests unitaires  
 Les tests unitaires sont des programmes qui vérifient les chemins de code dans votre application ou service. Visual Studio 2015 installe les infrastructures de tests unitaires Microsoft pour le code managé et le code natif. Utilisez une infrastructure de test unitaire pour créer des tests unitaires, les exécuter et signaler les résultats de ces tests. Réexécutez des tests unitaires quand vous apportez des modifications pour vérifier que votre code fonctionne toujours correctement. Quand vous utilisez Visual Studio 2015 Enterprise, vous pouvez exécuter automatiquement les tests après chaque build.  
  
 Pour commencer, consultez [Générer des tests unitaires pour votre code avec IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).  
  
 Pour en savoir plus sur les tests unitaires dans Visual Studio 2015 et comment ils peuvent vous aider à créer du code de meilleure qualité, [concepts de base de tests unitaires](../test/unit-test-basics.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Déboguer des applications 64 bits](../debugger/debug-64-bit-applications.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)



