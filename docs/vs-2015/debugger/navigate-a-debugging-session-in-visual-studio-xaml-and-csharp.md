---
title: Parcourir une session de débogage (Xaml et C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6a4ea19013aefa1b3d078ce5993d48b4694989c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949735"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Parcourir une session de débogage dans Visual Studio (XAML et C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce guide de démarrage rapide montre comment naviguer dans les sessions de débogage Visual Studio et comment afficher et modifier l'état du programme dans la session.

 Ce guide de démarrage rapide s'adresse aux développeurs qui découvrent le débogage avec Visual Studio et aux développeurs qui souhaitent apprendre à naviguer dans une session de débogage Visual Studio. Il n'explique pas les techniques de débogage. Les méthodes décrites dans l'exemple de code sont conçues pour illustrer les procédures de débogage décrites dans cette rubrique. Les méthodes n'utilisent pas les meilleures pratiques en matière de conception d'applications ou de fonctions. En fait, vous découvrirez rapidement que les méthodes, et l'application elle-même, ne font pas grand-chose.

 Les sections de ce guide de démarrage rapide ont été conçues pour être aussi indépendantes que possible. Vous pouvez sauter les sections qui contiennent des informations avec lesquelles vous êtes déjà familiarisé. Vous n'êtes pas non plus tenu de créer un exemple d'application. Toutefois, nous vous le recommandons et avons rendu le processus aussi simple que possible.

 **Raccourcis clavier du débogueur.** La navigation dans le débogueur Visual Studio est optimisée pour la souris et le clavier. Plusieurs étapes dans cette rubrique présentent l'accélérateur clavier ou la touche de raccourci dans une note entre parenthèses. Par exemple, (clavier : F5) indique que la touche F5 démarre ou continue l’exécution du débogueur.

## <a name="in-this-topic"></a>Dans cette rubrique
 Vous allez apprendre à :

-   [Créer un exemple d'application](#BKMK_CreateTheApplication)

-   [Définir et exécuter un point d'arrêt, exécuter une méthode pas-à-pas et examiner les données du programme](#BKMK_StepInto)

-   [Pas à pas détaillé, principal et sortant des méthodes](#BKMK_StepIntoOverOut)

-   [Définir un point d'arrêt conditionnel, exécuter le curseur et visualiser une variable](#BKMK_ConditionCursorVisualize)

-   [Modifier et continuer, récupérer à partir d'une exception](#BKMK_EditContinueRecoverExceptions)

##  <a name="BKMK_CreateTheApplication"></a> Créer un exemple d'application
 Le débogage est centré sur le code. Ainsi, l'exemple d'application utilise l'infrastructure de l'application Windows Store pour créer un fichier source dans lequel vous pouvez découvrir comment fonctionne la navigation dans une session de débogage et comment examiner et modifier l'état du programme. Tous les appels de code s'effectuent à partir du constructeur de la page principale. Aucun contrôle n'est ajouté et aucun événement n'est traité.

 **Créer une application Windows Store C# par défaut.** Ouvrez Visual Studio. Sur la page d'accueil, cliquez sur le lien **Nouveau projet** . Dans la boîte de dialogue Nouveau projet, choisissez **Visual C#** dans la liste **Installé** , puis **Windows Store**. Dans la liste de modèles de projet, choisissez **Application**. Visual Studio crée une solution et un projet, puis affiche le concepteur MainPage.xaml et l'éditeur de code XAML.

 **Ouvrir le fichier source MainPage.xaml.cs.** Cliquez avec le bouton droit n'importe où dans l'éditeur XAML et choisissez **Afficher le code**. Le fichier code-behind MainPage.xaml.cs s'affiche. Notez qu'une seule méthode, le constructeur `MainPage()` , est répertoriée dans le fichier.

 **Remplacer le constructeur MainPage par l'exemple de code.** Supprimez la méthode MainPage(). Suivez ce lien : [Exemple de code de navigation du débogueur (Xaml et C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md), puis copiez le code répertorié dans le C# section dans le Presse-papiers. (Choisissez **retour** dans le navigateur ou la visionneuse d’aide pour revenir à cette page de démarrage rapide.) Dans l'éditeur Visual Studio, collez le code dans le bloc `partial class MainPage`. Appuyez sur Ctrl+S pour enregistrer le fichier.

 Vous pouvez désormais vous référer aux exemples contenus dans cette rubrique.

##  <a name="BKMK_StepInto"></a> Définir et exécuter un point d'arrêt, exécuter une méthode pas-à-pas et examiner les données du programme
 La méthode la plus courante que vous pouvez démarrer une session de débogage consiste à choisir **démarrer le débogage** à partir de la **déboguer** menu (clavier : F5). L'exécution démarre et se poursuit jusqu'à ce qu'un point d'arrêt soit atteint, que vous suspendiez manuellement l'exécution, qu'une exception se produise ou que l'application se termine.

 Lorsque l'exécution est suspendue dans le débogueur, affichez la valeur d'une variable active dans une bulle d'informations en plaçant le pointeur de la souris au-dessus de la variable. Vous pouvez également ouvrir les fenêtres Variables locales et Automatique pour afficher les listes des variables actives et de leurs valeurs actuelles. L'ajout d'une ou plusieurs variables dans une fenêtre Espion permet de se concentrer sur la valeur des variables lorsque l'exécution de l'application se poursuit.

 Après avoir suspendu l'exécution de l'application (on parle également d'accéder au débogueur), vous contrôlez le mode d'exécution du reste du code du programme. Continuez ligne par ligne, déplacez-vous entre un appel de méthode et la méthode elle-même, ou exécutez une méthode appelée en une seule étape. Ces procédures désignent une exécution pas à pas du code de l'application. Vous pouvez également reprendre l'exécution standard de l'application, poursuivre l'exécution jusqu'au point d'arrêt que vous avez défini ou jusqu'à la ligne où vous avez positionné votre curseur. Vous pouvez arrêter la session de débogage à tout moment. Le débogueur est conçu pour effectuer les opérations de nettoyage et l'exécution de sortie nécessaires.

### <a name="example-1"></a>Exemple 1
 Dans cet exemple, vous définissez un point d'arrêt dans le constructeur MainPage du fichier MainPage.xaml.cs, vous exécutez pas-à-pas la première méthode, vous affichez les valeurs des variables et vous arrêtez le débogage.

 **Définir un point d'arrêt.** Définissez un point d'arrêt au niveau de l'instruction `methodTrack = "Main Page";` dans le constructeur MainPage. Sélectionnez la ligne dans la marge grisée de l’éditeur de code source (clavier : Positionnez le curseur sur la ligne et appuyez sur la touche F9).

 ![Pas à pas détaillé](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 L'icône du point d'arrêt apparaît dans la marge.

 **Lancer l'exécution jusqu'au point d'arrêt.** Démarrez la session de débogage en choisissant **démarrer le débogage** sur le **déboguer** menu (clavier : F5).

 L'exécution de l'application démarre et est suspendue immédiatement avant l'instruction au niveau de laquelle vous avez défini le point d'arrêt. L'icône de la ligne en cours dans la marge identifie l'emplacement et l'instruction en cours est mise en surbrillance.

 ![Définissez un point d’arrêt](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Vous êtes maintenant aux commandes de l'exécution de l'application et pouvez examiner l'état du programme lorsque vous exécutez pas-à-pas les instructions de programmation.

 **Exécuter pas-à-pas la méthode.** Sur le **déboguer** menu, choisissez **pas à pas détaillé** (clavier : F11).

 ![Ligne active](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Notez que le débogueur passe à la ligne suivante, ce qui correspond à un appel à la méthode Example1. Choisissez de nouveau Pas à pas détaillé. Le débogueur se déplace jusqu'au point d'entrée de la méthode Example1. Cela indique que la méthode a été chargée sur la pile des appels et que la mémoire des variables locales a été allouée.

 Lorsque vous effectuez une exécution pas-à-pas d'une ligne de code, le débogueur effectue l'une des opérations suivantes :

- Si l'instruction suivante n'est pas un appel à une fonction dans votre solution, le débogueur exécute l'instruction, passe à l'instruction, puis suspend l'exécution.

- Si l'instruction est un appel à une fonction dans votre solution, le débogueur passe au point d'entrée de la fonction appelée, puis suspend l'exécution.

  Continuez l'exécution pas-à-pas des instructions pour Example1 jusqu'au point de sortie. Le débogueur met en surbrillance l'accolade fermante de la méthode.

  **Examiner les valeurs de la variable dans la bulle d'informations.** Lorsque vous placez le pointeur de la souris au-dessus d'un nom de variable, le nom, la valeur et le type de la variable s'affichent dans une bulle d'informations.

  ![Bulle du débogueur](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Placez le pointeur de la souris au-dessus de la variable `a`. Notez le nom, la valeur et le type de données. Placez le pointeur de la souris au-dessus de la variable `methodTrack`. Notez à nouveau le nom, la valeur et le type de données.

  **Examiner les valeurs des variables dans la fenêtre Variables locales.** Dans la boîte de dialogue **Déboguer** , pointez sur **Fenêtres**, puis choisissez **Variables locales**. (Clavier : Alt+4).

  ![Fenêtre variables locales](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  Les fenêtres Variables locales forment une arborescence des paramètres et des variables de la fonction. Les propriétés d'une variable objet sont les nœuds enfants de l'objet lui-même. La variable `this` est un paramètre masqué dans chaque méthode d'objet qui représente l'objet lui-même. Dans ce cas, elle représente la classe MainPage. Comme `methodTrack` est membre de la classe MainPage, sa valeur et son type de données apparaissent dans une ligne sous `this`. Développez le nœud `this` pour afficher les informations de `methodTrack` .

  **Ajouter un espion à la variable methodTrack.** La variable `methodWatch` est utilisée dans ce guide de démarrage rapide pour montrer les méthodes appelées dans les exemples. Pour simplifier l'affichage de la valeur de la variable, ajoutez-la dans une fenêtre Espion. Cliquez avec le bouton droit sur le nom de la variable dans la fenêtre Variables locales, puis choisissez **Ajouter un espion**.

  ![Fenêtre Espion](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  Examinez plusieurs variables dans une fenêtre Espion. Les valeurs des variables espionnées, comme les valeurs affichées dans les fenêtres Variables locales et les bulles d'informations, sont mises à jour chaque fois que l'exécution est suspendue. Vous pouvez également ajouter des variables dans la fenêtre Espion de l'éditeur de code. Sélectionnez la variable à espionner, cliquez avec le bouton droit, puis choisissez **Ajouter un espion**.

##  <a name="BKMK_StepIntoOverOut"></a> Pas à pas détaillé, principal et sortant des méthodes
 Contrairement à l'exécution pas-à-pas d'une méthode appelée par une méthode parente, le survol d'une méthode exécute la méthode enfant, puis suspend l'exécution de la méthode d'appel lorsque l'exécution de la méthode parent reprend. Vous pouvez exécuter un survol d'une méthode lorsque vous êtes familiarisé avec le mode de fonctionnement de la méthode et que vous êtes sûr que l'exécution n'affectera pas le problème que vous analysez.

 Le survol d'une ligne de code qui ne contient pas d'appel de méthode exécute la ligne comme s'il s'agissait d'une exécution pas-à-pas.

 La sortie d'une méthode enfant continue l'exécution de la méthode, puis suspend l'exécution lorsque la méthode retourne le contrôle à la méthode d'appel. Vous pouvez effectuer une sortie de code d'une longue fonction si vous pensez que le reste de la fonction n'a pas d'importance.

 Le survol et la sortie de code d'une fonction permettent d'exécuter la fonction.

 ![Étape détaillé, principal et sortant des méthodes](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Exemple 2
 Dans cet exemple, vous effectuez les méthodes d'exécution pas-à-pas, de survol et de sortie de code.

 **Appeler la méthode Example2dans le constructeur MainPage.** Modifiez le constructeur MainPage et remplacez la ligne qui suit `methodTrack = String.Empty;` par `Example2();`.

 ![Appelez Example2 méthode à partir de la méthode de démonstration](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **Lancer l'exécution jusqu'au point d'arrêt.** Démarrez la session de débogage en choisissant **démarrer le débogage** sur le **déboguer** menu (clavier : F5). Le débogueur interrompt l'exécution au point d'arrêt.

 **Effectuer un survol de la ligne de code.** Sur le **déboguer** menu, choisissez **pas à pas principal** (clavier : F10). Le débogueur exécute l'instruction `methodTrack = "MainPage";` de la même manière que l'exécution pas-à-pas.

 **Exécuter pas-à-pas Example2 et Example2_A.** Choisissez la touche F11 pour exécuter pas-à-pas la méthode de l'exemple 2. Continuez l'exécution pas-à-pas des instructions Example2 jusqu'à la ligne `int x = Example2_A();`. Une fois encore, effectuez une exécution pas-à-pas de cette ligne jusqu'au point d'entrée d'Example2_A. Continuez l'exécution pas-à-pas entrer pour chaque instruction d'Example2_A jusqu'à ce que vous retourniez à Example2.

 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **Survol d'une fonction.** Notez que la ligne suivante dans Example2, `int y = Example2_A();` est en fait identique à la ligne précédente. Vous pouvez effectuer sans risque le survol de cette ligne. Choisissez la touche F10 pour passer de la reprise d'Example2 à ce deuxième appel d'Example2_A. Choisissez F10 pour effectuer le survol de cette méthode. Notez que la chaîne `methodTrack` indique que la méthode Example2_A a été exécutée deux fois. Vous remarquerez également que le débogueur passe immédiatement sur la ligne suivante. Il ne suspend pas l'exécution au point de reprise Example2.

 **Sortie de code d'une fonction.** Choisissez la touche F11 pour exécuter pas-à-pas la méthode d'Example2_B. Notez que Example2_B n'est pas très différent d'Example2_A. Pour sortir de la méthode, choisissez **pas à pas sortant** sur le **déboguer** menu (clavier : MAJ + F11). Notez que la variable `methodTrack` indique qu'Example2_B a été exécuté et que le débogueur est retourné au point de reprise d'Example2.

 **Arrêter le débogage.** Dans le menu Déboguer, choisissez Arrêter le débogage (clavier : MAJ + F5). La session de débogage se termine.

##  <a name="BKMK_ConditionCursorVisualize"></a> Définir un point d'arrêt conditionnel, exécuter le curseur et visualiser une variable
 Un point d'arrêt conditionnel désigne une condition qui entraîne la suspension de l'exécution par le débogueur. La condition est spécifiée par une expression de code qui peut être évaluée comme valeur true ou false. Par exemple, vous pouvez utiliser un point d'arrêt conditionnel pour examiner l'état du programme dans une méthode souvent appelée uniquement si une variable atteint une certaine valeur.

 L'exécution jusqu'au curseur revient à définir un point d'arrêt ponctuel. Lorsque l'exécution est suspendue, sélectionnez une ligne dans le code source et reprenez l'exécution jusqu'à la ligne sélectionnée. Par exemple, vous pouvez exécuter pas-à-pas une boucle dans une méthode et confirmer que le code dans la boucle est exécuté correctement. Au lieu d'une exécution pas-à-pas pour chaque itération de la boucle, lancez l'exécution jusqu'au curseur qui est positionné après l'exécution de la boucle.

 Parfois, il est difficile d'afficher une valeur de variable dans la ligne de la bulle d'informations ou de la fenêtre de variables. Le débogueur peut afficher des chaînes, le code HTML et XML dans un visualiseur de texte qui présente une vue mise en forme de la valeur dans une fenêtre déroulante.

### <a name="example-3"></a>Exemple 3
 Dans cet exemple, vous définissez un point d'arrêt conditionnel pour s'arrêter au niveau d'une itération spécifique d'une boucle, puis vous lancez l'exécution jusqu'au curseur positionné après la boucle. Vous affichez également la valeur d'une variable dans un visualiseur de texte.

 **Appeler la méthode Example3 dans le constructeur MainPage.** Modifiez le constructeur MainPage et remplacez la ligne qui suit `methodTrack = String.Empty;` par la ligne `Example3();`.

 ![Exemple3 d’appel de la méthode de démonstration](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **Lancer l'exécution jusqu'au point d'arrêt.** Démarrez la session de débogage en choisissant **démarrer le débogage** sur le **déboguer** menu (clavier : F5). Le débogueur suspend l'exécution au point d'arrêt dans la méthode MainPage.

 **Exécuter pas-à-pas la méthode Example3.** Choisissez **pas à pas détaillé** sur le **déboguer** menu (clavier : Touche F11) pour déplacer vers le point d’entrée de la méthode Example3. Reprend l'exécution pas-à-pas dans la méthode jusqu'à l'itération d'une ou deux boucles du bloc `for` . Notez que l'exécution pas-à-pas de toutes les 1 000 itérations peut prendre du temps.

 **Définir un point d'arrêt conditionnel.** Dans la marge gauche de la fenêtre du code, cliquez avec le bouton droit sur la ligne `x += i;` , puis choisissez **Condition**. Sélectionnez la case à cocher **Condition** , puis entrez `i == 500;` dans la zone de texte. Choisissez l'option **Est VRAI** , puis **OK**. Le point d'arrêt permet de vérifier la valeur à la 500 ème itération de la boucle `for` .

 ![Boîte de dialogue de Condition de point d’arrêt](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Vous pouvez identifier une icône de point d'arrêt conditionnel par la croix blanche associée.

 ![Point d’arrêt conditionnel](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **Lancer l'exécution jusqu'au point d'arrêt.** Dans le menu Déboguer, cliquez sur Continuer (clavier : F5). Dans la fenêtre Variables locales, vérifiez que la valeur actuelle de `i` est égale à 500. Notez que la variable `s` est représentée comme une ligne unique et est beaucoup plus longue que la fenêtre.

 **Visualiser une variable chaîne.** Cliquez sur l'icône de loupe dans la colonne **Valeur** de `s`.

 La fenêtre du visualiseur de texte apparaît et la valeur de la chaîne est présentée comme chaîne multiligne.

 **Lancer l'exécution jusqu'au curseur.** Cliquez sur la ligne `methodTrack += "->Example3";` , puis **exécuter jusqu’au curseur** (clavier : Placer le curseur sur la ligne ; CTRL + F10). Le débogueur exécute les itérations de boucle, puis suspend l'exécution au niveau de la ligne.

 **Arrêter le débogage.** Dans le menu Déboguer, choisissez Arrêter le débogage (clavier : MAJ + F5). La session de débogage se termine.

##  <a name="BKMK_EditContinueRecoverExceptions"></a> Modifier et continuer, récupérer à partir d'une exception
 Dans certaines circonstances, lorsque vous vous arrêtez dans le code du débogueur Visual Studio vous avez la possibilité de modifier la valeur des variables et même la logique des instructions. Cette fonctionnalité est appelée « modifier et continuer ».

 La fonction modifier et continuer peut être particulièrement utile lorsque vous vous arrêtez au niveau d'une exception. Au lieu de s'arrêter et de redémarrer le débogage d'une procédure longue et complexe pour éviter l'exception, vous pouvez « dérouler » l'exception pour déplacer l'exécution au point juste avant l'endroit où l'exception s'est produite, puis modifier la variable ou l'instruction incriminée et continuer la session de débogage en cours dans un état qui n'entraîne pas d'exception.

 Même si vous pouvez utiliser la fonction modifier et continuer dans un grand nombre situations, il est difficile de spécifier les conditions spécifiques qui ne prennent pas en charge cette fonction, car elles dépendent du langage de programmation, de l'état actuel de la pile du programme et de la capacité du débogueur à changer d'état sans nuire au processus. Le meilleur moyen pour déterminer si une modification est prise en charge est simplement d'essayer. Le débogueur permet de savoir immédiatement si la modification n'est pas prise en charge.

### <a name="example-4"></a>Exemple 4
 Dans cet exemple, vous exécutez le débogueur jusqu'à une exception, vous remontez l'exception, vous corrigez la logique de la méthode, puis vous modifiez la valeur d'une variable afin que vous puissiez continuer l'exécution de la méthode.

 **Appeler la méthode Example4 dans le constructeur MainPage.** Modifiez le constructeur MainPage() et remplacez la ligne qui suit `methodTrack = String.Empty;` par la ligne `Example4();`.

 ![Exemple4 d’appel de la méthode de démonstration](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Lancer l'exécution jusqu'à l'exception.** Démarrez la session de débogage en choisissant **démarrer le débogage** sur le **déboguer** menu (clavier : F5). Appuyez de nouveau sur F5 pour reprendre l'exécution. Le débogueur suspend l'exécution au niveau de l'exception de la méthode Example4 et affiche une boîte de dialogue d'exception.

 ![Boîte de dialogue d’exception](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Modifier la logique du programme.** Il est évident que l'erreur se trouve dans la condition `if` : la valeur `x` doit être modifiée lorsque `x` est égal à 0 ; non lorsque `x` n'est pas égal à zéro. Choisissez **Arrêter** pour corriger la logique de la méthode. Lorsque vous essayez de modifier la ligne, une autre boîte de dialogue s'affiche.

 ![Modifier et continuer, boîte de dialogue](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 Choisissez **Modifier** , puis remplacez la ligne `if (x != 0)` par `if (x == 0)`. Le débogueur rend les modifications de la logique de programme permanentes dans le fichier source.

 **Modifier la valeur de la variable.** Examinez la valeur `x` dans une bulle d'informations ou dans la fenêtre Variables locales. Elle est toujours égale à 0 (zéro). Si vous essayez d'exécuter l'instruction qui a provoqué l'exception d'origine, elle sera de nouveau déclenchée. Vous pouvez modifier la valeur `x`. Dans la fenêtre Variables locales, double-cliquez sur la colonne de **Valeur** de la ligne **x** . Remplacez la valeur 0 par 1.

 ![Modifier une valeur dans la fenêtre variables locales](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Choisissez la touche F11 pour lancer une exécution pas-à-pas de l'instruction qui a levé précédemment une exception. Notez que la ligne s'exécute sans erreur. Choisissez de nouveau la touche F11.

 **Arrêter le débogage.** Sur le **déboguer** menu, choisissez **arrêter le débogage** (clavier : MAJ + F5). La session de débogage se termine.

## <a name="see-also"></a>Voir aussi
 [Démarrer une session de débogage (VB, C#, C++ et XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [déclencheur suspendre, reprendre, événements et d’arrière-plan pour le Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
