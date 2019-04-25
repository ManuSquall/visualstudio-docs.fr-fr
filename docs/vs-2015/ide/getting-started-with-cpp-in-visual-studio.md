---
title: Mise en route de C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae373742c114129c99e7b3444393e12c6c4dd8dd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057821"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Bien démarrer avec C++ dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En suivant cette procédure pas à pas, vous allez vous familiariser avec la plupart des outils et boîtes de dialogue que vous pouvez utiliser lorsque vous développez des applications avec Visual Studio. Vous allez créer une simple application de type « Hello, World », tout en approfondissant votre connaissance de l’utilisation de l’IDE (environnement de développement intégré).

 Cette rubrique contient les sections suivantes :

 [Se connecter à Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Créer une application simple](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Ajouter du code à l’application](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Déboguer et tester l’application](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Générer une version release de l’application](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

## <a name="BKMK_Configure"></a> Se connecter à Visual Studio
 Lorsque vous démarrez Visual Studio pour la première fois, vous avez la possibilité de vous connecter à l’aide d’un compte Microsoft tel que Live ou Outlook. La connexion permet que vos paramètres soient synchronisés sur tous vos appareils. Pour plus d’informations, consultez [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md)

 Figure 1 : IDE de Visual Studio

 ![IDE avec paramètres Visual C&#43;&#43; appliqués](../ide/media/c-ide-defaultenvironmentlayout.png "IDE_DefaultEnvironmentLayout C ++")

 Après avoir ouvert Visual Studio, vous pouvez voir les trois composants de base de l’IDE : les fenêtres Outil, les menus et les barres d’outils, ainsi que l’espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre d’application. **Lancement rapide**, la barre de menus et la barre d’outils standard se trouvent en haut. La **Page de démarrage**est située au centre de la fenêtre d’application. Lorsque vous ouvrez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans cet espace. Lorsque vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.

## <a name="BKMK_CreateApp"></a> Créer une application simple
 Lorsque vous créez une application dans Visual Studio, vous créez d’abord un projet et une solution. Dans cet exemple, vous allez créer une application console Windows.

#### <a name="to-create-a-console-app"></a>Pour créer une application console

1. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.

    ![Dans la barre de menus, choisissez Fichier, Nouveau, Projet](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. Dans la catégorie **Visual C++**, choisissez le modèle **Application console Win32**, puis nommez le projet `GreetingsConsoleApp`.

    ![Modèle d’application console Win32](../ide/media/c-ide-newprojectdlg.png "C++IDE_NewProjectDlg")

3. Lorsque l’Assistant Application Win32 s’affiche, sélectionnez le bouton **Terminer** .

    ![Assistant d’application console Win32](../ide/media/c-ide-win32consoleappwizard.png "C++IDE_Win32ConsoleAppWizard")

   La solution et le projet GreetingsConsoleApp, avec les fichiers de base d’une application console Win32, sont créés et chargés automatiquement dans l’ **Explorateur de solutions**. Le fichier GreetingsConsoleApp.cpp s’ouvre dans l’éditeur de code. Les éléments suivants apparaissent dans l’ **Explorateur de solutions**:

   Figure 4 : Éléments du projet

   ![Fichiers pour la solution dans l’Explorateur de solutions](../ide/media/c-ide-solutioncontents.png "C++IDE_SolutionContents")

## <a name="BKMK_AddCode"></a> Ajouter du code à l’application
 Ensuite, vous ajouterez le code pour afficher le mot « Hello » dans la fenêtre de console.

#### <a name="to-display-hello-in-the-console-window"></a>Pour afficher « Hello » dans la fenêtre de console

1. Dans le fichier GreetingsConsoleApp.cpp, entrez une ligne vide avant la ligne `return 0;` , puis entrez le code suivant :

    ```
    cout << "Hello\n";
    ```

     Une ligne ondulée rouge s’affiche sous `cout`. Un message d’erreur apparaît si vous pointez dessus.

     ![Texte d’erreur pour cout](../ide/media/c-ide-couterror.png "C++IDE_CoutError")

     Le message d’erreur s’affiche également dans la fenêtre **Liste d’erreurs** . Vous pouvez afficher la fenêtre en choisissant dans la barre de menus **Affichage**, **Liste d’erreurs**.

     [cout](http://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) est inclus dans le fichier d’en-tête \<iostream\>.

2. Pour inclure l’en-tête iostream, entrez le code suivant après `#include "stdafx.h"`:

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Vous avez probablement remarqué qu’une zone est apparue tandis que vous entriez le code et qu’elle vous a fourni des suggestions pour les caractères que vous tapiez. Cette zone fait partie de C++ IntelliSense, qui fournit des invites de codage, telles que la liste des membres de classe ou des membres d’interface et les informations de paramètre. Vous pouvez aussi utiliser des extraits de code, qui sont des blocs de code prédéfinis. Pour plus d’informations, consultez [Using IntelliSense](../ide/using-intellisense.md) et [Code Snippets](../ide/code-snippets.md).

     La ligne ondulée rouge sous `cout` disparaît lorsque vous corrigez l’erreur.

3. Enregistrez les modifications dans le fichier.

     ![Code qui corrige les erreurs cout](../ide/media/c-ide-coutfix.png "C++IDE_CoutFix")

## <a name="BKMK_DebugTest"></a> Déboguer et tester l’application
 Vous pouvez déboguer GreetingsConsoleApp pour voir si le mot « Hello » s’affiche dans la fenêtre de console.

#### <a name="to-debug-the-application"></a>Pour déboguer l’application

- Démarrez le débogueur.

     ![Commande Démarrer le débogage du menu Débogage](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

     Le débogueur démarre et exécute le code. La fenêtre de console (une fenêtre distincte qui ressemble à une invite de commandes) s’affiche pendant quelques secondes, mais se clôt rapidement lorsque le débogueur s’arrête en cours d’exécution. Pour afficher le texte, vous devez définir un point d’arrêt afin d’interrompre l’exécution du programme.

#### <a name="to-add-a-breakpoint"></a>Pour ajouter un point d’arrêt

1. Ajoutez un point d’arrêt à partir de la barre de menus dans la ligne `return 0;`. Vous pouvez également cliquer dans la marge de gauche pour définir un point d’arrêt.

    ![Commande Basculer le point d’arrêt du menu Débogage](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")

    Un cercle rouge apparaît à côté de la ligne de code dans la bordure gauche de la fenêtre de l’éditeur.

2. Appuyez sur la touche F5 pour démarrer le débogage.

    Le débogueur démarre et une fenêtre de console apparaît avec le mot **Hello**.

    ![Texte Hello dans la fenêtre d’invite de commandes Windows](../ide/media/c-ide-hellocommandwindow.png "C++IDE_HelloCommandWindow")

3. Appuyez sur Maj+F5 pour arrêter le débogage.

   Pour plus d’informations, consultez [Projets console](../debugger/debugging-preparation-console-projects.md).

## <a name="BKMK_BuildRelease"></a> Générer une version Release de l’application
 Maintenant que vous avez vérifié que tout fonctionne, vous pouvez préparer une version Release de l'application.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Pour nettoyer les fichiers solution et générer une version Release

1. Dans la barre de menus, supprimez les fichiers intermédiaires et les fichiers de sortie créés pendant les générations précédentes.

    ![Commande Nettoyer la solution du menu Générer](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Changez la configuration de build pour GreetingsConsoleApp de **Debug** en **Release**.

    ![Générer une version Release de l’application](../ide/media/c-ide-changingbuildtorelease.png "C++IDE_ChangingBuildtoRelease")

3. Générez la solution.

    ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Félicitations ! Vous avez terminé cette procédure. Pour explorer d’autres exemples, consultez [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : créer une application simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [Conseils de productivité](../ide/productivity-tips-for-visual-studio.md) [Exemples Visual Studio](../ide/visual-studio-samples.md) [Bien démarrer avec le développement avec Visual Studio](../ide/get-started-developing-with-visual-studio.md)
