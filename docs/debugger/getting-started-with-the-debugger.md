---
title: Apprenez à déboguer - Visual Studio | Documents Microsoft
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data
ms.custom: mvc
ms.date: 03/16/2018
ms.technology:
- vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92194e403e5a8fe6c7075ea7cd449442f281a7e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="learn-to-debug-using-visual-studio"></a>Apprenez à déboguer à l’aide de Visual Studio

Cette rubrique présente les fonctionnalités du débogueur Visual Studio dans une procédure pas à pas. Si vous souhaitez une vue de niveau supérieur des fonctionnalités du débogueur, consultez [présentation des fonctionnalités de débogueur](../debugger/debugger-feature-tour.md).

Vous pouvez lire le long pour voir les fonctionnalités du débogueur, ou vous pouvez télécharger l’exemple complet utilisé dans la visite guidée des fonctionnalités et suivez les étapes vous-même. Pour télécharger l’exemple et suivre la procédure, accédez à [démo Photo de la visionneuse](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")  |    [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sur le débogage, qui affiche des étapes similaires. |

Bien que l’application de démonstration est c#, les fonctionnalités sont applicables à C++, Visual Basic, JavaScript et autres langues prises en charge par Visual Studio (sauf mention contraire).

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrer le débogueur et les points d’arrêt.
> * Découvrir les commandes pour parcourir votre code dans le débogueur
> * Inspecter des variables dans les info-bulles et des fenêtres de débogage
> * Examiner la pile des appels
> * Utilisez l’Assistant Exception

## <a name="start-the-debugger"></a>Démarrez le débogueur !

1. Pour suivre ces étapes dans Visual Studio, téléchargez l’exemple [sur cette page](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Vous devez installer Visual Studio avec la charge de travail de développement de bureau .NET pour exécuter l’application que nous utilisons dans la démonstration.

2. Décompressez le projet.

3. Ouvrez Visual Studio et sélectionnez le **fichier > Ouvrir** menu de commande, puis choisissez **projet/Solution**, puis ouvrez le dossier où vous avez téléchargé le projet.

     ![Ouvrez l’exemple de projet](../debugger/media/dbg-tour-open-project.png "ouvrir un projet")

3. Ouvrez la démonstration de visionneuse de photos WPF > dossier c#, choisissez le fichier photoapp.sln, puis sélectionnez **ouvrir**.

     Le projet s’ouvre dans Visual Studio. L’Explorateur de solutions dans le volet droit affiche tous les fichiers projet.

    ![Fichiers de l’Explorateur de solutions](../debugger/media/dbg-tour-solution-explorer.png "l’Explorateur de solutions")

4. Appuyez sur F5 (**Déboguer > Démarrer le débogage** ou **démarrer le débogage** bouton ![démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "démarrer le débogage") dans la barre d’outils Déboguer).

     ![Application de visionneuse photo](../debugger/media/dbg-tour-wpf-app.png "Photo application de visionneuse")

     F5 démarre l’application avec le débogueur attaché au processus de l’application, mais à droite, maintenant nous n’avons pas ajouté les points d’arrêt ou fait rien de spécial pour examiner le code. Par conséquent, l’application charge simplement et que les images photo.

     Dans cette visite guidée, nous intéresser plus près à cette application à l’aide du débogueur et obtenir un aperçu du débogueur de fonctionnalités.

5. Arrêtez le débogueur en appuyant sur le taquet rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") bouton.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrage du débogueur

Pour déboguer, vous devez démarrer votre application avec le débogueur attaché au processus de l’application.

1. Dans la `MainWindow` constructeur de MainWindow.xaml.cs, définir un point d’arrêt en cliquant sur la marge de gauche de la première ligne de code.

     ![Définir un point d’arrêt](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. Appuyez sur F5 ou **démarrer le débogage** bouton, l’application démarre, et le débogueur exécute jusqu'à la ligne de code où vous avez défini le point d’arrêt.

    La flèche jaune représente l’instruction sur laquelle le débogueur a suspendu, également suspend l’exécution d’application sur le même point (cette instruction n’a pas encore exécuté).

    F5 continue l’exécution de l’application pour le point d’arrêt suivant. (Si l’application n’est pas encore en cours d’exécution, appuyez sur F5 démarre le débogueur et s’arrête au premier point d’arrêt.)

    Points d’arrêt sont une fonctionnalité utile lorsque vous savez que la ligne de code ou de la section de code que vous souhaitez examiner en détail.

## <a name="restart-your-app-quickly"></a>Redémarrez votre application rapidement

Cliquez sur le **redémarrer** ![redémarrer l’application](../debugger/media/dbg-tour-restart.png "RestartApp") bouton dans la barre d’outils de débogage (Ctrl + Maj + F5).

Lorsque vous appuyez sur **redémarrer**, il fait gagner du temps par rapport à l’arrêt de l’application et de redémarrer le débogueur. Le débogueur s’arrête sur le premier point d’arrêt est atteint par l’exécution de code.

Le débogueur s’arrête à nouveau sur le point d’arrêt que vous avez défini dans le `MainWindow` constructeur.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Parcourir le code dans le débogueur à l’aide des commandes d’étape

Essentiellement, nous utilisons ici, des raccourcis clavier, car il s’agit d’un bon moyen pour obtenir rapidement à l’exécution de votre application dans le débogueur (commandes équivalentes telles que le menu commandes sont indiqués entre parenthèses).

1. Appuyez sur F11 (**Déboguer > pas à pas détaillé**) à deux reprises pour avancer l’exécution de l’application vers le `InitializeComponent()` (fonction).

     ![Utilisez la touche F11 pour le code pas à pas détaillé](../debugger/media/dbg-tour-f11.png "F11 pas à pas détaillé")

     F11 est la **pas à pas détaillé** commande et avance l’instruction de l’exécution une application à la fois. F11 est une bonne solution pour examiner le flux d’exécution dans le détail la plupart des. (Pour déplacer plus rapidement dans le code, nous vous indiquons d’autres options également.) Par défaut, le débogueur ignore code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > Dans le code managé, vous verrez une boîte de dialogue vous demandant si vous souhaitez être averti lorsque vous effectuez pas automatiquement dans les propriétés et les opérateurs (comportement par défaut). Si vous souhaitez modifier le paramètre de désactiver une version ultérieure, **étape dans les propriétés et les opérateurs** définition dans le **Outils > Options** menu sous **débogage**.

2. Appuyez sur F10 (**Déboguer > pas à pas principal**) plusieurs fois jusqu'à ce que le débogueur s’arrête sur la première ligne de code dans le `OnApplicationStartup` Gestionnaire d’événements.

     ![Utiliser la touche F10 pour le code pas à pas principal](../debugger/media/dbg-tour-f10-step-over.png "F10 pas à pas principal")

     F10 avance le débogueur sans entrer dans les fonctions ou méthodes dans votre code d’application (le code s’exécute toujours). En appuyant sur F10 le `InitializeComponent` appel de méthode (au lieu de F11), nous avons ignoré sur le code d’implémentation `InitializeComponent` (qui nous ne mettons pas intéressés par dès maintenant par exemple).

## <a name="step-into-a-property"></a>Pas à pas détaillé d’une propriété

1. Avec le débogueur en pause sur cette ligne de code :

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Avec le bouton droit sur la ligne de code et choisissez **détaillé spécifique**, puis **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Utilisez l’étape dans la fonctionnalité spécifique](../debugger/media/dbg-tour-step-into-specific.png "détaillé spécifique")

    Comme mentionné précédemment, par défaut, le débogueur ignore les propriétés gérées et des champs, mais la **détaillé spécifique** commande vous permet de substituer ce comportement. Pour l’instant, nous souhaitons rechercher que se passe-t-il lorsque le `Path.set` s’exécute la méthode setter de propriété. **Détaillé spécifique** obtient nous le `Path.set` code ici.

     ![résultat de pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific-2.png "détaillé spécifique")

     Le `Update` méthode dans ce code semble il pourrait être intéressant, ce vous permet d’utiliser le débogueur pour examiner ce code près.

5. Placez le curseur sur le `Update` méthode jusqu'à ce que le vert **exécuter. Cliquez ensuite sur** bouton ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaît à gauche.

     ![Utilisez l’exécuter. Cliquez ensuite sur fonctionnalité](../debugger/media/dbg-tour-run-to-click-2.png "exécuter à, cliquez sur")

    >  [!NOTE] 
    > Le **exécuter. Cliquez ensuite sur** bouton est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Si vous ne voyez pas le bouton de flèche verte, utilisez F11 dans cet exemple à la place d’avancer le débogueur.

6. Cliquez sur le **exécuter. Cliquez ensuite sur** bouton ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    L’utilisation de ce bouton est similaire à la définition d’un point d’arrêt temporaire. **Cliquez sur exécuter** est pratique pour se déplacer rapidement au sein de la région visible du code d’application (vous pouvez cliquer dans un fichier ouvert).

    Le débogueur passe à la `Update` implémentation de méthode.

7. Appuyez sur F11 pour avancer dans le `Update` (méthode).

     ![Résultat de l’exécution pas à pas dans la méthode de mise à jour](../debugger/media/dbg-tour-update-method.png "étape dans la méthode de mise à jour")

    Ici, nous trouver encore du code qui vous intéresse ; l’application obtient tous les fichiers *.jpg résidant dans un répertoire particulier, puis en créant un objet Photo pour chaque fichier. Ce code produit une bonne opportunité de commencer à examiner l’état de votre application (variables) avec le débogueur. Nous ferons que dans les sections suivantes de ce didacticiel.

    Les fonctionnalités qui vous permettent d’inspecter des variables sont une des fonctionnalités plus utiles du débogueur, et il existe différentes manières de procéder. Souvent, lorsque vous essayez de déboguer un problème, vous essayez de savoir si les variables stockent les valeurs que vous attendez à leur attribuer à un moment donné.

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

Pendant la suspension de la `Update` (méthode), cliquez sur le **pile des appels** fenêtre, qui est par défaut ouvert dans le volet inférieur droit.

![Examiner la pile des appels](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

Le **pile des appels** fenêtre indique l’ordre dans lequel les méthodes et les fonctions sont mise en route appelées. La première ligne affiche la fonction en cours (la `Update` méthode dans l’application de la visite guidée). La deuxième ligne montre que `Update` a été appelée à partir de la `Path.set` propriété et ainsi de suite.

>  [!NOTE]
> Le **pile des appels** fenêtre est identique à la perspective de débogage dans certains environnements IDE comme Eclipse.

La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

Vous pouvez double-cliquer sur une ligne de code pour accéder à examiner le code source et qui change également l’étendue actuelle en cours d’inspection par le débogueur. Cette action n’avance pas le débogueur.

Vous pouvez également utiliser les menus contextuels à partir de la **pile des appels** fenêtre pour effectuer d’autres opérations. Par exemple, vous pouvez insérer des points d’arrêt dans les fonctions spécifiées, le débogueur à l’aide d’avance **exécuter jusqu’au curseur**et accédez à examiner le code source. Pour plus d’informations, consultez [Comment : examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Pas à pas sortant

Supposons que vous avez terminé examinant le `Update` méthode dans Data.cs et que vous souhaitez tirer parti de la fonction, mais restent dans le débogueur. Ce faire, vous pouvez utiliser la **pas à pas sortant** commande.

1. Appuyez sur MAJ + F11 (ou **Déboguer > pas à pas sortant**).

     Cette commande reprend l’exécution d’application (et avance le débogueur) jusqu’au retour de la fonction actuelle.

     Vous devez être dans le `Update` appel de méthode dans Data.cs.

2. Appuyez sur MAJ + F11 à nouveau et que le débogueur passe la pile des appels pour revenir le `OnApplicationStartup` Gestionnaire d’événements.

## <a name="run-to-cursor"></a>Exécuter jusqu'au curseur

1. Choisissez le **arrêter le débogage** bouton rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") ou MAJ + F5.

2. Dans le `Update` avec le bouton droit de la méthode dans Data.cs, le `Add` appel de méthode et choisissez **exécuter jusqu’au curseur**. Cette commande démarre le débogage et définit un point d’arrêt temporaire sur la ligne de code active.

     ![Utilisez l’exécution de la fonctionnalité de curseur](../debugger/media/dbg-tour-run-to-cursor.png "exécuter jusqu’au curseur")

    Vous devez être suspendue sur le point d’arrêt dans `MainWindow` (car il s’agit du premier point d’arrêt vous définissez).

3. Appuyez sur F5 pour passer à la `Add` méthode où vous avez sélectionné **exécuter jusqu’au curseur**.

    Cette commande est utile lorsque vous modifiez du code et que vous souhaitez définir un point d’arrêt temporaire rapidement et de démarrer le débogueur.

## <a name="change-the-execution-flow"></a>Modifier le flux d’exécution

1. Avec le débogueur en mode pause sur le `Add` appel de méthode, utilisez la souris de saisir la flèche jaune (le pointeur d’exécution) sur la gauche et déplacer la flèche jaune une ligne à la `foreach` boucle.

     ![Déplacez le pointeur d’exécution](../debugger/media/dbg-tour-move-the-execution-pointer.gif "déplacer le pointeur d’exécution")

    En modifiant le flux d’exécution, vous pouvez effectuer diverses tâches telles que les chemins d’exécution de code différent de test ou réexécutez le code sans redémarrer le débogueur.

2. Maintenant, appuyez sur F5.

    Vous pouvez voir les images ajoutées à la fenêtre de l’application. Étant donné que vous exécutez à nouveau le code dans le `foreach` boucle, certaines images ont été ajoutées à deux reprises.
    
    > [!WARNING]
    > Fréquence à laquelle vous devez être prudent avec cette fonctionnalité, et un avertissement s’affiche dans l’info-bulle. Vous pouvez voir les autres avertissements, trop. Déplacer le pointeur ne peut pas rétablir votre application à un état antérieur de l’application.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec info-bulles

1. Ouvrez Data.cs dans l’application de démonstration de l’Observateur de Photo, cliquez sur le `private void Update` déclaration de fonction et choisissez **exécuter jusqu’au curseur** (arrêter tout d’abord l’application si elle est déjà en cours d’exécution).

    Cela va suspendre l’application avec le débogueur attaché. Cela nous permet d’examiner son état.

2. Placez le curseur sur le `Add` méthode appeler et cliquez sur le **exécuter. Cliquez ensuite sur** bouton ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Maintenant, placez le curseur sur l’objet de fichier (`f`) et que sa valeur de propriété par défaut, le nom de fichier `market 031.jpg`.

     ![Afficher une info-bulle](../debugger/media/dbg-tour-data-tips.gif "afficher une info-bulle")

4. Développez l’objet pour afficher ses propriétés, telles que le `FullPath` propriété.

    Souvent, lors du débogage, vous souhaitez un moyen rapide de vérifier les valeurs de propriétés des objets et les conseils de données sont un bon moyen de le faire.

    > [!TIP]
    > Dans les langues prises en charge de plus, vous pouvez modifier le code au milieu d’une session du débogueur si vous trouvez quelque chose que vous souhaitez modifier. Pour plus d’informations, consultez [Modifier & Continuer](../debugger/edit-and-continue.md). Pour utiliser cette fonctionnalité dans cette application, toutefois, nous avons tout d’abord doit mettre à jour la version de l’application du .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les fenêtres automatique et variables locales

1. Examinez le **automatique** fenêtre au bas de l’éditeur de code.

     ![Inspecter des variables dans la fenêtre automatique](../debugger/media/dbg-tour-autos-window.png "automatique (fenêtre)")

    Dans le **automatique** fenêtre, vous voyez des variables et leur valeur actuelle. Le **automatique** fenêtre affiche toutes les variables utilisées dans la ligne actuelle ou de la ligne précédente (en C++, la fenêtre affiche les variables dans les trois lignes de code précédents. Consultez la documentation pour le comportement spécifique au langage).

    > [!NOTE]
    > Dans JavaScript, le **variables locales** fenêtre est pris en charge mais pas les **automatique** fenêtre.

2. Ensuite, examinez le **variables locales** fenêtre.

    Le **variables locales** fenêtre affiche les variables qui sont dans la portée actuelle.

    ![Inspecter des variables dans la fenêtre variables locales](../debugger/media/dbg-tour-locals-window.png "fenêtre variables locales")

    Actuellement, le `this` objet et l’objet de fichier (`f`) se trouvent dans la portée actuelle. Pour plus d’informations, consultez [inspecter des Variables dans les fenêtres variables locales et automatique](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Définissez un espion

1. Dans la fenêtre d’éditeur de code principal, cliquez sur l’objet de fichier (`f`) et choisissez **ajouter un espion**.

    Vous pouvez utiliser un **espion** fenêtre pour spécifier une variable (ou une expression) que vous souhaitez garder un œil sur.

    Vous avez maintenant un espion à définir sur le `File` objet et vous pouvez voir sa valeur changent à mesure que vous parcourez le débogueur. Contrairement à d’autres fenêtres de variables, le **espion** fenêtre affiche toujours les variables que vous surveillez (elles sont grisées lorsque hors de portée).

2. Sur le `Add` (méthode), cliquez sur le vert ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png "RunToClick") bouton Nouveau (ou appuyez sur F11 à plusieurs fois) pour faire défiler le `foreach` boucle.

    ![Définissez un espion dans une variable](../debugger/media/dbg-tour-watch-window.png "fenêtre Espion")

    Vous pouvez également voir la première image sont ajoutés à la fenêtre principale de l’exécution exemple d’application, mais cela se produit sur un thread d’application différents, les images peut ne pas être visibles encore.

    Pour plus d’informations, consultez [définissez un espion à l’aide de l’espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Examiner une exception

1. Dans la fenêtre de l’application en cours d’exécution, supprimez le texte dans le **chemin d’accès** zone d’entrée, puis sélectionnez le **modification** bouton.

     ![Une exception levée](../debugger/media/dbg-tour-cause-an-exception.png "générer une Exception.")

     L’application lève une exception, et le débogueur vous amène à la ligne de code qui a levé l’exception.
     
     ![Assistance d’exception](../debugger/media/dbg-tour-exception-helper.png "assistance d’Exception")

     Ici, le **assistance d’Exception** vous montre une `System.ArgumentException` et un message d’erreur indiquant que le chemin d’accès n’est pas une forme conforme. Par conséquent, nous savons que l’erreur s’est produite sur un argument de méthode ou fonction.

     Dans cet exemple, le `DirectoryInfo` appel a renvoyé l’erreur sur la chaîne vide, stockée dans le `value` variable. (Placez le curseur sur `value` pour afficher la chaîne vide.)

     L’application d’assistance de l’Exception est une fonctionnalité intéressante qui peut vous aider à déboguer les erreurs. Vous pouvez également effectuer les opérations vue Détails de l’erreur et ajouter un espion à partir de l’application d’assistance de l’Exception. Ou, si nécessaire, vous pouvez modifier les conditions pour lever l’exception particulière.

    >  [!NOTE] 
    > L’application d’assistance de l’Exception remplace l’Assistant Exception dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Développez le **paramètres d’Exception** nœud pour afficher davantage d’options sur la façon de gérer ce type d’exception, mais vous n’avez pas besoin de modifications dans cette visite guidée !

3. Appuyez sur F5 pour poursuivre l’application.

Pour en savoir plus sur les fonctionnalités du débogueur, consultez [débogueur trucs et astuces](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment démarrer le débogueur, parcourir le code et d’inspecter des variables. Vous souhaiterez plus haut niveau sur les fonctionnalités du débogueur, ainsi que des liens vers plus d’informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
