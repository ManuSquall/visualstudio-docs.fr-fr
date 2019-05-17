---
title: Naviguer dans le Code avec le débogueur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430971"
---
# <a name="navigating-through-code-with-the-debugger"></a>Naviguer dans le code avec le débogueur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous familiariser avec les commandes et les raccourcis pour naviguer dans le code dans le débogueur, et qui rendra plus rapide et plus faciles à trouver et résoudre les problèmes dans votre application. Pendant que vous naviguez dans le code dans le débogueur, vous pouvez [Inspecter l’état de votre application](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) ou en savoir plus sur son flux d’exécution.  
  
## <a name="start-debugging"></a>Démarrer le débogage  
 Souvent, vous démarrez une session de débogage à l’aide **F5** (**déboguer** / **démarrer le débogage**). Cette commande démarre votre application avec le débogueur attaché.  
  
 La flèche verte démarre également le débogueur (même en tant que **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Incluent d’autres manières que vous pouvez démarrer l’application avec le débogueur attaché **F11** ([détaillé code](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([ignorer le code](#BKMK_Step_over_Step_out)), ou par à l’aide de **exécuter jusqu’au curseur**.  Consultez les autres sections de cette rubrique pour plus d’informations sur les opérations de ces options.  
  
 Lorsque vous déboguez, la ligne jaune vous montre le code qui sera exécutée ensuite.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Pendant le débogage, vous pouvez basculer entre les commandes telles que **F5**, **F11** et utiliser d’autres fonctionnalités décrites dans cette rubrique (par exemple, des points d’arrêt) afin d’obtenir rapidement le code que vous souhaitez examiner.  
  
 La plupart des fonctionnalités du débogueur, telles que l’affichage des valeurs des variables dans la fenêtre variables locales ou de l’évaluation des expressions dans la fenêtre Espion, sont disponibles uniquement lorsque le débogueur est suspendu (également appelé *mode arrêt*). Lorsque le débogueur est interrompu, état de votre application est interrompue lors de fonctions, variables, et les objets restent en mémoire. En mode arrêt, vous pouvez examiner leurs positions et états à la recherche de violations ou de bogues. Pour certains types de projets, vous pouvez également effectuer des ajustements à l’application en mode arrêt.  
  
## <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Étape dans du code ligne par ligne  
 Pour arrêter sur chaque ligne de code (chaque instruction) pendant le débogage, utilisez le **F11** raccourci clavier (ou **déboguer** / **pas à pas détaillé** dans le menu).  
  
> [!TIP]
> Quand vous exécutez chaque ligne de code, vous pouvez pointer sur les variables pour voir leurs valeurs, ou utiliser le [variables locales](../debugger/autos-and-locals-windows.md) et [espion](../debugger/autos-and-locals-windows.md) pour observer leurs valeurs à modifier.  
  
 Voici quelques détails sur le comportement de **pas à pas détaillé**:  
  
- Dans un appel à plusieurs fonctions imbriquées, **Pas à pas détaillé** va jusqu'à la fonction se trouvant au niveau le plus profond. Si vous utilisez **Pas à pas détaillé** dans un appel tel que `Func1(Func2())`, le débogueur parcourt la fonction `Func2`.  
  
- En fait, le débogueur parcourt les instructions de code plutôt que les lignes physiques. Par exemple, une clause `if` peut être écrite sur une ligne :  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   Lorsque vous parcourez cette ligne, le débogueur traite la condition comme une étape et la conséquence comme une autre (dans cet exemple, la condition est remplie).  
  
  Pour suivre visuellement la pile des appels lors de l’entrer dans les fonctions, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="BKMK_Step_over_Step_out"></a> Parcourir le code, en ignorant les fonctions  
 Lors de l’exécution de code dans le débogueur, souvent vous réalisez que vous n’avez pas besoin de voir ce qui se passe dans une fonction particulière (vous ne vous souciez il ou si vous savez qu’il fonctionne, comme le code de bibliothèque bien testé). Utilisez ces commandes pour ignorer le code (les fonctions s’exécutent toujours, bien sûr, mais le débogueur ignore dessus).  
  
|Commande de clavier|Commande de menu|Description|  
|----------------------|------------------|-----------------|  
|**F10**|**Pas à pas principal**|Si la ligne actuelle contient un appel de fonction, **pas à pas principal** exécute le code, puis suspend l’exécution à la première ligne de code après le retour de la fonction appelée.|  
|**Maj+F11**|**Pas à pas sortant**|**Pas à pas sortant** continue de s’exécuter de code et suspend l’exécution lorsque la fonction active est retournée (le débogueur ignore via la fonction active).|  
  
> [!TIP]
> Si vous devez rechercher le point d’entrée dans votre application, commencez par **F10** ou **F11**. Ces commandes sont souvent utiles lors de l’inspection de votre état de l’application ou tente de trouver plus d’informations sur son flux d’exécution.  
  
## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Exécuter à un emplacement spécifique ou d’une fonction  
 Fréquence à laquelle la méthode préférée de débogage du code, ces méthodes sont utiles lorsque vous savez exactement quel code que vous souhaitez inspecter ou au moins vous savez où vous souhaitez démarrer le débogage.  
  
- **Définir des points d'arrêt dans le code**  
  
     Pour définir un point d'arrêt simple dans votre code, ouvrez le fichier source dans l'éditeur Visual Studio. Définissez le curseur sur la ligne de code où vous souhaitez interrompre l’exécution, puis avec le bouton droit dans la fenêtre de code pour afficher le menu contextuel et choisissez **point d’arrêt / insérer un point d’arrêt** (ou appuyez sur **F9**). Le débogueur interrompt le droit de l’exécution avant l’exécution de la ligne.  
  
     ![Définissez un point d’arrêt](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Les points d'arrêt dans Visual Studio fournissent un ensemble enrichi de fonctionnalités supplémentaires, telles que les points d'arrêt et les points de trace conditionnels. Consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md).  
  
- **Exécuter le code jusqu'à l'emplacement du curseur**  
  
     Pour exécuter le code jusqu'à l'emplacement du curseur, placez le curseur sur une ligne de code exécutable dans une fenêtre source. Dans le menu contextuel de l’éditeur (clic droit dans l’éditeur), choisissez **exécuter jusqu’au curseur**. Cela équivaut à définir un point d’arrêt temporaire.  
  
- **S'arrêter manuellement dans le code**  
  
     Pour vous arrêter sur la ligne de code dans une application en cours d’exécution disponible suivante, choisissez **déboguer**, **interrompre tout** (clavier : **Ctrl+Alt+Break**).  
  
     Si vous arrêtez l’exécution de code sans les fichiers sources ou de symboles (.pdb) correspondants, le débogueur affiche une page **Fichiers sources introuvables** ou **Symboles introuvables** qui peut vous aider à trouver les fichiers appropriés. Consultez [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Si vous ne pouvez pas accéder aux fichiers de prise en charge, vous pouvez tout de même déboguer les instructions assembleur dans la fenêtre Code Machine.  
  
- **Exécuter le code jusqu'à une fonction de la pile des appels**  
  
     Dans le **pile des appels** fenêtre (disponible pendant le débogage), sélectionnez la fonction, avec le bouton droit et choisissez **exécuter jusqu’au curseur**. Pour suivre visuellement la pile des appels, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Exécuter le code jusqu'à une fonction spécifiée par nom**  
  
     Vous pouvez demander au débogueur d’exécuter votre application jusqu'à ce qu’il atteigne une fonction spécifiée. Vous pouvez spécifier la fonction par nom ou la sélectionner dans la pile des appels.  
  
     Pour spécifier une fonction par nom, choisissez **Déboguer**, **Nouveau point d'arrêt**, **Interrompre à la fonction**, puis tapez le nom de la fonction et d'autres informations d'identification.  
  
     ![Boîte de dialogue Nouveau point d’arrêt](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Si la fonction est surchargée ou si elle figure dans plusieurs espaces de noms, vous pouvez choisir les fonctions souhaitées dans la boîte de dialogue **Choisir les points d'arrêt** .  
  
     ![Choisir des points d’arrêt, boîte de dialogue](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="BKMK_Set_the_next_statement_to_execute"></a> Déplacez le pointeur pour modifier le flux d’exécution  
 Bien que le débogueur est suspendu, vous pouvez déplacer le pointeur d’instruction pour définir l’instruction suivante de code qui doit être exécuté. Dans la marge d'une fenêtre source ou Code Machine, une flèche jaune marque l'emplacement de la prochaine instruction à exécuter. Déplacer cette flèche permet d'ignorer une partie du code ou de revenir à une ligne déjà exécutée. Vous pouvez utiliser cette fonctionnalité, par exemple, pour ignorer une section de code qui contient un bogue connu.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Pour définir l'instruction suivante à exécuter, appliquez l'une de ces procédures :  
  
- Dans une fenêtre source, faites glisser la flèche jaune vers l'emplacement où vous souhaitez définir l'instruction suivante dans le même fichier source.  
  
- Dans une fenêtre source, définissez le curseur sur la ligne que vous souhaitez exécuter ensuite, avec le bouton droit et choisissez **définir l’instruction suivante**.  
  
- Dans la fenêtre code machine, définissez le curseur sur l’instruction assembleur que vous souhaitez exécuter ensuite, cliquez sur un et choisissez **définir l’instruction suivante**.  
  
> [!CAUTION]
> Le fait de définir l'instruction suivante fait en sorte que le compteur du programme accède directement au nouvel emplacement. Utilisez cette commande avec précaution :  
> 
> - Les instructions entre les nouveaux et les anciens points d'exécution ne sont pas exécutées.  
>   - Si vous déplacez le point d'exécution vers l'arrière, les instructions déjà traitées ne sont pas annulées.  
>   - Le déplacement de l'instruction suivante vers une autre fonction ou portée entraîne généralement une altération de la pile des appels, provoquant une erreur ou exception d'exécution. Si vous tentez de déplacer l'instruction suivante vers une autre portée, le débogueur ouvre une boîte de dialogue avec un avertissement et vous donne une occasion d'annuler l'opération. En Visual Basic, vous ne pouvez pas déplacer l'instruction suivante à une autre portée ou fonction.  
>   - En C++ natif, si les contrôles d'exécution sont activés, la définition de l'instruction suivante peut provoquer la levée d'une exception lorsque l'exécution atteint la fin de la méthode.  
>   - Lorsque Modifier & Continuer est activé, la commande **Définir l'instruction suivante** échoue si vous avez apporté des modifications qui ne peuvent pas être remappées immédiatement par Modifier &amp;amp; Continuer. Par exemple, cela peut se produire si vous avez modifié le code contenu dans un bloc catch. Dans ce cas, un message d'erreur s'affiche pour indiquer que l'opération n'est pas prise en charge.  
> 
> [!NOTE]
> Dans du code managé, vous ne pouvez pas déplacer l'instruction suivante dans les conditions suivantes :  
> 
> - L'instruction suivante se trouve dans une méthode différente de celle de l'instruction actuelle.  
>   - Le débogage a été démarré à l'aide du débogage juste-à-temps.  
>   - Le déroulement d'une pile des appels est en cours.  
>   - Une exception System.StackOverflowException ou System.Threading.ThreadAbortException a été levée.  
  
 Il est impossible de définir l'instruction suivante lorsque l'application est active. Pour définir l'instruction suivante, le débogueur doit être en mode arrêt.  
  
## <a name="step-into-non-user-code"></a>Pas à pas détaillé code non-utilisateur  
 Par défaut, le débogueur essaie d’afficher uniquement votre code d’application pendant le débogage, qui est déterminé par un débogueur paramètre *uniquement mon Code*. (Consultez [uniquement mon Code](../debugger/just-my-code.md) pour voir comment cela fonctionne pour les différents types de projets et langages et comment vous pouvez personnaliser le comportement.) Toutefois, parfois pendant le débogage, vous souhaiterez peut-être examiner du code du framework, le code de bibliothèque tierce ou les appels au système d’exploitation (appels système).  
  
 Vous pouvez désactiver uniquement mon Code en accédant à **outils** / **Options** / **débogage** et désactivez le **activer uniquement mon Code** case à cocher.  
  
 Lorsque uniquement mon Code est désactivé, le débogueur peut accéder dans le code de non-utilisateur et code non-utilisateur apparaît dans les fenêtres du débogueur.  
  
> [!NOTE]
> Uniquement mon code n'est pas pris en charge pour les projets Smart Device.  
  
 **Effectuer un pas à pas détaillé dans des appels système**  
  
 Si vous avez chargé des symboles de débogage pour le code système et uniquement mon Code n’est pas activé, vous pouvez effectuer dans un appel système tout comme n’importe quel autre appel.  
  
 Pour accéder aux fichiers de symboles Microsoft, consultez [utiliser des serveurs de symboles pour rechercher les fichiers de symboles non sur votre ordinateur local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) dans le [spécifier le symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) rubrique.  
  
 Pour charger des symboles pour un composant système spécifique lors du débogage :  
  
1. Ouvrez la fenêtre Modules (clavier : **Ctrl+Alt+U**).  
  
2. Sélectionnez le module pour lequel vous souhaitez charger des symboles.  
  
     Consultez la colonne **État du symbole** pour connaître les modules qui possèdent des symboles chargés.  
  
3. Choisissez **Charger les symboles** dans le menu contextuel.  
  
## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Effectuer un pas à pas détaillé dans des propriétés et des opérateurs au sein du code managé  
 Par défaut, le débogueur effectue un pas à pas principal sur les propriétés et les opérateurs dans le code managé. Dans la plupart des cas, cela fournit une meilleure expérience de débogage. Pour activer l’exécution pas à pas détaillé des propriétés ou des opérateurs, choisissez **déboguer** / **Options**. Dans la page **Débogage** / **Général** , désactivez la case à cocher **Pas à pas principal dans les propriétés et les opérateurs (Managé uniquement)** .
