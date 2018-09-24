---
title: Commencer le débogage dans Visual Studio 2017
description: Commencer le débogage des applications à l’aide du débogueur Visual Studio
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2339dcfe80e994b8bc9062d137263d3b25d274d
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542414"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Tout d’abord examiner le débogueur Visual Studio

Cette rubrique présente les outils de débogueur fournis par Visual Studio. Dans le contexte de Visual Studio, lorsque vous *déboguer votre application*, cela signifie généralement que vous exécutez l’application avec le débogueur attaché (autrement dit, en mode débogage). Lorsque vous effectuez cette opération, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant son exécution. Vous pouvez parcourir votre code et examinez les valeurs stockées dans des variables, vous pouvez définir des observations sur les variables pour voir lorsque les valeurs changent, vous pouvez examiner le chemin d’accès de l’exécution de votre code, et al. S’il s’agit de la première fois que vous avez essayé de déboguer du code, il pouvez que vous souhaitez lire [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de passer par cette rubrique.

Les fonctionnalités décrites ici sont applicables à C#, C++, Visual Basic, JavaScript et d’autres langages pris en charge par Visual Studio (sauf mention contraire).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définissez un point d’arrêt et démarrez le débogueur

Pour déboguer, vous devez démarrer votre application avec le débogueur attaché au processus de l’application. **F5** (**Déboguer > Démarrer le débogage**) est l’approche la plus courante pour ce faire. Toutefois, vous n’avez peut-être pas encore défini de points d’arrêt pour examiner le code de votre application : nous allons donc commencer par cela, pour ensuite démarrer le débogage. Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. 

Si vous avez un fichier ouvert dans l’éditeur de code, vous pouvez définir un point d’arrêt en cliquant dans la marge à gauche d’une ligne de code.

![Définissez un point d’arrêt](../debugger/media/dbg-tour-set-a-breakpoint.gif "définir un point d’arrêt")

Appuyez sur **F5** (**Déboguer > Démarrer le débogage**) ou le **démarrer le débogage** bouton ![démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "démarrer le débogage ") dans la barre d’outils de débogage et l’exécution du débogueur pour le premier point d’arrêt qu’il rencontre. Si l’application n’est pas encore en cours d’exécution, F5 démarre le débogueur et s’arrête au premier point d’arrêt.

Les points d’arrêt sont une fonctionnalité utile quand vous savez quelle ligne ou section de code vous voulez examiner en détail.

## <a name="navigate"></a> Parcourir le code dans le débogueur à l’aide des commandes de l’étape

Nous fournissons des raccourcis clavier pour la plupart des commandes car elles rendent la navigation dans le code de votre application plus rapide. (Les équivalents des commandes telles que les commandes de menu sont indiqués entre parenthèses.)

Pour démarrer votre application avec le débogueur attaché, appuyez sur **F11** (**Déboguer > pas à pas détaillé**). F11 est la commande **pas à pas détaillé** et elle exécute l'application une instruction à la fois. Lorsque vous démarrez l’application en appuyant sur F11, le débogueur s’arrête à la première instruction exécutée.

![F11 Pas à pas détaillé](../debugger/media/dbg-tour-f11.png "F11 pas à pas détaillé")

La flèche jaune représente l’instruction sur laquelle le débogueur a suspendu, ce qui interrompt également l’exécution d’application au même moment (cette instruction n’a pas encore exécuté).

F11 est une bonne solution pour examiner le flux d’exécution en détails. (Pour se déplacer plus rapidement dans le code, nous vous montrerons d’autres options.) Par défaut, le débogueur ignore le code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon Code](../debugger/just-my-code.md)).

>[!NOTE]
> Dans le code managé, vous verrez une boîte de dialogue vous demandant si vous souhaitez être averti quand vous effectuez automatiquement un pas à pas dans les propriétés et les opérateurs (le comportement par défaut). Si vous voulez changer cette option plus tard, désactivez **Pas à pas principal dans les propriétés et les opérateurs** dans le menu **Outils > Options** sous **Débogage**.

## <a name="step-over-code-to-skip-functions"></a>Ignorer le code pour ignorer les fonctions

Lorsque vous êtes sur une ligne de code qui est un appel de fonction ou une méthode, vous pouvez appuyer sur **F10** (**Déboguer > pas à pas principal**) au lieu de F11.

F10 fait avancer le débogueur sans entrer dans les fonctions ou méthodes dans votre code d’application (le code s’exécute toujours). En appuyant sur F10, vous pouvez ignorer le code qui vous n'intéressent pas. De cette façon, vous pouvez obtenir rapidement au code qui vous intéressent le plus.

## <a name="step-into-a-property"></a>Pas à pas détaillé d’une propriété

Comme mentionné précédemment, par défaut, le débogueur ignore les propriétés et les champs managés, mais la commande **Pas à pas détaillé spécifique** vous permet de substituer ce comportement.

Cliquez avec le bouton droit sur une propriété ou un champ et choisissez **Pas à pas détaillé spécifique**, puis choisissez une des options disponibles.

![Pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific.png "pas à pas détaillé spécifique")

Dans cet exemple, **Pas à pas détaillé spécifique** nous amène au code correspondant à `Path.set`.

![Pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific-2.png "pas à pas détaillé spécifique")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Exécuter à un point dans votre code rapidement à l’aide de la souris

Lorsque vous êtes dans le débogueur, pointez sur une ligne de code jusqu'à ce que le bouton **Exécuter jusqu'au clic** (Exécuter l’exécution jusqu’ici) ![Exécuter jusqu'au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaisse à gauche.

![Exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click-2.png "exécuter jusqu’au clic")

> [!NOTE]
> Le bouton **Exécuter jusqu'au clic** (Exécuter l'exécution jusqu’ici) est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Cliquez sur le bouton **Exécuter jusqu'au clic** (Exécuter l'exécution jusqu’ici). Le débogueur passe à la ligne de code où vous avez cliqué.

L’utilisation de ce bouton est similaire à la définition d’un point d’arrêt temporaire. Cette commande est également pratique pour se déplacer rapidement au sein de la région visible du code d’application. Vous pouvez utiliser le bouton **Exécuter jusqu'au clic** dans un fichier ouvert.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Faire avancer le débogueur en dehors de la fonction Active

Parfois, vous souhaiterez continuer votre session de débogage mais faire avancer le débogueur tout au long de la fonction active.

Appuyez sur **MAJ + F11** (ou **Déboguer > pas à pas sortant**).

Cette commande reprend l’exécution d’application (et avance le débogueur) jusqu'à ce que retourne la fonction active.

## <a name="run-to-cursor"></a>Exécuter jusqu'au curseur

Arrêtez le débogueur en appuyant sur la **arrêter le débogage** bouton rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") ou **MAJ**  +  **F5**.

Cliquez sur une ligne de code dans votre application et choisissez **exécuter jusqu’au curseur**. Cette commande démarre le débogage et définit un point d’arrêt temporaire sur la ligne de code active.

![Exécuter jusqu’au curseur](../debugger/media/dbg-tour-run-to-cursor.png "exécuter jusqu’au curseur")

Si vous avez défini des points d’arrêt, le débogueur s’arrête sur le premier point d’arrêt il atteint.

Appuyez sur **F5** jusqu'à ce que vous atteigniez la ligne de code où vous avez sélectionné **exécuter jusqu’au curseur**.

Cette commande est utile lorsque vous modifiez du code et que vous souhaitez définir un point d’arrêt temporaire rapidement et de démarrer le débogueur en même temps.

> [!NOTE]
> Vous pouvez utiliser **exécuter jusqu’au curseur** dans le **pile des appels** fenêtre pendant le débogage.

## <a name="restart-your-app-quickly"></a>Redémarrez votre application rapidement

Cliquez sur le **redémarrer** ![redémarrer une application](../debugger/media/dbg-tour-restart.png "redémarrer une application") bouton dans la barre d’outils déboguer (**Ctrl + Maj + F5**).

Quand vous appuyez sur **redémarrer**, il fait gagner du temps par rapport à l’arrêt de l’application et de redémarrer le débogueur. Le débogueur s’arrête sur le premier point d’arrêt est atteint par l’exécution de code.

Si vous ne souhaitez pas arrêter le débogueur et revenir à l’éditeur de code, vous pouvez appuyer sur le taquet rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") bouton au lieu de **redémarrer**.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations

Maintenant que vous connaissez un peu à votre rythme, vous avez une bonne occasion pour commencer à examiner l’état de votre application (variables) avec le débogueur. Les fonctionnalités qui vous permettent d’inspecter les variables sont quelques-unes des fonctionnalités plus utiles du débogueur, et il existe différentes manières de procéder. Souvent, lorsque vous essayez de déboguer un problème, vous essayez de déterminer si les variables sont stocker les valeurs que vous attendez d’elles dans un état d’application particulier.

Pendant la suspension dans le débogueur, placez le curseur sur un objet avec la souris et que sa valeur de propriété par défaut (dans cet exemple, le nom de fichier `market 031.jpg` est la valeur de propriété par défaut).

![Afficher une bulle](../debugger/media/dbg-tour-data-tips.gif "afficher une info-bulle de données")

Développez l’objet pour voir toutes ses propriétés (telles que le `FullPath` propriété dans cet exemple).

Souvent, lors du débogage, vous souhaitez un moyen rapide de vérifier les valeurs de propriété sur les objets et les conseils de données constituent un bon moyen de le faire.

> [!TIP]
> Dans les langues prises en charge de plus, vous pouvez modifier le code au milieu d’une session de débogage. Pour plus d’informations, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les fenêtres automatique et variables locales

Pendant le débogage, examinez le **automatique** fenêtre en bas de l’éditeur de code.

![Automatique fenêtre](../debugger/media/dbg-tour-autos-window.png "fenêtre automatique")

Dans le **automatique** , vous devez voir variables le long de leur valeur actuelle et leur type. Le **automatique** fenêtre affiche toutes les variables utilisées dans la ligne actuelle ou de la ligne précédente (en C++, la fenêtre affiche les variables dans les trois lignes de code précédents. Consultez la documentation pour le comportement spécifique à la langue).

> [!NOTE]
> Dans JavaScript, le **variables locales** fenêtre est pris en charge, mais pas le **automatique** fenêtre.

Ensuite, examinons le **variables locales** fenêtre. Le **variables locales** fenêtre vous montre les variables qui sont actuellement dans la portée.

![Fenêtre variables locales](../debugger/media/dbg-tour-locals-window.png "fenêtre variables locales")

Dans cet exemple, le `this` objet et l’objet `f` sont dans la portée. Pour plus d’informations, consultez [inspecter des Variables dans le Windows de variables locales et automatique](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Définir un espion

Vous pouvez utiliser un **espion** fenêtre pour spécifier une variable (ou une expression) que vous souhaitez garder un œil sur.

Pendant le débogage, cliquez sur un objet et choisissez **ajouter un espion**.

![Fenêtre Espion](../debugger/media/dbg-tour-watch-window.png "fenêtre Espion")

Dans cet exemple, vous avez un espion défini sur le `f` objet et vous pouvez voir sa valeur changent à mesure que vous parcourez le débogueur. Contrairement à d’autres fenêtres de variables, le **espion** windows toujours affichent les variables que vous surveillez (elles sont grisées lorsque hors de portée).

Pour plus d’informations, consultez [définir un espion à l’aide d’espion et Espion express Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

Cliquez sur le **pile des appels** fenêtre pendant le débogage, ce qui est par défaut ouvert dans le volet inférieur droit.

![Examiner la pile des appels](../debugger/media/dbg-tour-call-stack.png "examiner la pile des appels")

Le **pile des appels** fenêtre indique l’ordre dans lequel les méthodes et les fonctions sont bien appelées. La première ligne affiche la fonction active (la `Update` méthode dans cet exemple). La deuxième ligne montre que `Update` a été appelée à partir de la `Path.set` propriété et ainsi de suite. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

> [!NOTE]
> Le **pile des appels** est identique à la perspective de débogage dans certains IDE comme Eclipse.

Vous pouvez double-cliquer sur une ligne de code revenir sur ce code source et qui modifie également la portée actuelle est inspectée par le débogueur. Cela n’avance pas le débogueur.

Vous pouvez également utiliser les menus contextuels à partir de la **pile des appels** fenêtre pour faire autre chose. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiques, redémarrez votre application à l’aide **exécuter jusqu’au curseur**et accéder à examiner le code source. Consultez [Comment : examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Examiner une exception

Lorsque votre application lève une exception, le débogueur vous amène directement à la ligne de code qui a levé l’exception.

![Assistance d’exception](../debugger/media/dbg-tour-exception-helper.png "assistance d’Exception")

Dans cet exemple, le **assistance d’Exception** vous montre une `System.Argument` exception et un message d’erreur indiquant que le chemin d’accès n’est pas une forme conforme. Par conséquent, nous savons que l’erreur s’est produite sur un argument de méthode ou fonction.

Dans cet exemple, le `DirectoryInfo` appelle a donné l’erreur sur la chaîne vide, stockée dans le `value` variable.

L’assistance de l’Exception est une fonctionnalité intéressante qui peut vous aider à déboguer les erreurs. Vous pouvez également effectuer des opérations comme vue Détails de l’erreur et ajouter un espion à partir de l’assistance de l’Exception. Ou, si nécessaire, vous pouvez modifier les conditions pour lever l’exception particulière.

>  [!NOTE]
> L’assistance d’Exception remplace l’Assistant Exception dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Développez le **paramètres d’Exception** nœud pour afficher davantage d’options sur la gestion de ce type d’exception, mais vous n’avez pas besoin de modifier quoi que ce soit pour cette visite guidée !

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Déboguer des applications ASP.NET en production dans Azure App Service

le **débogueur de capture instantanée** prend un instantané de vos applications de production lors de l’exécution de code qui vous intéresse. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

![Lancer le débogueur de capture instantanée](../debugger/media/snapshot-launch.png "lancer le débogueur de capture instantanée")

Collecte de captures instantanées est disponible pour les applications ASP.NET exécutées dans Azure App Service. Les applications ASP.NET doivent s’exécuter sur .NET Framework 4.6.1 ou version ultérieure, et les applications ASP.NET Core doivent s’exécuter sur .NET Core 2.0 ou version ultérieure sur Windows.

Pour plus d’informations, consultez [déboguer des applications ASP.NET en production à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Afficher les instantanés en arrière IntelliTrace (Visual Studio Enterprise)

**En arrière IntelliTrace** prend automatiquement un instantané de votre application à chaque point d’arrêt et le débogueur événement d’étape. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils de débogage. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**.

![Étape vers l’arrière et vers l’avant](../debugger/media/intellitrace-step-back-icons-description.png  "boutons étape précédente et étape suivante")

Pour plus d’informations, consultez le [Inspecter les États d’application précédent à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md) page.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez vu rapidement de nombreuses fonctionnalités du débogueur. Vous pouvez voir ces fonctionnalités plus en détail avec un exemple d’application

> [!div class="nextstepaction"]
> [Apprendre à déboguer avec Visual Studio](../debugger/getting-started-with-the-debugger.md)
