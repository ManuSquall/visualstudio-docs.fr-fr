---
title: Bien démarrer avec le débogage dans Visual Studio 2017
description: Bien démarrer avec le débogage d’applications en utilisant le débogueur Visual Studio
ms.custom: mvc
ms.date: 06/15/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf7bcba0ceaa71b933d4875cd5eee28d7cea0028
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904966"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Premier aperçu du débogueur Visual Studio

Cette rubrique présente les outils du débogueur fournis par Visual Studio. Dans le contexte Visual Studio, quand vous *déboguez votre application*, cela signifie généralement que vous exécutez votre application en y ayant attaché le débogueur (c’est-à-dire en mode Débogueur). Quand vous faites cela, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant qu’il s’exécute. Vous pouvez parcourir votre code pas à pas et examiner les valeurs stockées dans les variables, vous pouvez définir des espions sur des variables pour voir quand les valeurs changent, vous pouvez examiner le chemin d’exécution de votre code, etc. Si c’est la première fois que vous essayez de déboguer du code, vous pouvez lire [Débogage pour grands débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cette rubrique.

Les fonctionnalités décrites ici sont applicables à C#, C++, Visual Basic, JavaScript et à d’autres langages pris en charge par Visual Studio (sauf indication contraire).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrer le débogueur

Pour déboguer, vous devez démarrer votre application avec le débogueur attaché au processus de l’application. **F5** (**Déboguer > Démarrer le débogage**) est l’approche la plus courante pour faire cela. Cependant, vous n’avez peut-être pas encore défini de points d’arrêt pour examiner le code de votre application : nous commençons donc par cela, puis nous démarrons le débogage. Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. 

Si vous avez un fichier ouvert dans l’éditeur de code, vous pouvez définir un point d’arrêt en cliquant dans la marge à gauche d’une ligne de code.

![Définir un point d’arrêt](../debugger/media/dbg-tour-set-a-breakpoint.gif "Définir un point d’arrêt")

Appuyez sur **F5** (**Déboguer > Démarrer le débogage**) ou sur le bouton **Démarrer le débogage** ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage ") dans la barre d’outils Débogage : le débogueur s’exécute jusqu’au premier point d’arrêt qu’il rencontre. Si l’application n’est pas déjà en cours d’exécution, F5 démarre le débogueur et s’arrête au premier point d’arrêt.

Les points d’arrêt sont une fonctionnalité pratique quand vous savez quelle ligne de code ou section de code vous voulez examiner en détail.

## <a name="navigate"></a> Parcourir le code dans le débogueur avec les commandes d’exécution pas à pas

Nous fournissons les raccourcis clavier pour la plupart des commandes, car ils rendent plus rapide la navigation dans le code de votre d’application. (Les commandes équivalentes, comme les commandes des menus, sont données entre parenthèses.)

Pour démarrer votre application avec le débogueur attaché, appuyez sur **F11** (**Déboguer > Pas à pas détaillé**). F11 est la commande **Pas à pas détaillé** : elle fait avancer l’exécution de l’application une instruction à la fois. Quand vous démarrez l’application avec F11, le débogueur s’arrête sur la première instruction exécutée.

![F11 Pas à pas détaillé](../debugger/media/dbg-tour-f11.png "F11 Pas à pas détaillé")

La flèche jaune représente l’instruction sur laquelle le débogueur s’est mis en pause, ce qui interrompt également l’exécution de l’application au même point (cette instruction n’a pas encore été exécutée).

F11 est un bon moyen pour examiner le flux de l’exécution de la façon la plus détaillée. (Pour avancer plus rapidement dans le code, il existe d’autres options, que nous allons vous montrer.) Par défaut, le débogueur ignore le code non-utilisateur (si vous voulez plus d’informations, consultez [Uniquement mon code](../debugger/just-my-code.md)).

>[!NOTE]
> Dans le code managé, vous voyez une boîte de dialogue vous demandant si vous voulez être averti quand vous effectuez automatiquement un pas à pas principal dans les propriétés et les opérateurs (le comportement par défaut). Si vous voulez changer ce paramètre ultérieurement, désactivez le paramètre **Pas à pas principal dans les propriétés et les opérateurs** dans le menu **Outils > Options** sous **Débogage**.

## <a name="step-over-code-to-skip-functions"></a>Effectuer un pas à pas principal dans le code pour ignorer les fonctions

Quand vous êtes sur une ligne de code qui est un appel de fonction ou de méthode, vous pouvez appuyer sur **F10** (**Déboguer > Pas à pas principal**) au lieu de F11.

F10 fait avancer le débogueur sans effectuer de pas à pas détaillé dans les fonctions ou les méthodes du code de votre application (le code s’exécute néanmoins). En appuyant sur F10, vous pouvez ignorer le code qui ne vous intéresse pas. De cette façon, vous pouvez rapidement accéder au code qui vous intéresse le plus.

## <a name="step-into-a-property"></a>Pas à pas détaillé d’une propriété

Comme mentionné précédemment, par défaut, le débogueur ignore les propriétés et les champs managés, mais la commande **Pas à pas détaillé spécifique** vous permet de remplacer ce comportement.

Cliquez avec le bouton droit sur une propriété ou un champ, et choisissez **Pas à pas détaillé spécifique**, puis choisissez une des options disponibles.

![Pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific.png "Pas à pas détaillé spécifique")

Dans cet exemple, **Pas à pas détaillé spécifique** nous amène au code pour `Path.set`.

![Pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific-2.png "Pas à pas détaillé spécifique")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Exécuter rapidement jusqu’à un point dans votre code avec la souris

Dans le débogueur, placez le curseur sur une ligne de code jusqu’à ce que le bouton **Exécuter jusqu’au clic** (Exécuter l’exécution jusqu’ici) ![Exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaisse à gauche.

![Exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click-2.png "Exécuter jusqu’au clic")

> [!NOTE]
> Le bouton **Exécuter jusqu’au clic** (Exécuter l’exécution jusqu’ici) est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Cliquez sur le bouton **Exécuter jusqu’au clic** (Exécuter l’exécution jusqu’ici). Le débogueur avance jusqu’à la ligne de code où vous avez cliqué.

L’utilisation de ce bouton revient à définir un point d’arrêt temporaire. Cette commande est également pratique pour parcourir rapidement une zone visible du code d’application. Vous pouvez utiliser **Exécuter jusqu’au clic** dans n’importe quel fichier ouvert.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Faire avancer le débogueur en dehors de la fonction active

Parfois, vous voulez continuer votre session de débogage, mais faire avancer le débogueur en dehors de la fonction active.

Appuyez sur **Maj+F11** (**ou Déboguer > Pas à pas sortant**).

Cette commande reprend l’exécution de l’application (et fait avancer le débogueur) jusqu’au retour de la fonction active.

## <a name="run-to-cursor"></a>Exécuter jusqu'au curseur

Arrêtez le débogueur en appuyant sur le bouton d’arrêt rouge **Arrêter le débogage**![Arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "Arrêter le débogage") ou **Maj** + **F5**.

Cliquez avec le bouton droit sur une ligne de votre code d’application et choisissez **Exécuter jusqu’au curseur**. Cette commande démarre le débogage et définit un point d’arrêt temporaire sur la ligne de code active.

![Exécuter jusqu’au curseur](../debugger/media/dbg-tour-run-to-cursor.png "Exécuter jusqu’au curseur")

Si vous avez défini des points d’arrêt, le débogueur se met en pause sur le premier point d’arrêt qu’il atteint.

Appuyez sur **F5** jusqu’à atteindre la ligne de code où vous avez sélectionné **Exécuter jusqu’au curseur**.

Cette commande est pratique quand vous modifiez du code, et que vous voulez définir rapidement un point d’arrêt temporaire et démarrer en même temps le débogueur.

> [!NOTE]
> Vous pouvez utiliser **Exécuter jusqu’au curseur** dans la fenêtre **Pile des appels** pendant que vous déboguez.

## <a name="restart-your-app-quickly"></a>Redémarrer rapidement votre application

Cliquez sur le bouton **Redémarrer** ![Redémarrer l’application](../debugger/media/dbg-tour-restart.png "Redémarrer l’application") dans la barre d’outils Débogage (**Ctrl+Maj+F5**).

Quand vous appuyez sur **Redémarrer**, vous gagnez du temps par rapport à l’action consistant à arrêter l’application, puis à redémarrer le débogueur. Le débogueur se met en pause sur le premier point d’arrêt qui est atteint par l’exécution du code.

Si vous voulez arrêter le débogueur et revenir à l’éditeur de code, vous pouvez appuyer sur le bouton d’arrêt rouge ![Arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "Arrêter le débogage") au lieu de **Redémarrer**.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations (datatips)

Maintenant que vous vous débrouillez un peu, vous pouvez commencer à examiner l’état de votre application (ses variables) avec le débogueur. Les fonctionnalités qui vous permettent d’inspecter des variables sont parmi les plus pratiques du débogueur : vous pouvez faire cela de différentes façons. Souvent, quand vous essayez de déboguer un problème, vous essayez de déterminer si les variables stockent les valeurs que vous prévoyez dans un état donné de l’application.

Avec l’exécution en pause dans le débogueur, placez le curseur sur un objet avec la souris : vous voyez la valeur par défaut de sa propriété (dans cet exemple, le nom de fichier `market 031.jpg` est la valeur par défaut de la propriété).

![Afficher un datatip](../debugger/media/dbg-tour-data-tips.gif "Afficher un datatip")

Développez l’objet pour voir toutes ses propriétés (comme la propriété `FullPath` dans cet exemple).

Souvent, lors du débogage, vous voulez un moyen rapide de vérifier les valeurs des propriétés sur des objets : les datatips sont un bon moyen de le faire.

> [!TIP]
> Dans la plupart des langages pris en charge, vous pouvez modifier le code pendant une session de débogage. Pour plus d’informations, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les Fenêtres Automatique et Variables locales

Pendant le débogage, examinez la fenêtre **Automatique** en bas de l’éditeur de code.

![Fenêtre Automatique](../debugger/media/dbg-tour-autos-window.png "Fenêtre Automatique")

Dans la fenêtre **Automatique**, vous voyez des variables, avec leur valeur actuelle et leur type. La fenêtre **Automatique** montre toutes les variables utilisées dans la ligne active ou la ligne précédente (en C++, la fenêtre montre les variables des trois lignes de code précédentes ; consultez la documentation pour les comportements selon le langage).

> [!NOTE]
> En JavaScript, la fenêtre **Variables locales** est prise en charge, mais pas la fenêtre **Automatique**.

Ensuite, examinez la fenêtre **Variables locales**. La fenêtre **Variables locales** vous montre les variables qui se trouvent actuellement dans l’étendue.

![Fenêtre Variables locales](../debugger/media/dbg-tour-locals-window.png "Fenêtre Variables locales")

Dans cet exemple, l’objet `this` et l’objet `f` sont dans l’étendue. Pour plus d’informations, consultez [Inspecter les variables dans les fenêtres Automatique et Variables locales](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Définir un espion

Vous pouvez utiliser une fenêtre **Espion** pour spécifier une variable (ou une expression) que vous voulez observer.

Pendant le débogage, cliquez avec le bouton droit sur un objet et choisissez **Ajouter un espion**.

![Fenêtre Espion](../debugger/media/dbg-tour-watch-window.png "Fenêtre Espion")

Dans cet exemple, vous avez un espion défini sur l’objet `f` et vous pouvez voir sa valeur changer au fil de votre déplacement dans le débogueur. Contrairement à d’autres fenêtres de variables, la fenêtre **Espion** montre toujours les variables que vous observez (elles apparaissent en grisé quand elles sont en dehors de l’étendue).

Pour plus d’informations, consultez [Définir un espion avec les Fenêtres Espion et Espion express](../debugger/watch-and-quickwatch-windows.md).

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

Pendant que vous déboguez, cliquez sur la fenêtre **Pile des appels**, qui est ouverte par défaut dans le volet inférieur droit.

![Examiner la pile des appels](../debugger/media/dbg-tour-call-stack.png "Examiner la pile des appels")

La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La ligne du haut montre la fonction active (dans cet exemple, la méthode `Update`). La deuxième ligne montre que `Update` a été appelée depuis la propriété `Path.set`, etc. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

> [!NOTE]
> La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

Vous pouvez double-cliquer sur une ligne de code pour accéder à ce code source ; ceci change également l’étendue active inspectée par le débogueur. Ceci ne fait pas avancer le débogueur.

Vous pouvez également utiliser les menus contextuels de la fenêtre **Pile des appels** pour faire d’autres choses. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiques, redémarrer votre application avec **Exécuter jusqu’au curseur** et aller examiner le code source. Voir [Guide pratique pour examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Examiner une exception

Quand votre application lève une exception, le débogueur vous amène à la ligne de code qui a levé cette exception.

![Assistance sur l’exception](../debugger/media/dbg-tour-exception-helper.png "Assistance sur l’exception")

Dans cet exemple, **l’Assistance sur l’exception** vous montre une exception `System.Argument` et un message d’erreur indiquant que le chemin n’est pas d’une forme autorisée. Ainsi, nous savons que l’erreur s’est produite sur l’argument d’une méthode ou d’une fonction.

Dans cet exemple, l’appel de `DirectoryInfo` a provoqué l’erreur sur la chaîne vide, stockée dans la variable `value`.

L’Assistance sur l’exception est une fonctionnalité intéressante qui peut vous aider à déboguer des erreurs. Vous pouvez également examiner les détails de l’erreur et ajouter un espion à partir de l’Assistance sur l’exception. Si nécessaire, vous pouvez aussi changer les conditions pour lever une exception donnée.

> [!NOTE]
> L’Assistance sur l’exception remplace l’Assistant Exception dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Développez le nœud **Paramètres d’exception** pour voir plus d’options sur la façon de gérer ce type d’exception ; dans le cadre de cette visite guidée, vous ne devez néanmoins rien changer !

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Déboguer des applications ASP.NET en production dans Azure App Service

Le **débogueur de capture instantanée** prend une capture instantanée de vos applications en production au moment de l’exécution du code qui vous intéresse. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

![Lancer le débogueur de capture instantanée](../debugger/media/snapshot-launch.png "Lancer le débogueur de capture instantanée")

La collecte de captures instantanées est disponible pour les applications ASP.NET qui s’exécutent dans Azure App Service. Les applications ASP.NET doivent s’exécuter sur le .NET Framework 4.6.1 ou ultérieur, et les applications ASP.NET Core doivent s’exécuter sur .NET Core 2.0 ou ultérieur sur Windows.

Pour plus d’informations, consultez [Déboguer des applications ASP.NET en production avec le débogueur de capture instantanée](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Examiner des captures instantanées avec le retour en arrière IntelliTrace (Visual Studio Enterprise)

Le **retour en arrière IntelliTrace** crée automatiquement une capture instantanée de votre application à chaque événement de point d’arrêt et d’étape du débogueur. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils de débogage. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**.

![Boutons Étape précédente et Étape suivante](../debugger/media/intellitrace-step-back-icons-description.png  "Boutons Étape précédente et Étape suivante")

Pour plus d’informations, consultez la page [Inspecter les états antérieurs de l’application avec IntelliTrace](../debugger/view-historical-application-state.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez vu rapidement de nombreuses fonctionnalités du débogueur. Pour plus d’informations sur l’une de ces fonctionnalités en particulier, et notamment les points d'arrêt :

> [!div class="nextstepaction"]
> [Apprendre à utiliser les points d’arrêt](../debugger/using-breakpoints.md)
