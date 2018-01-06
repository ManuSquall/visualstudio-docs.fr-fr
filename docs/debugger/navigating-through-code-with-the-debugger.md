---
title: "Parcourir le Code avec le débogueur dans Visual Studio | Documents Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2c45f6cfa37ee8593da08d59071d8244b08feac7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="navigate-code-with-the-visual-studio-debugger"></a>Parcourir le Code avec le débogueur Visual Studio
Vous familiariser avec les commandes et des raccourcis pour parcourir le code dans le débogueur, et qui rend plus rapide et plus facile rechercher et résoudre les problèmes de votre application. Pendant que vous naviguez dans le code dans le débogueur, vous pouvez examiner l’état de votre application ou en savoir plus sur ses flux d’exécution.  
  
## <a name="start-debugging"></a>Démarrer le débogage  
 Souvent, vous démarrez une session de débogage à l’aide **F5** (**déboguer** > **démarrer le débogage**). Cette commande démarre votre application avec le débogueur attaché.  
  
 La flèche verte démarre également le débogueur (identique à **F5**).  
  
 ![DBG &#95; Principes de base &#95; Démarrer &#95; le débogage](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
 Incluent d’autres manières que vous pouvez démarrer l’application avec le débogueur attaché **F11** ([pas à pas détaillé code](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([pas à pas principal code](#BKMK_Step_over_Step_out)), ou par à l’aide de **exécuter jusqu’au curseur**.  Consultez les autres sections de cette rubrique pour plus d’informations sur les opérations de ces options.  
  
 Lorsque vous déboguez, la ligne jaune indique le code qui sera exécutée ensuite.  
  
 ![DBG &#95; Principes de base &#95; Saut de &#95; Mode](../debugger/media/dbg_basics_break_mode.png "DBG_Basics_Break_Mode")  
  
 Pendant le débogage, vous pouvez basculer entre les commandes telles que **F5**, **F11** et utiliser d’autres fonctionnalités décrites dans cette rubrique (comme les points d’arrêt) pour accéder rapidement au code que vous souhaitez consulter.  
  
 La plupart des fonctionnalités du débogueur, comme l’affichage des valeurs des variables dans la fenêtre variables locales ou l’évaluation des expressions dans la fenêtre Espion, sont disponibles uniquement lorsque le débogueur est suspendu (également appelé *en mode arrêt*). Lorsque le débogueur est en pause, état de votre application est interrompue lors de fonctions, variables, et les objets restent en mémoire. En mode arrêt, vous pouvez examiner les positions et états à la recherche de violations ou de bogues. Pour certains types de projet, vous pouvez également effectuer des ajustements à l’application en mode arrêt. Pour visionner une vidéo ces fonctionnalités, consultez [mise en route avec le débogueur](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a>L’étape dans du code, ligne par ligne  
 Pour arrêter de chaque ligne de code (chaque instruction) pendant le débogage, utilisez le **F11** raccourci clavier (ou **déboguer** > **pas à pas détaillé** dans le menu).  
  
> [!TIP]
>  Lorsque vous exécutez chaque ligne de code, vous pouvez pointer sur les variables à leurs valeurs, ou utiliser le [variables locales](../debugger/autos-and-locals-windows.md) et [espion](../debugger/autos-and-locals-windows.md) pour observer les modifier leurs valeurs.  
  
 Voici quelques détails sur le comportement du **pas à pas détaillé**:  
  
-   Dans un appel à plusieurs fonctions imbriquées, **Pas à pas détaillé** va jusqu'à la fonction se trouvant au niveau le plus profond. Si vous utilisez **Pas à pas détaillé** dans un appel tel que `Func1(Func2())`, le débogueur parcourt la fonction `Func2`.  
  
-   En fait, le débogueur parcourt les instructions de code plutôt que les lignes physiques. Par exemple, une clause `if` peut être écrite sur une ligne :  
  
    ```CSharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```VB  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Lorsque vous parcourez cette ligne, le débogueur traite la condition comme une étape et la conséquence comme une autre (dans cet exemple, la condition est remplie).  
  
 Pour suivre visuellement la pile des appels lors de l’exécution pas à pas dans les fonctions, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a>Parcourir le code, ignorer des fonctions  
 Lors de l’exécution de code dans le débogueur, fréquence à laquelle vous bénéficiez des avantages que vous n’avez pas besoin de voir ce qui se passe dans une fonction particulière (vous ne vous souciez il ou qu’elle fonctionne, comme le code de bibliothèque bien testé). Utilisez ces commandes pour parcourir le code (les fonctions s’exécutent toujours, bien sûr, mais le débogueur ignore les).  
  
|Commande de clavier|Commande de menu|Description|  
|----------------------|------------------|-----------------|  
|**F10**|**Pas à pas principal**|Si la ligne actuelle contient un appel de fonction, **pas à pas principal** exécute le code, puis suspend l’exécution à la première ligne de code après le retour de la fonction appelée.|  
|**MAJ + F11**|**Pas à pas sortant**|**Pas à pas sortant** continue l’exécution du code et suspend l’exécution lorsque la fonction en cours est retournée (le débogueur ignore via la fonction en cours).|  
  
> [!TIP]
>  Si vous avez besoin rechercher le point d’entrée dans votre application, commencez par **F10** ou **F11**. Ces commandes sont souvent utiles lorsque vous recherchez plus d’informations sur son flux d’exécution ou inspecter l’état de votre application.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Exécuter à un emplacement spécifique ou d’une fonction  
 Fréquence à laquelle la méthode recommandée de débogage de code, ces méthodes sont utiles lorsque vous savez exactement quel code que vous voulez inspecter, ou au moins vous savez où vous souhaitez démarrer le débogage.  
  
-   **Définir des points d'arrêt dans le code**  
  
     Pour définir un point d'arrêt simple dans votre code, ouvrez le fichier source dans l'éditeur Visual Studio. Définissez le curseur sur la ligne de code où vous souhaitez suspendre l’exécution, puis avec le bouton droit dans la fenêtre de code pour afficher le menu contextuel et choisissez **point d’arrêt > Insérer un point d’arrêt** (ou appuyez sur **F9**). Le débogueur interrompt à droite de l’exécution avant l’exécution de la ligne.  
  
     ![Définir un point d’arrêt](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Les points d'arrêt dans Visual Studio fournissent un ensemble enrichi de fonctionnalités supplémentaires, telles que les points d'arrêt et les points de trace conditionnels. Consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md).  
  
-   **Exécuter le code jusqu'à l'emplacement du curseur**  
  
     Pour exécuter le code jusqu'à l'emplacement du curseur, placez le curseur sur une ligne de code exécutable dans une fenêtre source. Dans le menu contextuel de l’éditeur (avec le bouton droit dans l’éditeur), choisissez **exécuter jusqu’au curseur**. Cela ressemble à définir un point d’arrêt temporaire.

-   **Exécuter à, cliquez sur** 

    Pour exécuter un point dans votre code pendant la suspension dans le débogueur, sélectionnez le **exécuter ici** icône de flèche verte (vous voyez l’icône tout en pointant sur une ligne de code). Cela élimine le besoin de définir des points d’arrêt temporaires.

    ![Exécution du débogueur. Cliquez ensuite sur](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

    > [!NOTE]
    > **Cliquez sur exécuter** est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].
  
-   **S'arrêter manuellement dans le code**  
  
     Pour vous arrêter sur la ligne de code suivante disponible dans une application en cours d'exécution, choisissez **Déboguer**, **Interrompre tout** (raccourci : **Ctrl+Alt+Break**). 
  
     Si vous arrêtez l’exécution de code sans les fichiers sources ou de symboles (.pdb) correspondants, le débogueur affiche une page **Fichiers sources introuvables** ou **Symboles introuvables** qui peut vous aider à trouver les fichiers appropriés. Consultez [spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Si vous ne pouvez pas accéder aux fichiers de prise en charge, vous pouvez tout de même déboguer les instructions assembleur dans la fenêtre Code Machine.  
  
-   **Exécuter le code jusqu'à une fonction de la pile des appels**  
  
     Dans le **pile des appels** fenêtre (disponible lors du débogage), sélectionnez la fonction, avec le bouton droit et choisissez **exécuter jusqu’au curseur**. Pour suivre visuellement la pile des appels, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Exécuter le code jusqu'à une fonction spécifiée par nom**  
  
     Vous pouvez demander au débogueur d’exécuter votre application jusqu'à ce qu’il atteigne une fonction spécifiée. Vous pouvez spécifier la fonction par nom ou la sélectionner dans la pile des appels.  
  
     Pour spécifier une fonction par nom, choisissez **Déboguer**, **Nouveau point d'arrêt**, **Interrompre à la fonction**, puis tapez le nom de la fonction et d'autres informations d'identification.  
  
     ![Boîte de dialogue Nouveau point d’arrêt](../debugger/media/dbg_execution_newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Si la fonction est surchargée ou si elle figure dans plusieurs espaces de noms, vous pouvez choisir les fonctions souhaitées dans la boîte de dialogue **Choisir les points d'arrêt** .  
  
     ![Choisissez la boîte de dialogue points d’arrêt](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a>Déplacez le pointeur pour modifier le flux d’exécution  
 Lorsque le débogueur est suspendu, vous pouvez déplacer le pointeur d’instruction pour définir l’instruction suivante de code à exécuter. Dans la marge d'une fenêtre source ou Code Machine, une flèche jaune marque l'emplacement de la prochaine instruction à exécuter. Déplacer cette flèche permet d'ignorer une partie du code ou de revenir à une ligne déjà exécutée. Vous pouvez utiliser cette fonctionnalité, par exemple, pour ignorer une section de code qui contient un bogue connu.  
  
 ![Déplacer le pointeur](../debugger/media/dbg_basics_example3.gif "DBG_Basics_Example3")
  
 Pour définir l'instruction suivante à exécuter, appliquez l'une de ces procédures :  
  
-   Dans une fenêtre source, faites glisser la flèche jaune vers l'emplacement où vous souhaitez définir l'instruction suivante dans le même fichier source.  
  
-   Dans une fenêtre source, définissez le curseur sur la ligne que vous souhaitez exécuter ensuite, avec le bouton droit et choisissez **définir l’instruction suivante**.  
  
-   Dans la fenêtre code machine, définissez le curseur sur l’instruction d’assembly que vous souhaitez exécuter ensuite, cliquez sur un et choisissez **définir l’instruction suivante**.  
  
> [!CAUTION]
>  Le fait de définir l'instruction suivante fait en sorte que le compteur du programme accède directement au nouvel emplacement. Utilisez cette commande avec précaution :  
>   
>  -   Les instructions entre les nouveaux et les anciens points d'exécution ne sont pas exécutées.  
> -   Si vous déplacez le point d'exécution vers l'arrière, les instructions déjà traitées ne sont pas annulées.  
> -   Le déplacement de l'instruction suivante vers une autre fonction ou portée entraîne généralement une altération de la pile des appels, provoquant une erreur ou exception d'exécution. Si vous tentez de déplacer l'instruction suivante vers une autre portée, le débogueur ouvre une boîte de dialogue avec un avertissement et vous donne une occasion d'annuler l'opération. En Visual Basic, vous ne pouvez pas déplacer l'instruction suivante à une autre portée ou fonction.  
> -   En C++ natif, si les contrôles d'exécution sont activés, la définition de l'instruction suivante peut provoquer la levée d'une exception lorsque l'exécution atteint la fin de la méthode.  
> -   Lorsque Modifier &amp; Continuer est activé, la commande **Définir l'instruction suivante** échoue si vous avez apporté des modifications qui ne peuvent pas être remappées immédiatement par Modifier &amp; Continuer. Par exemple, cela peut se produire si vous avez modifié le code contenu dans un bloc catch. Dans ce cas, vous verrez un message d’erreur indiquant que l’opération n’est pas pris en charge.  
  
> [!NOTE]
>  Dans du code managé, vous ne pouvez pas déplacer l'instruction suivante dans les conditions suivantes :  
>   
>  -   L'instruction suivante se trouve dans une méthode différente de celle de l'instruction actuelle.  
> -   Le débogage a été démarré à l'aide du débogage juste-à-temps.  
> -   Le déroulement d'une pile des appels est en cours.  
> -   Une exception System.StackOverflowException ou System.Threading.ThreadAbortException a été levée.  
  
 Il est impossible de définir l'instruction suivante lorsque l'application est active. Pour définir l'instruction suivante, le débogueur doit être en mode arrêt.  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Pas à pas détaillé code non-utilisateur  
 Par défaut, le débogueur essaie d’afficher uniquement votre code d’application pendant le débogage, qui est déterminé par un débogueur appelé *uniquement mon Code*. (Consultez [uniquement mon Code](../debugger/just-my-code.md) pour voir comment cela fonctionne pour les langues et différents types de projet et comment vous pouvez personnaliser le comportement.) Cependant, parfois pendant le débogage, vous pouvez souhaiter examiner du code framework, votre code de bibliothèque tierce ou les appels au système d’exploitation (appels système).  
  
 Vous pouvez désactiver uniquement mon Code en accédant à **outils** > **Options** > **débogage** et désactivez la **activer uniquement mon Code** case à cocher.  
  
 Lorsque uniquement mon Code est désactivée, le débogueur peut exécuter dans le code de non-utilisateur et code non-utilisateur apparaît dans les fenêtres du débogueur.  
  
> [!NOTE]
>  Uniquement mon code n'est pas pris en charge pour les projets Smart Device.  
  
 **Effectuer un pas à pas détaillé dans des appels système**  
  
 Si vous avez chargé des symboles de débogage pour le code système et uniquement mon Code n’est pas activé, vous pouvez exécuter dans un appel système tout comme n’importe quel autre appel.  
  
 Pour accéder aux fichiers de symboles Microsoft, consultez [utiliser des serveurs de symboles pour rechercher des fichiers de symboles pas sur votre ordinateur local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) dans les [spécifier de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) rubrique.  
  
 Pour charger des symboles pour un composant système spécifique lors du débogage :  
  
1.  Ouvrez la fenêtre Modules (clavier : **Ctrl + Alt + U**).  
  
2.  Sélectionnez le module pour lequel vous souhaitez charger des symboles.  
  
     Consultez la colonne **État du symbole** pour connaître les modules qui possèdent des symboles chargés.  
  
3.  Choisissez **Charger les symboles** dans le menu contextuel.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Effectuer un pas à pas détaillé dans des propriétés et des opérateurs au sein du code managé  
 Par défaut, le débogueur effectue un pas à pas principal sur les propriétés et les opérateurs dans le code managé. Dans la plupart des cas, cela fournit une meilleure expérience de débogage. Pour activer le pas à pas détaillé dans les propriétés ou des opérateurs, choisissez **déboguer** > **Options**. Sur le **débogage** > **général** page, désactivez la **pas à pas principal des propriétés et les opérateurs (managé uniquement)** case à cocher