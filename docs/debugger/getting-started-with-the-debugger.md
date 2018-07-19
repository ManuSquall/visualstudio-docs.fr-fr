---
title: Apprenez à déboguer à l’aide du débogueur Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1144e7e33709510cb03ed02cb62020f81e8e8b62
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303144"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Didacticiel : Apprenez à déboguer à l’aide de Visual Studio

Cette rubrique présente les fonctionnalités du débogueur Visual Studio dans une procédure pas à pas. Si vous souhaitez une vue plus générale des fonctionnalités du débogueur, consultez [visite guidée des fonctionnalités débogueur](../debugger/debugger-feature-tour.md). Lorsque vous *déboguer votre application*, cela signifie généralement que vous exécutez votre application avec le débogueur attaché. Lorsque vous effectuez cette opération, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant son exécution. Vous pouvez parcourir votre code et examinez les valeurs stockées dans des variables, vous pouvez définir des observations sur les variables pour voir lorsque les valeurs changent, vous pouvez examiner le chemin d’accès de l’exécution de votre code, et al. S’il s’agit de la première fois que vous avez essayé de déboguer du code, il pouvez que vous souhaitez lire [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de passer par cette rubrique.

Vous pouvez lire le long à découvrir les fonctionnalités du débogueur, ou vous pouvez télécharger l’exemple complet utilisé dans la visite guidée des fonctionnalités et suivez les étapes vous-même. Pour télécharger l’exemple et suivre la procédure, accédez à [démo de la visionneuse Photo](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")  |    [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sur le débogage, qui affiche des étapes similaires. |

Bien que l’application de démonstration est c#, les fonctionnalités sont applicables à C++, Visual Basic, JavaScript et autres langues prises en charge par Visual Studio (sauf indication contraire).

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrez le débogueur et les points d’arrêt.
> * Découvrez les commandes pour parcourir le code dans le débogueur
> * Inspecter des variables dans des bulles d’informations et les fenêtres du débogueur
> * Examiner la pile des appels
> * L’assistance d’Exception

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio 2017 est installé et le. **NET développement bureautique** charge de travail.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

    Si vous devez installer la charge de travail mais que vous avez déjà Visual Studio, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet** (sélectionnez **Fichier** > **Nouveau** > **Projet**). Visual Studio Installer est lancé. Choisissez le. **Développement bureautique NET** charge de travail, puis choisissez **modifier**.

## <a name="start-the-debugger"></a>Démarrez le débogueur !

1. Pour suivre ces étapes dans Visual Studio, téléchargez l’exemple [sur cette page](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > Vous devez installer Visual Studio avec la charge de travail de développement de bureau .NET pour exécuter l’application que nous utilisons dans la démonstration.

2. Décompressez le projet.

3. Ouvrez Visual Studio et sélectionnez le **fichier > Ouvrir** menu de commande, puis choisissez **projet/Solution**, puis ouvrez le dossier où vous avez téléchargé le projet.

     ![Ouvrez l’exemple de projet](../debugger/media/dbg-tour-open-project.png "ouvrir un projet")

3. Ouvrez la démonstration de visionneuse de photos WPF > dossier c#, choisissez le *photoapp.sln* et sélectionnez **Open**.

     Le projet s’ouvre dans Visual Studio. L’Explorateur de solutions dans le volet de droite vous montre tous les fichiers projet.

    ![Fichiers de l’Explorateur de solutions](../debugger/media/dbg-tour-solution-explorer.png "l’Explorateur de solutions")

4. Appuyez sur **F5** (**Déboguer > Démarrer le débogage**) ou le **démarrer le débogage** bouton ![démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "démarrer le débogage ") dans la barre d’outils de débogage.

     ![Application de visionneuse de photos](../debugger/media/dbg-tour-wpf-app.png "application de visionneuse de photos")

     F5 démarre l’application avec le débogueur attaché au processus de l’application, mais droite maintenant nous n’avons pas ajouté les points d’arrêt ou fait rien de spécial à examiner le code. Par conséquent, l’application se charge juste et vous voyez les images de photos.

     Dans cette présentation, nous examinons plus en détail cette application à l’aide du débogueur et avoir une idée du débogueur de fonctionnalités.

5. Arrêtez le débogueur en appuyant sur le taquet rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") bouton.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définissez un point d’arrêt et démarrez le débogueur

Pour déboguer, vous devez démarrer votre application avec le débogueur attaché au processus de l’application.

1. Dans le `MainWindow` constructeur de MainWindow.xaml.cs, définissez un point d’arrêt en cliquant sur la marge gauche de la première ligne de code.

     ![Définissez un point d’arrêt](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. 

6. Appuyez sur **F5** ou **démarrer le débogage** bouton, l’application démarre, et le débogueur exécute jusqu'à la ligne de code où vous avez défini le point d’arrêt.

    La flèche jaune représente l’instruction sur laquelle le débogueur a suspendu, ce qui interrompt également l’exécution d’application au même moment (cette instruction n’a pas encore exécuté).

    F5 continue l’exécution de l’application au point d’arrêt suivant. (Si l’application n’est pas encore en cours d’exécution, F5 démarre le débogueur et s’arrête au premier point d’arrêt).

    Les points d’arrêt sont une fonctionnalité utile quand vous savez quelle ligne ou section de code vous voulez examiner en détail.

## <a name="optional-restart-your-app-quickly"></a>(Facultatif) Redémarrez votre application rapidement

Cliquez sur le **redémarrer** ![redémarrer une application](../debugger/media/dbg-tour-restart.png "RestartApp") bouton dans la barre d’outils déboguer (**Ctrl** + **MAJ**   +  **F5**).

Quand vous appuyez sur **redémarrer**, il fait gagner du temps par rapport à l’arrêt de l’application et de redémarrer le débogueur. Le débogueur s’arrête sur le premier point d’arrêt est atteint par l’exécution de code.

Le débogueur s’arrête à nouveau sur le point d’arrêt que vous avez défini dans le `MainWindow` constructeur.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Parcourir le code dans le débogueur à l’aide des commandes de l’étape

Principalement, nous utilisons ici, des raccourcis clavier, car c’est un bon moyen pour obtenir rapidement à l’exécution de votre application dans le débogueur (commandes équivalentes tels que menu commandes sont affichées entre parenthèses).

1. Appuyez sur **F11** (**Déboguer > pas à pas détaillé**) à deux reprises pour avancer l’exécution de l’application vers le `InitializeComponent()` (fonction).

     ![Utilisez F11 pour le code pas à pas détaillé](../debugger/media/dbg-tour-f11.png "détaillé F11")

     F11 est la commande **pas à pas détaillé** et elle exécute l'application une instruction à la fois. F11 est une bonne solution pour examiner le flux d’exécution en détails. (Pour déplacer plus rapidement le code, nous vous montrons d’autres options également.) Par défaut, le débogueur ignore le code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > Dans le code managé, vous verrez une boîte de dialogue vous demandant si vous souhaitez être averti quand vous effectuez automatiquement un pas à pas dans les propriétés et les opérateurs (le comportement par défaut). Si vous voulez changer cette option plus tard, désactivez **Pas à pas principal dans les propriétés et les opérateurs** dans le menu **Outils > Options** sous **Débogage**.

2. Appuyez sur **F10** (**Déboguer > pas à pas principal**) plusieurs fois jusqu'à ce que le débogueur s’arrête sur la première ligne de code dans le `OnApplicationStartup` Gestionnaire d’événements.

     ![Utiliser la touche F10 pour le code pas à pas principal](../debugger/media/dbg-tour-f10-step-over.png "F10 pas à pas principal")

     F10 fait avancer le débogueur sans entrer dans les fonctions ou méthodes dans votre code d’application (le code s’exécute toujours). En appuyant sur F10 le `InitializeComponent` appel de méthode (au lieu de la touche F11), nous avons ignoré sur le code d’implémentation pour `InitializeComponent` (qui nous n’allons pas maintenant intéressés par exemple).

## <a name="step-into-a-property"></a>Pas à pas détaillé d’une propriété

1. Avec le débogueur suspendu sur cette ligne de code :

    ````c#
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Avec le bouton droit sur la ligne de code et choisissez **détaillé spécifique**, puis **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Utilisez le pas à pas détaillé spécifique fonctionnalité](../debugger/media/dbg-tour-step-into-specific.png "détaillé spécifique")

    Comme mentionné précédemment, par défaut, le débogueur ignore les propriétés et les champs managés, mais la commande **Pas à pas détaillé spécifique** vous permet de substituer ce comportement. Pour l’instant, nous souhaitons rechercher que se passe-t-il lorsque le `Path.set` exécutions de méthode setter de propriété. **Détaillé spécifique** obtient nous le `Path.set` ici le code.

     ![résultat de pas à pas détaillé spécifique](../debugger/media/dbg-tour-step-into-specific-2.png "détaillé spécifique")

     Le `Update` méthode dans ce code semble pourrait être intéressant, c’est le cas permet d’utiliser le débogueur pour examiner ce code, communiquez.

5. Placez le curseur sur le `Update` méthode jusqu'à ce que le vert **exécuter jusqu’au clic** bouton ![exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaît à gauche.

     ![Utiliser l’exécution sur clic fonctionnalité](../debugger/media/dbg-tour-run-to-click-2.png "exécuter jusqu’au clic")

    >  [!NOTE]
    > Le **exécuter jusqu’au clic** bouton est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Si vous ne voyez pas le bouton fléché vert, utilisez F11 dans cet exemple à la place pour faire avancer le débogueur.

6. Cliquez sur le **exécuter jusqu’au clic** bouton ![exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    L’utilisation de ce bouton est similaire à la définition d’un point d’arrêt temporaire. **Exécuter jusqu’au clic** est pratique pour la navigation rapidement dans une zone visible du code d’application (vous pouvez cliquer dans n’importe quel fichier ouvrir).

    Le débogueur avance jusqu'à le `Update` implémentation de la méthode.

7. Appuyez sur **F11** à l’étape dans le `Update` (méthode).

     ![Résultat de l’exécution pas à pas dans la méthode de mise à jour](../debugger/media/dbg-tour-update-method.png "étape dans la méthode de mise à jour")

    Ici, nous trouver du code qui vous intéresse ; l’application obtient tous les. *jpg* fichiers résidant dans un répertoire particulier, puis en créant un objet Photo pour chaque fichier. Ce code nous donne une bonne occasion pour commencer à examiner l’état de votre application (variables) avec le débogueur. Nous allons effectuer que dans les sections suivantes de ce didacticiel.

    Les fonctionnalités qui vous permettent d’inspecter les variables sont une des fonctionnalités plus utiles du débogueur, et il existe différentes manières de procéder. Souvent, lorsque vous essayez de déboguer un problème, vous essayez de déterminer si les variables sont stocker les valeurs que vous attendez d’avoir à un moment donné.

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

Pendant la suspension dans le `Update` (méthode), cliquez sur le **pile des appels** fenêtre, qui est par défaut ouvert dans le volet inférieur droit.

![Examiner la pile des appels](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

Le **pile des appels** fenêtre indique l’ordre dans lequel les méthodes et les fonctions sont bien appelées. La première ligne affiche la fonction active (la `Update` méthode dans l’application de la visite guidée). La deuxième ligne montre que `Update` a été appelée à partir de la `Path.set` propriété et ainsi de suite.

>  [!NOTE]
> Le **pile des appels** est identique à la perspective de débogage dans certains IDE comme Eclipse.

La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

Vous pouvez double-cliquer sur une ligne de code revenir sur ce code source et qui modifie également la portée actuelle est inspectée par le débogueur. Cette action n’avance pas le débogueur.

Vous pouvez également utiliser les menus contextuels à partir de la **pile des appels** fenêtre pour faire autre chose. Par exemple, vous pouvez insérer des points d’arrêt dans les fonctions spécifiées, faire avancer le débogueur à l’aide de **exécuter jusqu’au curseur**et accédez à examiner le code source. Pour plus d’informations, consultez [Comment : examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Pas à pas sortant

Supposons que vous avez terminé examinant le `Update` méthode dans Data.cs et que vous souhaitez tirer parti de la fonction, mais restent dans le débogueur. Vous pouvez le faire à l’aide de la **pas à pas sortant** commande.

1. Appuyez sur **MAJ** + **F11** (ou **Déboguer > pas à pas sortant**).

     Cette commande reprend l’exécution d’application (et avance le débogueur) jusqu'à ce que retourne la fonction active.

     Vous devez être revenu à la `Update` appel de méthode dans Data.cs.

2. Appuyez sur **MAJ** + **F11** à nouveau, et le débogueur remonte la pile des appels vers le `OnApplicationStartup` Gestionnaire d’événements.

## <a name="run-to-cursor"></a>Exécuter jusqu'au curseur

1. Choisissez le **arrêter le débogage** bouton rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") ou **MAJ** + **F5** .

2. Dans le `Update` méthode dans *Data.cs*, avec le bouton droit le `Add` appel de méthode et choisissez **exécuter jusqu’au curseur**. Cette commande démarre le débogage et définit un point d’arrêt temporaire sur la ligne de code active.

     ![Utiliser l’exécution de la fonctionnalité de curseur](../debugger/media/dbg-tour-run-to-cursor.png "exécuter jusqu’au curseur")

    Vous devez être suspendu sur le point d’arrêt dans `MainWindow` (puisque c’est le premier point d’arrêt vous définissez).

3. Appuyez sur **F5** pour accéder à la `Add` méthode où vous avez sélectionné **exécuter jusqu’au curseur**.

    Cette commande est utile lorsque vous modifiez du code et que vous souhaitez définir un point d’arrêt temporaire rapidement et de démarrer le débogueur.

## <a name="change-the-execution-flow"></a>Modifier le flux d’exécution

1. Avec le débogueur en pause sur le `Add` appel de méthode, utilisez la souris pour saisir la flèche jaune (le pointeur d’exécution) sur la gauche et déplacez la flèche jaune une ligne à la `foreach` boucle.

     ![Déplacer le pointeur d’exécution](../debugger/media/dbg-tour-move-the-execution-pointer.gif "déplacer le pointeur d’exécution")

    En modifiant le flux d’exécution, vous pouvez effectuer des opérations telles que les chemins d’exécution de code différent de test ou de réexécuter le code sans avoir à redémarrer le débogueur.

2. Maintenant, appuyez sur **F5**.

    Vous pouvez voir les images ajoutées à la fenêtre d’application. Étant donné que vous exécutez à nouveau le code dans le `foreach` boucle, certaines images ont été ajoutées à deux reprises !

    > [!WARNING]
    > Souvent, vous devez être prudent avec cette fonctionnalité, et un avertissement s’affiche dans l’info-bulle. Vous pouvez voir les autres avertissements, trop. Déplacer le pointeur ne peut pas rétablir votre application à un état antérieur de l’application.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations

1. Ouvrez *Data.cs* dans l’application de démonstration de visionneuse de photos, cliquez sur le `private void Update` déclaration de fonction et choisissez **exécuter jusqu’au curseur** (arrêter tout d’abord l’application si elle est déjà en cours d’exécution).

    Cela va suspendre l’application avec le débogueur attaché. Cela nous permet d’examiner son état.

2. Placez le curseur sur le `Add` méthode appeler et cliquez sur le **exécuter jusqu’au clic** bouton ![exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. Maintenant, placez le curseur sur l’objet de fichier (`f`) et que sa valeur de propriété par défaut, le nom de fichier *031. jpg du marché*.

     ![Afficher une bulle](../debugger/media/dbg-tour-data-tips.gif "afficher une info-bulle de données")

4. Développez l’objet pour afficher ses propriétés, telles que le `FullPath` propriété.

    Souvent, lors du débogage, vous souhaitez un moyen rapide de vérifier les valeurs de propriété sur les objets et les conseils de données constituent un bon moyen de le faire.

    > [!TIP]
    > Dans les langues prises en charge de plus, vous pouvez modifier le code au milieu d’une session de débogueur si vous trouvez quelque chose que vous souhaitez modifier. Pour plus d’informations, consultez [Modifier & Continuer](../debugger/edit-and-continue.md). Pour utiliser cette fonctionnalité dans cette application, toutefois, nous serait devons d’abord mettre à jour la version du .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les fenêtres automatique et variables locales

1. Examinez le **automatique** fenêtre en bas de l’éditeur de code.

     ![Inspecter des variables dans la fenêtre automatique](../debugger/media/dbg-tour-autos-window.png "fenêtre automatique")

    Dans le **automatique** fenêtre, vous voyez des variables et leur valeur actuelle. Le **automatique** fenêtre affiche toutes les variables utilisées dans la ligne actuelle ou de la ligne précédente (en C++, la fenêtre affiche les variables dans les trois lignes de code précédents. Consultez la documentation pour le comportement spécifique à la langue).

    > [!NOTE]
    > Dans JavaScript, le **variables locales** fenêtre est pris en charge, mais pas le **automatique** fenêtre.

2. Ensuite, examinons le **variables locales** fenêtre.

    Le **variables locales** fenêtre vous montre les variables qui se trouvent dans la portée actuelle.

    ![Inspecter des variables dans la fenêtre variables locales](../debugger/media/dbg-tour-locals-window.png "fenêtre variables locales")

    Actuellement, le `this` objet et l’objet de fichier (`f`) se trouvent dans la portée actuelle. Pour plus d’informations, consultez [inspecter des Variables dans le Windows de variables locales et automatique](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Définir un espion

1. Dans la fenêtre d’éditeur de code principal, cliquez sur l’objet de fichier (`f`) et choisissez **ajouter un espion**.

    Vous pouvez utiliser un **espion** fenêtre pour spécifier une variable (ou une expression) que vous souhaitez garder un œil sur.

    À présent, vous avez un espion défini sur le `File` objet et vous pouvez voir sa valeur changent à mesure que vous parcourez le débogueur. Contrairement à d’autres fenêtres de variables, le **espion** fenêtre affiche toujours les variables que vous surveillez (elles sont grisées lorsque hors de portée).

2. Sur le `Add` (méthode), cliquez sur le vert ![exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") bouton Nouveau (ou appuyez sur F11 à plusieurs fois) à travers le `foreach` boucle.

    ![Définir un espion sur une variable](../debugger/media/dbg-tour-watch-window.png "fenêtre Espion")

    Vous pouvez également voir la première image sont ajoutés à la fenêtre principale de l’exécution exemple d’application, mais cela se produit sur un thread d’application différents, les images ne sont pas encore forcément visibles.

    Pour plus d’informations, consultez [définir un espion à l’aide d’espion et Espion express Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Examiner une exception

1. Dans la fenêtre d’application en cours d’exécution, supprimez le texte dans le **chemin d’accès** zone d’entrée, puis sélectionnez le **modification** bouton.

     ![Lever une exception levée](../debugger/media/dbg-tour-cause-an-exception.png "provoquent une Exception")

     L’application lève une exception, et le débogueur vous amène à la ligne de code qui a levé l’exception.

     ![Assistance d’exception](../debugger/media/dbg-tour-exception-helper.png "assistance d’Exception")

     Ici, le **assistance d’Exception** vous montre une `System.ArgumentException` et un message d’erreur indiquant que le chemin d’accès n’est pas une forme conforme. Par conséquent, nous savons que l’erreur s’est produite sur un argument de méthode ou fonction.

     Dans cet exemple, le `DirectoryInfo` appelle a donné l’erreur sur la chaîne vide, stockée dans le `value` variable. (Placez le curseur sur `value` pour afficher la chaîne vide.)

     L’assistance de l’Exception est une fonctionnalité intéressante qui peut vous aider à déboguer les erreurs. Vous pouvez également effectuer des opérations comme vue Détails de l’erreur et ajouter un espion à partir de l’assistance de l’Exception. Ou, si nécessaire, vous pouvez modifier les conditions pour lever l’exception particulière.

    >  [!NOTE]
    > L’assistance d’Exception remplace l’Assistant Exception dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Développez le **paramètres d’Exception** nœud pour afficher davantage d’options sur la gestion de ce type d’exception, mais vous n’avez pas besoin de modifier quoi que ce soit pour cette visite guidée !

3. Appuyez sur **F5** pour continuer l’exécution de l’application.

Pour en savoir plus sur les fonctionnalités du débogueur, consultez [débogueur trucs et astuces](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment démarrer le débogueur, parcourir le code et inspecter les variables. Voulez-vous obtenir une vue d’ensemble des fonctionnalités de débogueur ainsi que des liens vers d’autres informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
