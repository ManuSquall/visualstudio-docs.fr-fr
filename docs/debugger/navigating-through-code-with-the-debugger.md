---
title: "Naviguer dans le code avec le d&#233;bogueur | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.execution"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "déboguer (Visual Studio), contrôle d'exécution"
  - "exécution, contrôler dans le débogueur"
  - "exécuter pas à pas"
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 42
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Naviguer dans le code avec le d&#233;bogueur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il existe de nombreuses façons de parcourir votre code dans le débogueur : vous pouvez effectuer un pas à pas détaillé ou principal des méthodes, exécuter le code jusqu'à un point d'arrêt ou un emplacement spécifié, et indiquer si vous voulez limiter le débogage à votre propre code ou inclure des symboles pour déboguer le code externe.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Effectuer un pas à pas détaillé, principal ou sortant  
 L'une des procédures de débogage les plus communes est l'*exécution pas à pas*. L'exécution pas à pas consiste à exécuter le code ligne par ligne. Lorsque vous avez interrompu l'exécution, par exemple en exécutant le débogueur à un point d'arrêt, vous pouvez utiliser trois commandes du menu **Déboguer** pour parcourir votre code :  
  
|Commande de menu|Raccourci clavier|Description|  
|----------------------|-----------------------|-----------------|  
|**Pas à pas détaillé**|**F11**|Si la ligne contient un appel à une fonction, **Pas à pas détaillé** n'exécute que l'appel, puis s'arrête à la première ligne de code se trouvant dans la fonction. Sinon, **Pas à pas détaillé** exécute l'instruction suivante.|  
|**Pas à pas principal**|**F10**|Si la ligne contient un appel à une fonction, **Pas à pas principal** exécute la fonction appelée, puis s'arrête à la première ligne de code se trouvant dans la fonction appelante. Sinon, **Pas à pas détaillé** exécute l'instruction suivante.|  
|**Pas à pas sortant**|**Shift\+F11**|**Pas à pas sortant** reprend l'exécution de votre code jusqu'au retour de la fonction, puis opère une interruption au point de retour dans la fonction appelante.|  
  
-   Dans un appel à plusieurs fonctions imbriquées, **Pas à pas détaillé** va jusqu'à la fonction se trouvant au niveau le plus profond. Si vous utilisez **Pas à pas détaillé** dans un appel tel que `Func1(Func2())`, le débogueur parcourt la fonction `Func2`.  
  
-   En fait, le débogueur parcourt les instructions de code plutôt que les lignes physiques. Par exemple, une clause `if` peut être écrite sur une ligne :  
  
    ```c#  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```vb  
    Dim x As Integet = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Lorsque vous parcourez cette ligne, le débogueur traite la condition comme une étape et la conséquence comme une autre \(dans cet exemple, la condition est remplie\).  
  
 Pour afficher la trace de la pile des appels tout en effectuant un pas à pas détaillé dans les fonctions, consultez [Mapper les méthodes sur la pile des appels tout en déboguant](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> S'arrêter dans le code en utilisant des points d'arrêt ou Interrompre tout  
 Lorsque vous déboguez une application avec le débogueur VS, elle est soit en cours d'exécution, soit en mode arrêt.  
  
 Le débogueur interrompt l'exécution de l'application lorsqu'il rencontre un point d'arrêt ou lorsqu'une exception se produit. Vous pouvez également interrompre manuellement l'exécution à tout moment.  
  
 Un point d'arrêt est un signal qui indique au débogueur de suspendre temporairement l'exécution de votre application à un certain point. Lorsque l'exécution est suspendue au niveau d'un point d'arrêt, votre programme est dit en mode arrêt. Le passage en mode arrêt ne termine pas l'exécution de votre programme, qui peut reprendre à tout moment.  
  
 La plupart des fonctionnalités du débogueur, comme l'affichage des valeurs des variables dans la fenêtre Variables locales ou l'évaluation des expressions dans la fenêtre Espion, sont disponibles uniquement en mode arrêt. Tous les éléments de votre application \(fonctions, variables et objets, par exemple\) restent en mémoire, mais leurs mouvements et leurs activités sont suspendus. En mode arrêt, vous pouvez examiner leurs positions et états à la recherche de violations ou de bogues. Vous pouvez également apporter des réglages à l'application en mode arrêt.  
  
 Vous pouvez configurer des points d'arrêt pour interrompre l'exécution selon plusieurs conditions. Consultez [Utilisation des points d'arrêt](../debugger/using-breakpoints.md). Cette section décrit deux méthodes de base pour arrêter le code.  
  
1.  **Définir des points d'arrêt dans le code**  
  
     Pour définir un point d'arrêt simple dans votre code, ouvrez le fichier source dans l'éditeur Visual Studio. Définissez le curseur sur la ligne de code à laquelle vous souhaitez vous arrêter, puis choisissez **Point d'arrêt**, **Insérer un point d'arrêt** dans le menu contextuel \(raccourci : **F9**. Le débogueur interrompt l'exécution juste avant que la ligne soit exécutée.  
  
     ![Définir un point d’arrêt](~/debugger/media/dbg_basics_setbreakpoint.png "DBG\_Basics\_SetBreakpoint")  
  
     Les points d'arrêt dans Visual Studio fournissent un ensemble enrichi de fonctionnalités supplémentaires, telles que les points d'arrêt et les points de trace conditionnels. Consultez [Utilisation des points d'arrêt](../debugger/using-breakpoints.md).  
  
2.  **S'arrêter manuellement dans le code**  
  
     Pour vous arrêter sur la ligne de code suivante disponible dans une application en cours d'exécution, choisissez **Déboguer**, **Interrompre tout** \(raccourci : **Ctrl\+Alt\+Break**\).  
  
-   Si vous déboguez avec l'option Uniquement mon code activée, l'exécution s'interrompt à la ligne de code suivante dans votre projet. Consultez [Limiter le pas à pas à Uniquement mon code](#BKMK_Restrict_stepping_to_Just_My_Code).  
  
-   Si vous déboguez plusieurs programmes, un point d'arrêt ou une commande Interrompre tout affecte par défaut tous les programmes en cours de débogage. Consultez [Configurer le comportement d'exécution de plusieurs processus](../debugger/debug-multiple-processes.md#BKMK_Configure_the_execution_behavior_of_multiple_processes).  
  
-   Si vous arrêtez l’exécution de code sans les fichiers sources ou de symboles \(.pdb\) correspondants, le débogueur affiche une page **Fichiers sources introuvables** ou **Symboles introuvables** qui peut vous aider à trouver les fichiers appropriés. Consultez [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
     Si vous ne pouvez pas accéder aux fichiers de prise en charge, vous pouvez tout de même déboguer les instructions assembleur dans la fenêtre Code Machine.  
  
##  <a name="BKMK_Run_to_a_specified_location_or_function"></a> Exécuter à un emplacement ou une fonction spécifié\(e\)  
 Parfois, il est nécessaire d'exécuter le code jusqu'à un certain point, puis d'interrompre l'exécution. Si un point d'arrêt est défini à l'emplacement où vous souhaitez interrompre l'exécution, choisissez **Déboguer**, **Démarrer le débogage** si vous n'avez pas démarré le débogage, ou **Déboguer**, **Continuer**. \(Dans les deux cas, le raccourci est **F5**.\) Le débogueur s'arrête au point d'arrêt suivant dans l'exécution du code. Sélectionnez **Déboguer**, **Continuer** jusqu'à atteindre le point d'arrêt souhaité.  
  
 Vous pouvez également exécuter le code jusqu'à l'emplacement du curseur dans l'éditeur de code ou jusqu'à la fonction spécifiée.  
  
 **Exécuter le code jusqu'à l'emplacement du curseur**  
  
 Pour exécuter le code jusqu'à l'emplacement du curseur, placez le curseur sur une ligne de code exécutable dans une fenêtre source. Dans le menu contextuel de l'éditeur, choisissez **Exécuter jusqu'au curseur**.  
  
 **Exécuter le code jusqu'à une fonction de la pile des appels**  
  
 Dans la fenêtre **Pile des appels**, sélectionnez la fonction, puis choisissez **Exécuter jusqu'au curseur** dans le menu contextuel. Pour afficher la trace de la pile des appels, consultez [Mapper les méthodes sur la pile des appels tout en déboguant](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
 **Exécuter le code jusqu'à une fonction spécifiée par nom**  
  
 Vous pouvez demander au débogueur d'exécuter une application jusqu'à une fonction spécifiée. Vous pouvez spécifier la fonction par nom ou la sélectionner dans la pile des appels.  
  
 Pour spécifier une fonction par nom, choisissez **Déboguer**, **Nouveau point d'arrêt**, **Interrompre à la fonction**, puis tapez le nom de la fonction et d'autres informations d'identification.  
  
 ![Boîte de dialogue Nouveau point d’arrêt](../debugger/media/dbg_execution_newbreakpoint.png "DBG\_Execution\_NewBreakpoint")  
  
 Si la fonction est surchargée ou si elle figure dans plusieurs espaces de noms, vous pouvez choisir les fonctions souhaitées dans la boîte de dialogue **Choisir les points d'arrêt**.  
  
 ![Boîte de dialogue Choisir les points d’arrêt](~/debugger/media/dbg_execution_overloadedbreakpoints.png "DBG\_Execution\_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Définir l'instruction suivante à exécuter  
 Après une interruption dans le débogueur, vous pouvez déplacer le point d'exécution pour désigner l'instruction suivante à exécuter. Dans la marge d'une fenêtre source ou Code Machine, une flèche jaune marque l'emplacement de la prochaine instruction à exécuter. Déplacer cette flèche permet d'ignorer une partie du code ou de revenir à une ligne déjà exécutée. Vous pouvez utiliser cette fonctionnalité, par exemple, pour ignorer une section de code qui contient un bogue connu.  
  
 ![Exemple2](~/debugger/media/dbg_basics_example2.png "DBG\_Basics\_Example2")  
  
 Pour définir l'instruction suivante à exécuter, appliquez l'une de ces procédures :  
  
-   Dans une fenêtre source, faites glisser la flèche jaune vers l'emplacement où vous souhaitez définir l'instruction suivante dans le même fichier source.  
  
-   Dans une fenêtre source, définissez le curseur sur la ligne que vous souhaitez exécuter ensuite et choisissez **Définir l'instruction suivante** dans le menu contextuel.  
  
-   Dans la fenêtre Code Machine, définissez le curseur sur l'instruction assembleur que vous souhaitez exécuter ensuite et choisissez **Définir l'instruction suivante** dans le menu contextuel.  
  
> [!CAUTION]
>  Le fait de définir l'instruction suivante fait en sorte que le compteur du programme accède directement au nouvel emplacement. Utilisez cette commande avec précaution :  
>   
>  -   Les instructions entre les nouveaux et les anciens points d'exécution ne sont pas exécutées.  
> -   Si vous déplacez le point d'exécution vers l'arrière, les instructions déjà traitées ne sont pas annulées.  
> -   Le déplacement de l'instruction suivante vers une autre fonction ou portée entraîne généralement une altération de la pile des appels, provoquant une erreur ou exception d'exécution. Si vous tentez de déplacer l'instruction suivante vers une autre portée, le débogueur ouvre une boîte de dialogue avec un avertissement et vous donne une occasion d'annuler l'opération. En Visual Basic, vous ne pouvez pas déplacer l'instruction suivante à une autre portée ou fonction.  
> -   En C\+\+ natif, si les contrôles d'exécution sont activés, la définition de l'instruction suivante peut provoquer la levée d'une exception lorsque l'exécution atteint la fin de la méthode.  
> -   Lorsque Modifier & Continuer est activé, la commande **Définir l'instruction suivante** échoue si vous avez apporté des modifications qui ne peuvent pas être remappées immédiatement par Modifier & Continuer. Par exemple, cela peut se produire si vous avez modifié le code contenu dans un bloc catch. Dans ce cas, un message d'erreur s'affiche pour indiquer que l'opération n'est pas prise en charge.  
  
> [!NOTE]
>  Dans du code managé, vous ne pouvez pas déplacer l'instruction suivante dans les conditions suivantes :  
>   
>  -   L'instruction suivante se trouve dans une méthode différente de celle de l'instruction actuelle.  
> -   Le débogage a été démarré à l'aide du débogage juste\-à\-temps.  
> -   Le déroulement d'une pile des appels est en cours.  
> -   Une exception System.StackOverflowException ou System.Threading.ThreadAbortException a été levée.  
  
 Il est impossible de définir l'instruction suivante lorsque l'application est active. Pour définir l'instruction suivante, le débogueur doit être en mode arrêt.  
  
##  <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a> Limiter le pas à pas à Uniquement mon code  
 Parfois, en cours de débogage, vous pouvez être amené à examiner uniquement le code que vous avez écrit et ignorer les autres éléments de code, par exemple les appels système. C'est précisément ce que permet de faire le mode de débogage Uniquement mon code. Uniquement mon code masque le code non\-utilisateur pour l'empêcher d'apparaître dans les fenêtres du débogueur. Lorsque vous parcourez le code, le débogueur parcourt le code de non\-utilisateur sans s'y arrêter. Voir [Uniquement mon code](../debugger/just-my-code.md)  
  
> [!NOTE]
>  Uniquement mon code n'est pas pris en charge pour les projets Smart Device.  
  
##  <a name="BKMK_Step_into_system_calls"></a> Effectuer un pas à pas détaillé dans des appels système  
 Si vous avez chargé des symboles de débogage pour le code système et que l'option Uniquement mon code n'est pas activée, vous pouvez effectuer un pas à pas détaillé dans un appel système tout comme s'il s'agissait de n'importe quel autre appel.  
  
 Pour accéder aux fichiers de symboles Microsoft, consultez la section [Utiliser des serveurs de symboles pour rechercher des fichiers de symboles qui ne sont pas sur votre ordinateur local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) dans la rubrique [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Pour charger des symboles pour un composant système spécifique lors du débogage :  
  
1.  Ouvrez la fenêtre Modules \(raccourci : **Ctrl\+Alt\+U**\).  
  
2.  Sélectionnez le module pour lequel vous souhaitez charger des symboles.  
  
     Consultez la colonne **État du symbole** pour connaître les modules qui possèdent des symboles chargés.  
  
3.  Choisissez **Charger les symboles** dans le menu contextuel.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Effectuer un pas à pas détaillé dans des propriétés et des opérateurs au sein du code managé  
 Par défaut, le débogueur effectue un pas à pas principal sur les propriétés et les opérateurs dans le code managé. Dans la plupart des cas, cela fournit une meilleure expérience de débogage. Pour activer le pas à pas détaillé des propriétés ou des opérateurs, choisissez **Déboguer**, **Options et paramètres**. Dans la page **Débogage**, **Général**, désactivez la case à cocher **Pas à pas principal dans les propriétés et les opérateurs \(Managé uniquement\)**.