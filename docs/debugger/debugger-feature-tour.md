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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5bfa190f3bbc2a4f8b34d42d62b0ccc9b293674a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873130"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Premier aperçu du débogueur Visual Studio

Cette rubrique présente les outils du débogueur fournis par Visual Studio. Dans le contexte Visual Studio, quand vous *déboguez votre application*, cela signifie généralement que vous exécutez votre application en y ayant attaché le débogueur (c’est-à-dire en mode Débogueur). Quand vous faites cela, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant qu’il s’exécute. Vous pouvez parcourir votre code et examiner les valeurs stockées dans des variables, vous pouvez définir des espions sur des variables pour voir quand les valeurs changent, vous pouvez examiner le chemin d’exécution de votre code, et al. S’il s’agit de la première fois que vous tentez de déboguer du code, vous souhaiterez peut-être lire [débogage pour les débutants absolus](../debugger/debugging-absolute-beginners.md) avant de passer par cette rubrique.

Les fonctionnalités décrites ici sont applicables à C#, C++, Visual Basic, JavaScript et à d’autres langages pris en charge par Visual Studio (sauf indication contraire).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrer le débogueur

Pour déboguer, vous devez démarrer votre application avec le débogueur attaché au processus de l’application. **F5** (**Déboguer > Démarrer le débogage**) est l’approche la plus courante pour faire cela. Cependant, vous n’avez peut-être pas encore défini de points d’arrêt pour examiner le code de votre application : nous commençons donc par cela, puis nous démarrons le débogage. Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

Si vous avez un fichier ouvert dans l’éditeur de code, vous pouvez définir un point d’arrêt en cliquant dans la marge à gauche d’une ligne de code.

![Définir un point d’arrêt](../debugger/media/dbg-tour-set-a-breakpoint.gif "Définir un point d'arrêt")

Appuyez sur **F5** (**déboguer > démarrer le débogage**) ou sur le bouton **Démarrer** le débogage ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage") dans la barre d’outils déboguer, et le débogueur s’exécute jusqu’au premier point d’arrêt qu’il rencontre. Si l’application n’est pas déjà en cours d’exécution, F5 démarre le débogueur et s’arrête au premier point d’arrêt.

Les points d’arrêt sont une fonctionnalité pratique quand vous savez quelle ligne de code ou section de code vous voulez examiner en détail.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Parcourir le code dans le débogueur à l’aide des commandes Step

Nous fournissons les raccourcis clavier pour la plupart des commandes, car ils rendent plus rapide la navigation dans le code de votre d’application. (Les commandes équivalentes, comme les commandes des menus, sont données entre parenthèses.)

Pour démarrer votre application avec le débogueur attaché, appuyez sur **F11** (**Déboguer > Pas à pas détaillé**). F11 est la commande **Pas à pas détaillé** : elle fait avancer l’exécution de l’application une instruction à la fois. Quand vous démarrez l’application avec F11, le débogueur s’arrête sur la première instruction exécutée.

![F11 pas à pas détaillé](../debugger/media/dbg-tour-f11.png "F11 pas à pas détaillé")

La flèche jaune représente l’instruction sur laquelle le débogueur s’est mis en pause, ce qui interrompt également l’exécution de l’application au même point (cette instruction n’a pas encore été exécutée).

F11 est un bon moyen pour examiner le flux de l’exécution de la façon la plus détaillée. (Pour aller plus rapidement dans le code, nous vous présentons également d’autres options.) Par défaut, le débogueur ignore le code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon code](../debugger/just-my-code.md)).

>[!NOTE]
> Dans le code managé, vous voyez une boîte de dialogue vous demandant si vous voulez être averti quand vous effectuez automatiquement un pas à pas principal dans les propriétés et les opérateurs (le comportement par défaut). Si vous voulez changer ce paramètre ultérieurement, désactivez le paramètre **Pas à pas principal dans les propriétés et les opérateurs** dans le menu **Outils > Options** sous **Débogage**.

## <a name="step-over-code-to-skip-functions"></a>Effectuer un pas à pas principal dans le code pour ignorer les fonctions

Quand vous êtes sur une ligne de code qui est un appel de fonction ou de méthode, vous pouvez appuyer sur **F10** (**Déboguer > Pas à pas principal**) au lieu de F11.

F10 fait avancer le débogueur sans effectuer de pas à pas détaillé dans les fonctions ou les méthodes du code de votre application (le code s’exécute néanmoins). En appuyant sur F10, vous pouvez ignorer le code qui ne vous intéresse pas. De cette façon, vous pouvez rapidement accéder au code qui vous intéresse le plus.

## <a name="step-into-a-property"></a>Pas à pas détaillé d’une propriété

Comme mentionné précédemment, par défaut, le débogueur ignore les propriétés et les champs managés, mais la commande **Pas à pas détaillé spécifique** vous permet de remplacer ce comportement.

Cliquez avec le bouton droit sur une propriété ou un champ, et choisissez **Pas à pas détaillé spécifique**, puis choisissez une des options disponibles.

![Capture d’écran du débogueur Visual Studio avec une ligne de code mise en surbrillance. Pas à pas détaillé spécifique est sélectionné dans le menu contextuel, et la méthode path. Set est sélectionnée.](../debugger/media/dbg-tour-step-into-specific.png)

Dans cet exemple, **Pas à pas détaillé spécifique** nous amène au code pour `Path.set`.

![Capture d’écran du débogueur Visual Studio montrant le code pour Path. Set. Les accolades entourant la fonction Set sont mises en surbrillance en jaune.](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Exécuter rapidement jusqu’à un point dans votre code avec la souris

Dans le débogueur, placez le curseur sur une ligne de code jusqu’à la capture d’écran du bouton Exécuter pour **Cliquer** (exécuter l’exécution jusqu’ici) ![ du bouton Exécuter pour cliquer à partir du débogueur Visual Studio. Le bouton indique que l’exécution doit s’exécuter jusqu’à la ligne où le bouton est placé.](../debugger/media/dbg-tour-run-to-click.png) s’affiche à gauche.

![Capture d’écran du débogueur Visual Studio montrant que le bouton Exécuter jusqu’au clic s’affiche juste à gauche d’un appel à la fonction de mise à jour.](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> Le bouton **Exécuter jusqu’au clic** (Exécuter l’exécution jusqu’ici) est disponible à compter de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Cliquez sur le bouton **Exécuter jusqu’au clic** (Exécuter l’exécution jusqu’ici). Le débogueur avance jusqu’à la ligne de code où vous avez cliqué.

L’utilisation de ce bouton revient à définir un point d’arrêt temporaire. Cette commande est également pratique pour parcourir rapidement une zone visible du code d’application. Vous pouvez utiliser **Exécuter jusqu’au clic** dans n’importe quel fichier ouvert.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Faire avancer le débogueur en dehors de la fonction active

Parfois, vous voulez continuer votre session de débogage, mais faire avancer le débogueur en dehors de la fonction active.

Appuyez sur **Maj+F11** (**ou Déboguer > Pas à pas sortant**).

Cette commande reprend l’exécution de l’application (et fait avancer le débogueur) jusqu’au retour de la fonction active.

## <a name="run-to-cursor"></a>Exécuter jusqu'au curseur

Lorsque vous modifiez du code (au lieu d’être suspendu dans le débogueur), cliquez avec le bouton droit sur une ligne de code dans votre application, puis choisissez **Exécuter jusqu’au curseur** (ou appuyez sur **CTRL** pour **F10**). Cette commande démarre le débogage et définit un point d’arrêt temporaire sur la ligne de code active.

![Exécuter jusqu’au curseur](../debugger/media/dbg-tour-run-to-cursor.png "Exécuter jusqu'au curseur")

Si vous avez défini des points d’arrêt, le débogueur se met en pause sur le premier point d’arrêt qu’il atteint.

Appuyez sur **F5** jusqu’à atteindre la ligne de code où vous avez sélectionné **Exécuter jusqu’au curseur**.

Cette commande est pratique quand vous modifiez du code, et que vous voulez définir rapidement un point d’arrêt temporaire et démarrer en même temps le débogueur.

> [!NOTE]
> Vous pouvez utiliser **Exécuter jusqu’au curseur** dans la fenêtre **Pile des appels** pendant que vous déboguez.

## <a name="restart-your-app-quickly"></a>Redémarrer rapidement votre application

Cliquez sur le bouton **redémarrer** l' ![application de redémarrage](../debugger/media/dbg-tour-restart.png "Redémarrer l’application") dans la barre d’outils déboguer (ou appuyez sur **Ctrl + Maj + F5**).

Quand vous appuyez sur **Redémarrer**, vous gagnez du temps par rapport à l’action consistant à arrêter l’application, puis à redémarrer le débogueur. Le débogueur se met en pause sur le premier point d’arrêt qui est atteint par l’exécution du code.

Si vous ne souhaitez pas arrêter le débogueur et revenir à l’éditeur de code, vous pouvez appuyer sur le bouton rouge arrêter le ![débogage](../debugger/media/dbg-tour-stop-debugging.png "Arrêter le débogage") au lieu de **redémarrer**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Modifier votre code et continuer le débogage (C#, VB, C++, XAML)

Dans la plupart des langages pris en charge par Visual Studio, vous pouvez modifier votre code au milieu d’une session de débogage et poursuivre le débogage. Pour utiliser cette fonctionnalité, cliquez sur votre code à l’aide de votre curseur tout en étant suspendu dans le débogueur, apportez des modifications, puis appuyez sur **F5**, **F10** ou **F11** pour continuer le débogage.

![Modifier & continuer le débogage](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Pour plus d’informations sur l’utilisation de la fonctionnalité et sur les limitations relatives aux fonctionnalités, consultez [modifier & continuer](../debugger/edit-and-continue.md).

Pour modifier le code XAML pendant une session de débogage, consultez [écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations (datatips)

Maintenant que vous vous débrouillez un peu, vous pouvez commencer à examiner l’état de votre application (ses variables) avec le débogueur. Les fonctionnalités qui vous permettent d’inspecter des variables sont parmi les plus pratiques du débogueur : vous pouvez faire cela de différentes façons. Souvent, quand vous essayez de déboguer un problème, vous essayez de déterminer si les variables stockent les valeurs que vous prévoyez dans un état donné de l’application.

Avec l’exécution en pause dans le débogueur, placez le curseur sur un objet avec la souris : vous voyez la valeur par défaut de sa propriété (dans cet exemple, le nom de fichier `market 031.jpg` est la valeur par défaut de la propriété).

![Afficher une bulle d’informations](../debugger/media/dbg-tour-data-tips.gif "Afficher une bulle d’informations")

Développez l’objet pour voir toutes ses propriétés (comme la propriété `FullPath` dans cet exemple).

Souvent, lors du débogage, vous voulez un moyen rapide de vérifier les valeurs des propriétés sur des objets : les datatips sont un bon moyen de le faire.

> [!TIP]
> Dans la plupart des langages pris en charge, vous pouvez modifier le code pendant une session de débogage. Pour plus d’informations, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les Fenêtres Automatique et Variables locales

Pendant le débogage, examinez la fenêtre **Automatique** en bas de l’éditeur de code.

![Fenêtre automatique](../debugger/media/dbg-tour-autos-window.png "Automatique (fenêtre)")

Dans la fenêtre **Automatique**, vous voyez des variables, avec leur valeur actuelle et leur type. La fenêtre **Automatique** montre toutes les variables utilisées dans la ligne active ou la ligne précédente (en C++, la fenêtre montre les variables des trois lignes de code précédentes ; consultez la documentation pour les comportements selon le langage).

> [!NOTE]
> En JavaScript, la fenêtre **Variables locales** est prise en charge, mais pas la fenêtre **Automatique**.

Ensuite, examinez la fenêtre **Variables locales**. La fenêtre **Variables locales** vous montre les variables qui se trouvent actuellement dans l’étendue.

![Variables locales (fenêtre)](../debugger/media/dbg-tour-locals-window.png "Fenêtre Variables locales")

Dans cet exemple, l’objet `this` et l’objet `f` sont dans l’étendue. Pour plus d’informations, consultez [Inspecter les variables dans les fenêtres Automatique et Variables locales](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Définir un espion

Vous pouvez utiliser une fenêtre **Espion** pour spécifier une variable (ou une expression) que vous voulez observer.

Pendant le débogage, cliquez avec le bouton droit sur un objet et choisissez **Ajouter un espion**.

![Espion (fenêtre)](../debugger/media/dbg-tour-watch-window.png "Fenêtre Espion")

Dans cet exemple, vous avez un espion défini sur l’objet `f` et vous pouvez voir sa valeur changer au fil de votre déplacement dans le débogueur. Contrairement à d’autres fenêtres de variables, la fenêtre **Espion** montre toujours les variables que vous observez (elles apparaissent en grisé quand elles sont en dehors de l’étendue).

Pour plus d’informations, consultez [Définir un espion avec les Fenêtres Espion et Espion express](../debugger/watch-and-quickwatch-windows.md).

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

Pendant que vous déboguez, cliquez sur la fenêtre **Pile des appels**, qui est ouverte par défaut dans le volet inférieur droit.

![Examiner la pile des appels](../debugger/media/dbg-tour-call-stack.png "Examiner la pile des appels")

La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La ligne du haut montre la fonction active (dans cet exemple, la méthode `Update`). La deuxième ligne montre que `Update` a été appelée depuis la propriété `Path.set`, etc. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

> [!NOTE]
> La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

Vous pouvez double-cliquer sur une ligne de code pour accéder à ce code source ; ceci change également l’étendue active inspectée par le débogueur. Ceci ne fait pas avancer le débogueur.

Vous pouvez également utiliser les menus contextuels de la fenêtre **Pile des appels** pour faire d’autres choses. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiques, redémarrer votre application avec **Exécuter jusqu’au curseur** et aller examiner le code source. Consultez [Guide pratique pour examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a> Examiner une exception

Quand votre application lève une exception, le débogueur vous amène à la ligne de code qui a levé cette exception.

![Assistance d’exception](../debugger/media/dbg-tour-exception-helper.png "Assistance d’exception")

Dans cet exemple, **l’Assistance sur l’exception** vous montre une exception `System.Argument` et un message d’erreur indiquant que le chemin n’est pas d’une forme autorisée. Ainsi, nous savons que l’erreur s’est produite sur l’argument d’une méthode ou d’une fonction.

Dans cet exemple, l’appel de `DirectoryInfo` a provoqué l’erreur sur la chaîne vide, stockée dans la variable `value`.

L’Assistance sur l’exception est une fonctionnalité intéressante qui peut vous aider à déboguer des erreurs. Vous pouvez également examiner les détails de l’erreur et ajouter un espion à partir de l’Assistance sur l’exception. Si nécessaire, vous pouvez aussi changer les conditions pour lever une exception donnée. Pour plus d’informations sur la prise en charge des exceptions dans le code, consultez [Techniques et outils de débogage](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> L’Assistance Exception remplace l’Assistant Exception à compter de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Développez le nœud **Paramètres d’exception** pour voir plus d’options sur la façon de gérer ce type d’exception ; dans le cadre de cette visite guidée, vous ne devez néanmoins rien changer !

## <a name="configure-debugging"></a>Configurer le débogage

Vous pouvez configurer votre projet pour qu’il soit généré comme une [configuration Debug ou Release](../debugger/how-to-set-debug-and-release-configurations.md), configurer des propriétés de projet pour le débogage ou configurer des [paramètres généraux pour le](../debugger/how-to-specify-debugger-settings.md) débogage. En outre, vous pouvez configurer le débogueur pour afficher des informations personnalisées à l’aide de fonctionnalités telles que l’attribut [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) ou, pour C/C++, l' [infrastructure NatVis](create-custom-views-of-native-objects.md).

Les propriétés de débogage sont spécifiques à chaque type de projet. Par exemple, vous pouvez spécifier un argument à passer à l’application lorsque vous la démarrez. Vous pouvez accéder aux propriétés spécifiques au projet en cliquant avec le bouton droit sur le projet dans Explorateur de solutions et en sélectionnant **Propriétés**. Les propriétés de débogage apparaissent généralement sous l’onglet **générer** ou **Déboguer** , en fonction du type de projet particulier.

![Propriétés d’un projet](../debugger/media/dbg-tour-project-properties.png "Propriétés d’un projet")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Déboguer des applications ASP.NET en production dans Azure App Service

le **débogueur de capture instantanée** prend un instantané de vos applications en production lorsque le code qui vous intéresse s’exécute. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

![Lancer le Débogueur de capture instantanée](../debugger/media/snapshot-launch.png "Lancer le Débogueur de capture instantanée")

La collecte de captures instantanées est disponible pour les applications ASP.NET qui s’exécutent dans Azure App Service. Les applications ASP.NET doivent s’exécuter sur le .NET Framework 4.6.1 ou ultérieur, et les applications ASP.NET Core doivent s’exécuter sur .NET Core 2.0 ou ultérieur sur Windows.

Pour plus d’informations, consultez [Déboguer des applications ASP.NET en production avec le débogueur de capture instantanée](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Examiner des captures instantanées avec le retour en arrière IntelliTrace (Visual Studio Enterprise)

Le **retour en arrière IntelliTrace** crée automatiquement une capture instantanée de votre application à chaque événement de point d’arrêt et d’étape du débogueur. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils de débogage. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**.

![Boutons précédent et suivant](../debugger/media/intellitrace-step-back-icons-description.png  "Boutons précédent et suivant")

Pour plus d’informations, consultez la page [Inspecter les états antérieurs de l’application avec IntelliTrace](../debugger/view-historical-application-state.md).

## <a name="debug-performance-issues"></a>Problèmes de performances de débogage

Si votre application s’exécute trop lentement ou utilise trop de mémoire, vous devrez peut-être tester votre application avec les outils de profilage au plus tôt. Pour plus d’informations sur les outils de profilage, tels que l’outil utilisation de l’UC et l’analyseur de mémoire, consultez [tout d’abord les outils de profilage](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez vu rapidement de nombreuses fonctionnalités du débogueur. Pour plus d’informations sur l’une de ces fonctionnalités en particulier, et notamment les points d'arrêt :

> [!div class="nextstepaction"]
> [Apprendre à utiliser les points d’arrêt](../debugger/using-breakpoints.md)
