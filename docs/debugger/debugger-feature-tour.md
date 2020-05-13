---
title: Présentation du débogueur
description: Bien démarrer avec le débogage d’applications en utilisant le débogueur Visual Studio
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93973322c40ca62396414317c2ad8875e9b94854
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77578958"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Premier aperçu du débogueur Visual Studio

Cette rubrique prÃ©sente les outils du dÃ©bogueur fournis par Visual Studio. Dans le contexte Visual Studio, quand vous *dÃ©boguez votre application*, cela signifie gÃ©nÃ©ralement que vous exÃ©cutez votre application en y ayant attachÃ© le dÃ©bogueur (câ€™est-Ã -dire en mode DÃ©bogueur). Quand vous faites cela, le dÃ©bogueur fournit de nombreuses faÃ§ons de voir ce que fait votre code pendant quâ€™il sâ€™exÃ©cute. Vous pouvez passer Ã  travers votre code et regarder les valeurs stockÃ©es dans les variables, vous pouvez dÃ©finir des montres sur les variables pour voir quand les valeurs changent, vous pouvez examiner le chemin dâ€™exÃ©cution de votre code, et al. Si câ€™est la premiÃ¨re fois que vous avez essayÃ© de dÃ©boguer le code, vous voudrez peut-Ãªtre lire [Debugging pour les dÃ©butants absolus](../debugger/debugging-absolute-beginners.md) avant de passer par ce sujet.

Les fonctionnalités décrites ici sont applicables à C#, C++, Visual Basic, JavaScript et à d’autres langages pris en charge par Visual Studio (sauf indication contraire).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrer le débogueur

Pour déboguer, vous devez démarrer votre application avec le débogueur attaché au processus de l’application. **F5** (**Déboguer > Démarrer le débogage**) est l’approche la plus courante pour faire cela. Cependant, vous n’avez peut-être pas encore défini de points d’arrêt pour examiner le code de votre application : nous commençons donc par cela, puis nous démarrons le débogage. Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

Si vous avez un fichier ouvert dans l’éditeur de code, vous pouvez définir un point d’arrêt en cliquant dans la marge à gauche d’une ligne de code.

![Définir un point d’arrêt](../debugger/media/dbg-tour-set-a-breakpoint.gif "Définir un point d'arrêt")

Appuyez sur **F5** (**Debug > Start Debugging**) ou le bouton **Start Debugging** ![DÃ©marrer Debugging](../debugger/media/dbg-tour-start-debugging.png "DÃ©marrer le dÃ©bogage") dans la barre dâ€™outils Debug, et le dÃ©bogage fonctionne au premier point de rupture quâ€™il rencontre. Si lâ€™application nâ€™est pas dÃ©jÃ  en cours dâ€™exÃ©cution, F5 dÃ©marre le dÃ©bogueur et sâ€™arrÃªte au premier point dâ€™arrÃªt.

Les points d’arrêt sont une fonctionnalité pratique quand vous savez quelle ligne de code ou section de code vous voulez examiner en détail.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a>Naviguez le code dans le dÃ©bagÃ© Ã  lâ€™aide de commandes dâ€™Ã©tape

Nous fournissons les raccourcis clavier pour la plupart des commandes, car ils rendent plus rapide la navigation dans le code de votre d’application. (Les commandes équivalentes, comme les commandes des menus, sont données entre parenthèses.)

Pour démarrer votre application avec le débogueur attaché, appuyez sur **F11** (**Déboguer > Pas à pas détaillé**). F11 est la commande **Pas à pas détaillé** : elle fait avancer l’exécution de l’application une instruction à la fois. Quand vous démarrez l’application avec F11, le débogueur s’arrête sur la première instruction exécutée.

![F11 Step Into](../debugger/media/dbg-tour-f11.png "F11 Step Into")

La flèche jaune représente l’instruction sur laquelle le débogueur s’est mis en pause, ce qui interrompt également l’exécution de l’application au même point (cette instruction n’a pas encore été exécutée).

F11 est un bon moyen pour examiner le flux de lâ€™exÃ©cution de la faÃ§on la plus dÃ©taillÃ©e. (Pour aller plus vite Ã  travers le code, nous vous montrons dâ€™autres options ainsi.) Par dÃ©faut, le dÃ©bbuggeur saute sur le code non-utilisateur (si vous voulez plus de dÃ©tails, voir [Just My Code](../debugger/just-my-code.md)).

>[!NOTE]
> Dans le code managé, vous voyez une boîte de dialogue vous demandant si vous voulez être averti quand vous effectuez automatiquement un pas à pas principal dans les propriétés et les opérateurs (le comportement par défaut). Si vous voulez changer ce paramètre ultérieurement, désactivez le paramètre **Pas à pas principal dans les propriétés et les opérateurs** dans le menu **Outils > Options** sous **Débogage**.

## <a name="step-over-code-to-skip-functions"></a>Effectuer un pas à pas principal dans le code pour ignorer les fonctions

Quand vous êtes sur une ligne de code qui est un appel de fonction ou de méthode, vous pouvez appuyer sur **F10** (**Déboguer > Pas à pas principal**) au lieu de F11.

F10 fait avancer le débogueur sans effectuer de pas à pas détaillé dans les fonctions ou les méthodes du code de votre application (le code s’exécute néanmoins). En appuyant sur F10, vous pouvez ignorer le code qui ne vous intéresse pas. De cette façon, vous pouvez rapidement accéder au code qui vous intéresse le plus.

## <a name="step-into-a-property"></a>Pas à pas détaillé d’une propriété

Comme mentionné précédemment, par défaut, le débogueur ignore les propriétés et les champs managés, mais la commande **Pas à pas détaillé spécifique** vous permet de remplacer ce comportement.

Cliquez avec le bouton droit sur une propriété ou un champ, et choisissez **Pas à pas détaillé spécifique**, puis choisissez une des options disponibles.

![Entrez dans Specific](../debugger/media/dbg-tour-step-into-specific.png "Entrez dans specific")

Dans cet exemple, **Pas à pas détaillé spécifique** nous amène au code pour `Path.set`.

![Entrez dans Specific](../debugger/media/dbg-tour-step-into-specific-2.png "Entrez dans specific")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Exécuter rapidement jusqu’à un point dans votre code avec la souris

Pendant que dans le dÃ©bbugger, planer au-dessus dâ€™une ligne de code jusquâ€™Ã  ce que le bouton **Run to Click** (ExÃ©cution dâ€™exÃ©cution Ã  ici) Run to ![Click](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaÃ®t sur la gauche.

![Exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click-2.png "Exécuter jusqu’au clic")

> [!NOTE]
> Le bouton **Exécuter jusqu’au clic** (Exécuter l’exécution jusqu’ici) est disponible à compter de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Cliquez sur le bouton **Exécuter jusqu’au clic** (Exécuter l’exécution jusqu’ici). Le débogueur avance jusqu’à la ligne de code où vous avez cliqué.

L’utilisation de ce bouton revient à définir un point d’arrêt temporaire. Cette commande est également pratique pour parcourir rapidement une zone visible du code d’application. Vous pouvez utiliser **Exécuter jusqu’au clic** dans n’importe quel fichier ouvert.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Faire avancer le débogueur en dehors de la fonction active

Parfois, vous voulez continuer votre session de débogage, mais faire avancer le débogueur en dehors de la fonction active.

Appuyez sur **Maj+F11** (**ou Déboguer > Pas à pas sortant**).

Cette commande reprend l’exécution de l’application (et fait avancer le débogueur) jusqu’au retour de la fonction active.

## <a name="run-to-cursor"></a>Exécuter jusqu'au curseur

ArrÃªtez le dÃ©bogage en appuyant sur le bouton rouge **Stop Debugging** ![Stop Debugging](../debugger/media/dbg-tour-stop-debugging.png "ArrÃªter le dÃ©bogage") ou **Shift** + **F5**.

Cliquez avec le bouton droit sur une ligne de votre code d’application et choisissez **Exécuter jusqu’au curseur**. Cette commande démarre le débogage et définit un point d’arrêt temporaire sur la ligne de code active.

![Courir Ã  Cursor](../debugger/media/dbg-tour-run-to-cursor.png "ExÃ©cuter jusqu'au curseur")

Si vous avez défini des points d’arrêt, le débogueur se met en pause sur le premier point d’arrêt qu’il atteint.

Appuyez sur **F5** jusqu’à atteindre la ligne de code où vous avez sélectionné **Exécuter jusqu’au curseur**.

Cette commande est pratique quand vous modifiez du code, et que vous voulez définir rapidement un point d’arrêt temporaire et démarrer en même temps le débogueur.

> [!NOTE]
> Vous pouvez utiliser **Exécuter jusqu’au curseur** dans la fenêtre **Pile des appels** pendant que vous déboguez.

## <a name="restart-your-app-quickly"></a>Redémarrer rapidement votre application

Cliquez sur le bouton **RedÃ©marrer** ![lâ€™application](../debugger/media/dbg-tour-restart.png "RedÃ©marrer lâ€™application") de redÃ©marrage dans la barre dâ€™outils Debug (**Ctrl et Shift F5**).

Quand vous appuyez sur **Redémarrer**, vous gagnez du temps par rapport à l’action consistant à arrêter l’application, puis à redémarrer le débogueur. Le débogueur se met en pause sur le premier point d’arrêt qui est atteint par l’exécution du code.

Si vous voulez arrÃªter le dÃ©bogage et revenir dans lâ€™Ã©diteur de code, vous pouvez appuyer sur le bouton ![stop Debugging](../debugger/media/dbg-tour-stop-debugging.png "ArrÃªter le dÃ©bogage") rouge au lieu de **redÃ©marrer**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Modifiez votre code et continuez Ã  dÃ©bogage (C, VB, C, XAML)

Dans la plupart des langues prises en charge par Visual Studio, vous pouvez modifier votre code au milieu dâ€™une session de dÃ©bogage et continuer Ã  dÃ©bogage. Pour utiliser cette fonctionnalitÃ©, cliquez sur votre code avec votre curseur en pause dans le dÃ©bogage, faites des modifications et appuyez sur **F5**, **F10**ou **F11** pour continuer Ã  dÃ©bogage.

![Modifier et continuer Ã  dÃ©bogage](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Pour plus dâ€™informations sur lâ€™utilisation de la fonctionnalitÃ© et sur les limitations des fonctionnalitÃ©s, voir [Modifier et Continuer](../debugger/edit-and-continue.md).

Pour modifier le code XAML lors dâ€™une session de dÃ©bogage, voir [Ã‰crire et dÃ©boguer le code XAML avec XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles dâ€™informations (datatips)

Maintenant que vous vous débrouillez un peu, vous pouvez commencer à examiner l’état de votre application (ses variables) avec le débogueur. Les fonctionnalités qui vous permettent d’inspecter des variables sont parmi les plus pratiques du débogueur : vous pouvez faire cela de différentes façons. Souvent, quand vous essayez de déboguer un problème, vous essayez de déterminer si les variables stockent les valeurs que vous prévoyez dans un état donné de l’application.

Avec l’exécution en pause dans le débogueur, placez le curseur sur un objet avec la souris : vous voyez la valeur par défaut de sa propriété (dans cet exemple, le nom de fichier `market 031.jpg` est la valeur par défaut de la propriété).

![Afficher un conseil de donnÃ©es](../debugger/media/dbg-tour-data-tips.gif "Afficher une astuce de donnÃ©es")

Développez l’objet pour voir toutes ses propriétés (comme la propriété `FullPath` dans cet exemple).

Souvent, lors du dÃ©bogage, vous voulez un moyen rapide de vÃ©rifier les valeurs des propriÃ©tÃ©s sur des objetsÂ : les datatips sont un bon moyen de le faire.

> [!TIP]
> Dans la plupart des langages pris en charge, vous pouvez modifier le code pendant une session de débogage. Pour plus d’informations, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les Fenêtres Automatique et Variables locales

Pendant le débogage, examinez la fenêtre **Automatique** en bas de l’éditeur de code.

![FenÃªtre Autos](../debugger/media/dbg-tour-autos-window.png "Automatique (fenÃªtre)")

Dans la fenêtre **Automatique**, vous voyez des variables, avec leur valeur actuelle et leur type. La fenêtre **Automatique** montre toutes les variables utilisées dans la ligne active ou la ligne précédente (en C++, la fenêtre montre les variables des trois lignes de code précédentes ; consultez la documentation pour les comportements selon le langage).

> [!NOTE]
> En JavaScript, la fenêtre **Variables locales** est prise en charge, mais pas la fenêtre **Automatique**.

Ensuite, examinez la fenêtre **Variables locales**. La fenêtre **Variables locales** vous montre les variables qui se trouvent actuellement dans l’étendue.

![Variables locales, fenÃªtre](../debugger/media/dbg-tour-locals-window.png "FenÃªtre Variables locales")

Dans cet exemple, l’objet `this` et l’objet `f` sont dans l’étendue. Pour plus d’informations, consultez [Inspecter les variables dans les fenêtres Automatique et Variables locales](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Définir un espion

Vous pouvez utiliser une fenêtre **Espion** pour spécifier une variable (ou une expression) que vous voulez observer.

Pendant le débogage, cliquez avec le bouton droit sur un objet et choisissez **Ajouter un espion**.

![Espion, fenÃªtre](../debugger/media/dbg-tour-watch-window.png "FenÃªtre Espion")

Dans cet exemple, vous avez un espion défini sur l’objet `f` et vous pouvez voir sa valeur changer au fil de votre déplacement dans le débogueur. Contrairement à d’autres fenêtres de variables, la fenêtre **Espion** montre toujours les variables que vous observez (elles apparaissent en grisé quand elles sont en dehors de l’étendue).

Pour plus d’informations, consultez [Définir un espion avec les Fenêtres Espion et Espion express](../debugger/watch-and-quickwatch-windows.md).

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

Pendant que vous déboguez, cliquez sur la fenêtre **Pile des appels**, qui est ouverte par défaut dans le volet inférieur droit.

![Examiner la pile dâ€™appels](../debugger/media/dbg-tour-call-stack.png "Examiner la pile des appels")

La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La ligne du haut montre la fonction active (dans cet exemple, la méthode `Update`). La deuxième ligne montre que `Update` a été appelée depuis la propriété `Path.set`, etc. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

> [!NOTE]
> La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

Vous pouvez double-cliquer sur une ligne de code pour accéder à ce code source ; ceci change également l’étendue active inspectée par le débogueur. Ceci ne fait pas avancer le débogueur.

Vous pouvez également utiliser les menus contextuels de la fenêtre **Pile des appels** pour faire d’autres choses. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiques, redémarrer votre application avec **Exécuter jusqu’au curseur** et aller examiner le code source. Consultez [Guide pratique pour examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a> Examiner une exception

Quand votre application lève une exception, le débogueur vous amène à la ligne de code qui a levé cette exception.

![Aide dâ€™exception](../debugger/media/dbg-tour-exception-helper.png "Aide dâ€™exception")

Dans cet exemple, **l’Assistance sur l’exception** vous montre une exception `System.Argument` et un message d’erreur indiquant que le chemin n’est pas d’une forme autorisée. Ainsi, nous savons que l’erreur s’est produite sur l’argument d’une méthode ou d’une fonction.

Dans cet exemple, l’appel de `DirectoryInfo` a provoqué l’erreur sur la chaîne vide, stockée dans la variable `value`.

L’Assistance sur l’exception est une fonctionnalité intéressante qui peut vous aider à déboguer des erreurs. Vous pouvez également examiner les détails de l’erreur et ajouter un espion à partir de l’Assistance sur l’exception. Si nécessaire, vous pouvez aussi changer les conditions pour lever une exception donnée. Pour plus d’informations sur la prise en charge des exceptions dans le code, consultez [Techniques et outils de débogage](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> L’Assistance Exception remplace l’Assistant Exception à compter de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Développez le nœud **Paramètres d’exception** pour voir plus d’options sur la façon de gérer ce type d’exception ; dans le cadre de cette visite guidée, vous ne devez néanmoins rien changer !

## <a name="configure-debugging"></a>Configurer le débogage

Vous pouvez configurer votre projet pour construire comme configuration [Debug ou Release,](../debugger/how-to-set-debug-and-release-configurations.md)configurer les propriÃ©tÃ©s du projet pour dÃ©bogage, ou configurer [des paramÃ¨tres gÃ©nÃ©raux](../debugger/how-to-specify-debugger-settings.md) pour le dÃ©bogage. En outre, vous pouvez configurer le dÃ©bbugger pour afficher des informations personnalisÃ©es Ã  lâ€™aide de fonctionnalitÃ©s telles que [lâ€™attribut DebuggerDisplay](using-the-debuggerdisplay-attribute.md) ou, pour C /C, le [cadre NatVis](create-custom-views-of-native-objects.md).

Les propriÃ©tÃ©s de dÃ©bogage sont spÃ©cifiques Ã  chaque type de projet. Par exemple, vous pouvez spÃ©cifier un argument pour passer Ã  lâ€™application lorsque vous la dÃ©marrez. Vous pouvez accÃ©der aux propriÃ©tÃ©s spÃ©cifiques au projet en cliquant Ã  droite sur le projet dans Solution Explorer et en sÃ©lectionnant des **propriÃ©tÃ©s**. Les propriÃ©tÃ©s de dÃ©bogage apparaissent gÃ©nÃ©ralement dans lâ€™onglet **Build** ou **Debug,** selon le type de projet particulier.

![PropriÃ©tÃ©s dâ€™un projet](../debugger/media/dbg-tour-project-properties.png "PropriÃ©tÃ©s dâ€™un projet")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Déboguer des applications ASP.NET en production dans Azure App Service

**lâ€™instantanÃ© Debugger** prend un instantanÃ© de vos applications de production lorsque le code qui vous intÃ©resse exÃ©cute. Pour indiquer au dÃ©bogueur de prendre une capture instantanÃ©e, vous dÃ©finissez des points dâ€™ancrage et des points de journalisation dans votre code. Dans le dÃ©bogueur, vous pouvez voir prÃ©cisÃ©ment Ã  quel endroit le code ne sâ€™est pas exÃ©cutÃ© correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider Ã  rÃ©soudre beaucoup plus vite les problÃ¨mes rencontrÃ©s dans les environnements de production.

![Lancer le DÃ©bogueur de capture instantanÃ©e](../debugger/media/snapshot-launch.png "Lancer le DÃ©bogueur de capture instantanÃ©e")

La collecte de captures instantanées est disponible pour les applications ASP.NET qui s’exécutent dans Azure App Service. Les applications ASP.NET doivent s’exécuter sur le .NET Framework 4.6.1 ou ultérieur, et les applications ASP.NET Core doivent s’exécuter sur .NET Core 2.0 ou ultérieur sur Windows.

Pour plus d’informations, consultez [Déboguer des applications ASP.NET en production avec le débogueur de capture instantanée](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Examiner des captures instantanÃ©es avec le retour en arriÃ¨re IntelliTrace (Visual Studio Enterprise)

Le **retour en arrière IntelliTrace** crée automatiquement une capture instantanée de votre application à chaque événement de point d’arrêt et d’étape du débogueur. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils de débogage. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**.

![Avancez les boutons vers lâ€™arriÃ¨re et vers lâ€™avant](../debugger/media/intellitrace-step-back-icons-description.png  "Avancez vers lâ€™arriÃ¨re et en avant")

Pour plus d’informations, consultez la page [Inspecter les états antérieurs de l’application avec IntelliTrace](../debugger/view-historical-application-state.md).

## <a name="debug-performance-issues"></a>ProblÃ¨mes de performance Debug

Si votre application sâ€™exÃ©cute trop lentement ou utilise trop de mÃ©moire, vous devrez peut-Ãªtre tester votre application avec les outils de profilage dÃ¨s le dÃ©but. Pour plus dâ€™informations sur les outils de profilage tels que lâ€™outil dâ€™utilisation du processeur et lâ€™analyseur de mÃ©moire, voir [dâ€™abord les outils de profilage](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez vu rapidement de nombreuses fonctionnalités du débogueur. Pour plus d’informations sur l’une de ces fonctionnalités en particulier, et notamment les points d'arrêt :

> [!div class="nextstepaction"]
> [Apprendre à utiliser les points d’arrêt](../debugger/using-breakpoints.md)
