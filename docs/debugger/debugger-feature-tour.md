---
title: "Visite guidée des fonctionnalités du débogueur | Documents Microsoft"
ms.custom: H1HackMay2017
ms.date: 05/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 91b7ff9ea0b5caae46715894016469fadecaa098
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="feature-tour-of-the-visual-studio-debugger"></a>Visite guidée des fonctionnalités du débogueur Visual Studio

Cette rubrique présente les fonctionnalités du débogueur Visual Studio. Si vous souhaitez suivre la procédure en ouvrant votre propre application dans Visual Studio, vous pouvez le faire, ou vous pouvez le suivre une application d’exemple à l’aide du [Guide du débutant](../debugger/getting-started-with-the-debugger.md).

Les fonctionnalités décrites ici sont applicables pour c#, C++, Visual Basic, JavaScript et autres langues prises en charge par Visual Studio (sauf mention contraire).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrage du débogueur

Pour déboguer, vous devez démarrer votre application avec le débogueur attaché au processus de l’application. F5 (**Déboguer > Démarrer le débogage**) est la méthode la plus courante pour ce faire. Toutefois, l’instant, vous n’avez ne peut-être pas défini les points d’arrêt pour examiner votre application code, donc nous allons effectuer d’abord et démarrer le débogage.

Si un fichier est ouvert dans l’éditeur de code, vous pouvez définir un point d’arrêt en cliquant dans la marge à gauche d’une ligne de code.

![Définir un point d’arrêt](../debugger/media/dbg-tour-set-a-breakpoint.gif "définir un point d’arrêt")

Appuyez sur F5 (**Déboguer > Démarrer le débogage**) et le débogueur s’exécute pour le premier point d’arrêt qu’il détecte. Si l’application n’est pas encore en cours d’exécution, appuyez sur F5 démarre le débogueur et s’arrête au premier point d’arrêt.

Points d’arrêt sont une fonctionnalité utile lorsque vous savez que la ligne de code ou de la section de code que vous souhaitez examiner en détail.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Parcourir le code dans le débogueur à l’aide des commandes d’étape

Nous fournissons des raccourcis clavier pour la plupart des commandes car elles rendent la navigation dans le code de votre application plus rapide. (Équivalent des commandes telles que les commandes de menu sont indiqués entre parenthèses.)

Pour démarrer votre application avec le débogueur attaché, appuyez sur F11 (**Déboguer > pas à pas détaillé**). F11 est la **pas à pas détaillé** commande et avance l’instruction de l’exécution une application à la fois. Lorsque vous démarrez l’application en appuyant sur F11, le débogueur s’arrête à la première instruction est exécutée.

![F11 Pas à pas détaillé](../debugger/media/dbg-tour-f11.png "F11 pas à pas détaillé")

La flèche jaune représente l’instruction sur laquelle le débogueur a suspendu, également suspend l’exécution d’application sur le même point (cette instruction n’a pas encore exécuté).

F11 est une bonne solution pour examiner le flux d’exécution dans le détail la plupart des. (Pour déplacer plus rapidement dans le code, nous vous indiquons d’autres options.) Par défaut, le débogueur ignore code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon Code](../debugger/just-my-code.md)).

>[!NOTE]
> Dans le code managé, vous verrez une boîte de dialogue vous demandant si vous souhaitez être averti lorsque vous effectuez pas automatiquement dans les propriétés et les opérateurs (comportement par défaut). Si vous souhaitez modifier le paramètre de désactiver une version ultérieure, **étape dans les propriétés et les opérateurs** définition dans le **Outils > Options** menu sous **débogage**.

## <a name="step-over-code-to-skip-functions"></a>Ignorer le code pour ignorer les fonctions

Lorsque vous êtes sur une ligne de code qui est un appel de fonction ou une méthode, vous pouvez appuyer sur F10 (**Déboguer > pas à pas principal**) au lieu de F11.

F10 avance le débogueur sans entrer dans les fonctions ou méthodes dans votre code d’application (le code s’exécute toujours). En appuyant sur F10, vous pouvez ignorer le code qui vous n'intéressent pas. De cette manière, vous pouvez obtenir rapidement au code qui vous intéressent le plus.

## <a name="step-into-a-property"></a>Pas à pas détaillé d’une propriété

Comme mentionné précédemment, par défaut, le débogueur ignore les propriétés gérées et des champs, mais la **détaillé spécifique** commande vous permet de substituer ce comportement.

Avec le bouton droit sur une propriété ou un champ et choisissez **détaillé spécifique**, puis choisissez une des options disponibles.

![Pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific.png "pas à pas détaillé spécifique")

Dans cet exemple, **détaillé spécifique** nous Obtient le code de `Path.set`.

![Pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific-2.png "pas à pas détaillé spécifique")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Exécuter à un point dans votre code rapidement à l’aide de la souris

Dans le débogueur, pointez sur une ligne de code jusqu'à ce que le **exécuter. Cliquez ensuite sur** bouton de (exécution ici) ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaît à gauche.

![Cliquez sur exécuter](../debugger/media/dbg-tour-run-to-click-2.png "exécuter à, cliquez sur")

>  [!NOTE] 
> Le **exécuter. Cliquez ensuite sur** bouton de (exécution ici) est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Cliquez sur le **exécuter. Cliquez ensuite sur** bouton de (exécution ici). Le débogueur passe à la ligne de code où vous avez cliqué.

L’utilisation de ce bouton est similaire à la définition d’un point d’arrêt temporaire. Cette commande est également pratique pour se déplacer rapidement au sein de la région visible du code d’application. Vous pouvez utiliser **exécuter. Cliquez ensuite sur** dans un fichier ouvert.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Avancer le débogueur sort de la fonction en cours

Parfois, vous souhaiterez continuer votre session de débogage, mais le débogueur tout au long de la fonction en cours d’avance.

Appuyez sur MAJ + F11 (ou **Déboguer > pas à pas sortant**).

Cette commande reprend l’exécution d’application (et avance le débogueur) jusqu’au retour de la fonction actuelle.

## <a name="run-to-cursor"></a>Exécuter jusqu'au curseur

Arrêtez le débogueur en appuyant sur la **arrêter le débogage** bouton rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") ou MAJ + F5.

Cliquez sur une ligne de code dans votre application et choisissez **exécuter jusqu’au curseur**. Cette commande démarre le débogage et définit un point d’arrêt temporaire sur la ligne de code active.

![Exécuter jusqu’au curseur](../debugger/media/dbg-tour-run-to-cursor.png "exécuter jusqu’au curseur")

Si vous avez défini les points d’arrêt, le débogueur s’arrête sur le premier point d’arrêt auxquels il accède.

Appuyez sur F5, jusqu'à ce que vous atteigniez la ligne de code où vous avez sélectionné **exécuter jusqu’au curseur**.

Cette commande est utile lorsque vous modifiez du code et que vous souhaitez définir un point d’arrêt temporaire rapidement et de démarrer le débogueur.


> [!NOTE]
> Vous pouvez utiliser **exécuter jusqu’au curseur** dans les **pile des appels** fenêtre pendant que vous déboguez.

## <a name="restart-your-app-quickly"></a>Redémarrez votre application rapidement

Cliquez sur le **redémarrer** ![redémarrer l’application](../debugger/media/dbg-tour-restart.png "redémarrer l’application") bouton dans la barre d’outils déboguer (**Ctrl + Maj + F5**).

Lorsque vous appuyez sur **redémarrer**, il fait gagner du temps par rapport à l’arrêt de l’application et de redémarrer le débogueur. Le débogueur s’arrête sur le premier point d’arrêt est atteint par l’exécution de code.

Si vous ne souhaitez pas arrêter le débogueur et revenir dans l’éditeur de code, vous pouvez appuyer sur le taquet rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") bouton au lieu de **redémarrer**.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec info-bulles

Maintenant que vous connaissez un peu votre sens, vous avez une bonne opportunité de commencer à examiner l’état de votre application (variables) avec le débogueur. Les fonctionnalités qui vous permettent d’inspecter des variables sont certaines des fonctionnalités plus utiles du débogueur, et il existe différentes manières de procéder. Souvent, lorsque vous essayez de déboguer un problème, vous tentez savoir si les variables stockent les valeurs que vous attendez qu’elles dans un état de l’application.

Pendant la suspension dans le débogueur, placez le curseur sur un objet avec la souris et que sa valeur de propriété par défaut (dans cet exemple, le nom de fichier `market 031.jpg` est la valeur de propriété par défaut).

![Afficher une info-bulle](../debugger/media/dbg-tour-data-tips.gif "afficher une info-bulle")

Développez l’objet pour voir toutes ses propriétés (telles que le `FullPath` propriété dans cet exemple).

Souvent, lors du débogage, vous souhaitez un moyen rapide de vérifier les valeurs de propriétés des objets et les conseils de données sont un bon moyen de le faire.

> [!TIP]
> Dans les langues prises en charge de plus, vous pouvez modifier le code au milieu d’une session de débogage. Pour plus d’informations, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les fenêtres automatique et variables locales

Lors du débogage, examinez le **automatique** fenêtre au bas de l’éditeur de code.

![Automatique fenêtre](../debugger/media/dbg-tour-autos-window.png "automatique (fenêtre)")

Dans le **automatique** , vous devez voir variables le long de leur valeur actuelle et leur type. Le **automatique** fenêtre affiche toutes les variables utilisées dans la ligne actuelle ou de la ligne précédente (en C++, la fenêtre affiche les variables dans les trois lignes de code précédents. Consultez la documentation pour le comportement spécifique au langage).

> [!NOTE]
> Dans JavaScript, le **variables locales** fenêtre est pris en charge mais pas les **automatique** fenêtre.

Ensuite, examinez le **variables locales** fenêtre. Le **variables locales** fenêtre affiche les variables qui sont actuellement dans la portée.

![Fenêtre variables locales](../debugger/media/dbg-tour-locals-window.png "fenêtre variables locales")

Dans cet exemple, le `this` objet et l’objet `f` sont dans la portée. Pour plus d’informations, consultez [inspecter des Variables dans les fenêtres variables locales et automatique](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Définissez un espion

Vous pouvez utiliser un **espion** fenêtre pour spécifier une variable (ou une expression) que vous souhaitez garder un œil sur.

Pendant le débogage, cliquez sur un objet et choisissez **ajouter un espion**.

![Fenêtre Espion](../debugger/media/dbg-tour-watch-window.png "fenêtre Espion")

Dans cet exemple, vous avez un espion à définir sur le `File` objet et vous pouvez voir sa valeur changent à mesure que vous parcourez le débogueur. Contrairement à d’autres fenêtres de variables, le **espion** windows toujours affichent les variables que vous surveillez (elles sont grisées lorsque hors de portée).

Pour plus d’informations, consultez [définissez un espion à l’aide de l’espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

Cliquez sur le **pile des appels** fenêtre pendant que vous déboguez, par défaut, ouvrir dans le volet inférieur droit.

![Examiner la pile des appels](../debugger/media/dbg-tour-call-stack.png "examiner la pile des appels")

Le **pile des appels** fenêtre indique l’ordre dans lequel les méthodes et les fonctions sont mise en route appelées. La première ligne affiche la fonction en cours (la `Update` méthode dans cet exemple). La deuxième ligne montre que `Update` a été appelée à partir de la `Path.set` propriété et ainsi de suite. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

> [!NOTE]
> Le **pile des appels** fenêtre est identique à la perspective de débogage dans certains environnements IDE comme Eclipse.

Vous pouvez double-cliquer sur une ligne de code pour accéder à examiner le code source et qui change également l’étendue actuelle en cours d’inspection par le débogueur. Cela n’avance pas le débogueur.

Vous pouvez également utiliser les menus contextuels à partir de la **pile des appels** fenêtre pour effectuer d’autres opérations. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiques, redémarrez votre application à l’aide de **exécuter jusqu’au curseur**et accéder à examiner le code source. Consultez [Comment : examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a>Examiner une exception

Lorsque votre application lève une exception, le débogueur vous amène à la ligne de code qui a levé l’exception.
     
![Assistance d’exception](../debugger/media/dbg-tour-exception-helper.png "assistance d’Exception")

Dans cet exemple, le **assistance d’Exception** vous montre une `System.Argument` exception et un message d’erreur indiquant que le chemin d’accès n’est pas une forme conforme. Par conséquent, nous savons que l’erreur s’est produite sur un argument de méthode ou fonction.

Dans cet exemple, le `DirectoryInfo` appel a renvoyé l’erreur sur la chaîne vide, stockée dans le `value` variable.

L’application d’assistance de l’Exception est une fonctionnalité intéressante qui peut vous aider à déboguer les erreurs. Vous pouvez également effectuer les opérations vue Détails de l’erreur et ajouter un espion à partir de l’application d’assistance de l’Exception. Ou, si nécessaire, vous pouvez modifier les conditions pour lever l’exception particulière.

>  [!NOTE] 
> L’application d’assistance de l’Exception remplace l’Assistant Exception dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Développez le **paramètres d’Exception** nœud pour afficher davantage d’options sur la façon de gérer ce type d’exception, mais vous n’avez pas besoin de modifications dans cette visite guidée !

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Déboguer des applications ASP.NET en direct dans Azure App Service

le **instantané débogueur** prend un instantané de vos applications de production lors de l’exécution de code qui vous intéressez. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

![Lancer le débogueur de l’instantané](../debugger/media/snapshot-launch.png "lancer le débogueur de l’instantané")

Collection de l’instantané est disponible pour les applications ASP.NET s’exécutant dans Azure App Service. Les applications ASP.NET doivent s’exécuter sur .NET Framework 4.6.1 ou version ultérieure, et les applications ASP.NET Core doivent s’exécuter sur .NET Core 2.0 ou version ultérieure sur Windows.

Pour plus d’informations, consultez [déboguer des applications ASP.NET en direct à l’aide du débogueur de l’instantané](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Afficher des instantanés avec IntelliTrace étape différée (Visual Studio Enterprise)

**Étape IntelliTrace différée** prend automatiquement un instantané de votre application à chaque point d’arrêt et le débogueur événement d’étape. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils de débogage. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**.

![Étape vers l’arrière et des boutons](../debugger/media/intellitrace-step-back-icons-description.png  "boutons arrière et transférer")  

Pour plus d’informations, consultez la page [Afficher des captures instantanées avec le retour en arrière IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md).

## <a name="more-features-to-look-at"></a>Plusieurs fonctions à examiner

-   [Conseils et astuces de débogueur](../debugger/debugger-tips-and-tricks.md) apprendre à accroître votre productivité avec le débogueur.

-   [Modifier & Continuer](../debugger/edit-and-continue.md) pour un sous-ensemble de langues (c#, C++, Visual Basic), la fonctionnalité Modifier & Continuer vous permet de modifier le code au milieu d’une session de débogage.

-   [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md) décrit comment déboguer des applications multithread. 

-   [Débogage distant](../debugger/remote-debugging.md) décrit comment déboguer des applications qui s’exécutent sur d’autres ordinateurs ou les périphériques. 
  
-   [IntelliTrace](../debugger/intellitrace.md) décrit la fonctionnalité d’IntelliTrace dans Visual Studio Enterprise. Vous pouvez utiliser il à l’enregistrement et la trace de l’historique d’exécution de votre code.

-   [Utilisation du réseau](../profiling/network-usage.md) décrit un outil de profilage que vous pouvez utiliser pour déboguer des services web et autres ressources réseau dans les applications Windows universelle (UWP). Utilisez l’outil pour examiner les charges utiles.

-   [Debug Interface Access SDK](../debugger/debug-interface-access/debug-interface-access-sdk.md) décrit le Kit de développement des logiciels Microsoft Debug Interface Access (DIA SDK). Ce kit fournit l’accès aux informations de débogage stockées dans les fichiers de base de données du programme (.pdb) qui sont générés par les outils de post-compilation Microsoft.  

## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md)
