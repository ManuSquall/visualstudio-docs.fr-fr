---
title: Parcourir le code avec le débogueur | Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66478505fe59ef65eb703fef6be8941deebe3d49
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931422"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Naviguer dans le code avec le débogueur Visual Studio

Le débogueur Visual Studio peut vous aider à naviguer dans le code pour inspecter l’état d’une application et afficher ses flux d’exécution. Vous pouvez utiliser des raccourcis clavier, les commandes de débogage, les points d’arrêt et les autres fonctionnalités pour accéder rapidement au code que vous souhaitez examiner. Vous êtes familiarisé avec les commandes de navigation du débogueur et raccourcis accélère et plus faciles à trouver et résoudre les problèmes de l’application.  S’il s’agit de la première fois que vous avez essayé de déboguer du code, il pouvez que vous souhaitez lire [corriger les bogues en écrivant mieux C# code](../debugger/write-better-code-with-visual-studio.md) et [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.
  
## <a name="basic-debugging"></a>Bases du débogage  

Pour démarrer votre application avec le débogueur attaché, appuyez sur **F5**, sélectionnez **déboguer** > **démarrer le débogage**, ou sélectionnez la flèche verte dans la barre d’outils de Visual Studio.  
  
 ![DBG&#95;notions de base&#95;Démarrer&#95;débogage](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
Pendant que vous déboguez, une mise en surbrillance jaune indique la ligne de code qui s’exécute suivant.  
  
 ![DBG&#95;notions de base&#95;rompre&#95;Mode](../debugger/media/dbg_basics_break_mode.png "mode arrêt")  
  
Plus fenêtres du débogueur, comme le **Modules** et **espion** windows, sont disponibles uniquement lorsque le débogueur est en cours d’exécution. Certaines fonctionnalités de débogueur, telles que l’affichage des valeurs des variables dans le **variables locales** fenêtre ou l’évaluation des expressions dans le **espion** fenêtre, sont disponibles uniquement lorsque le débogueur est suspendu à un point d’arrêt, également appelé *mode arrêt*. 

En mode arrêt, exécution de l’application est interrompue lors de fonctions, variables, et les objets restent en mémoire. Vous pouvez examiner leurs positions et états à la recherche de violations ou de bogues. Pour certains types de projets, vous pouvez également effectuer des ajustements à l’application en mode arrêt. Pour une vidéo montrant ces fonctionnalités, consultez [mise en route avec le débogueur](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Si vous interrompez dans le code n’ayant pas source ou au symbole (*.pdb*) les fichiers chargés, le débogueur affiche un **fichiers sources introuvables** ou **symboles introuvables** page qui peut vous aider à Rechercher et charger les fichiers. Consultez [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Si vous ne pouvez pas charger les fichiers sources ou de symboles, vous pouvez toujours déboguer les instructions d’assembly dans le **désassemblage** fenêtre. 

Vous n’êtes pas obligé toujours démarrer le débogage en démarrant une application au début. Vous pouvez également appuyer sur **F11** à [détaillé code](#BKMK_Step_into__over__or_out_of_the_code), appuyez sur **F10** à [ignorer le code](#BKMK_Step_over_Step_out), ou [exécuter jusqu'à un emplacement spécifique ou fonction](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).    

##  <a name="step-through-code"></a>Exécuter le code pas à pas

Les commandes d’étape de débogueur vous aider à inspecter l’état de votre application ou en savoir plus sur son flux d’exécution. 

Si vous devez rechercher le point d’entrée dans votre application, commencez par **F10** ou **F11**.  

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Parcourez le code ligne par ligne  

Pour arrêter sur chaque ligne de code ou instruction pendant le débogage, utilisez **déboguer** > **pas à pas détaillé**, ou appuyez sur **F11**.  

Le débogueur exécute les instructions de code, les lignes non physiques. Par exemple, une clause `if` peut être écrite sur une ligne :  
  
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

Toutefois, lorsque vous parcourez cette ligne, le débogueur traite la condition comme une étape et la conséquence qu’une autre. Dans l’exemple précédent, la condition est true.  
  
Dans un appel à plusieurs fonctions imbriquées, **Pas à pas détaillé** va jusqu'à la fonction se trouvant au niveau le plus profond. Par exemple, si vous utilisez **pas à pas détaillé** dans un appel tel que `Func1(Func2())`, le débogueur parcourt la fonction `Func2`.  

>[!TIP]
>Quand vous exécutez chaque ligne de code, vous pouvez pointer sur les variables pour voir leurs valeurs, ou utiliser le [variables locales](autos-and-locals-windows.md) et [espion](watch-and-quickwatch-windows.md) pour observer les valeurs à modifier. Vous pouvez également suivre la pile des appels lors de l’entrer dans les fonctions. Consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md). 

###  <a name="BKMK_Step_over_Step_out"></a> Parcourir le code et d’ignorer certaines fonctions  

Vous pouvez s’intéressent pas à une fonction pendant le débogage, ou vous savez qu’il fonctionne, comme le code de bibliothèque bien testée. Vous pouvez utiliser les commandes suivantes pour ignorer le code. Les fonctions exécutent toujours, mais le débogueur ignore au-dessus d’eux.  
  
|Commande de clavier|Commande du menu Déboguer|Description|  
|----------------------|------------------|-----------------|  
|**F10**|**Pas à pas principal**|Si la ligne actuelle contient un appel de fonction, **pas à pas principal** exécute le code, puis suspend l’exécution à la première ligne de code après le retour de la fonction appelée.|  
|**Maj**+**F11**|**Pas à pas sortant**|**Pas à pas sortant** continue de s’exécuter de code et suspend l’exécution lorsque la fonction active est retournée. Le débogueur ignore via la fonction active.|  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Exécuter à un emplacement spécifique ou d’une fonction  

Vous pouvez exécuter directement à un emplacement spécifique ou la fonction lorsque vous savez exactement quel code que vous souhaitez inspecter ou que vous savez où vous souhaitez démarrer le débogage.  
  
### <a name="run-to-a-breakpoint-in-code"></a>Exécuter un point d’arrêt dans le code  
  
Pour définir un point d’arrêt simple dans votre code, cliquez sur la marge gauche en regard de la ligne de code où vous souhaitez interrompre l’exécution. Vous pouvez également sélectionner la ligne et appuyez sur **F9**, sélectionnez **déboguer** > **point d’arrêt**, ou avec le bouton droit et sélectionnez **point d’arrêt**  >  **Insérer le point d’arrêt**. Le point d’arrêt apparaît sous la forme d’un point rouge dans la marge gauche en regard de la ligne de code. Le débogueur interrompt l’exécution juste avant la ligne s’exécute.
  
![Définir un point d’arrêt](../debugger/media/dbg_basics_setbreakpoint.png "Définir un point d’arrêt")  
  
Les points d'arrêt dans Visual Studio fournissent un ensemble enrichi de fonctionnalités supplémentaires, telles que les points d'arrêt et les points de trace conditionnels. Pour plus d’informations, consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md).  
  
### <a name="run-to-a-function-breakpoint"></a>Exécuter un point d’arrêt (fonction)  

Vous pouvez indiquer au débogueur d’exécuter jusqu'à ce qu’il atteigne une fonction spécifiée. Vous pouvez spécifier la fonction par nom ou la sélectionner dans la pile des appels.  
  
**Pour spécifier un point d’arrêt de la fonction par nom**

1. Sélectionnez **déboguer** > **nouveau point d’arrêt** > **fonction de point d’arrêt**
   
1. Dans le **nouveau point d’arrêt de la fonction** boîte de dialogue, tapez le nom de la fonction et sélectionnez son langage.
   
   ![Boîte de dialogue Nouveau point d’arrêt de la fonction](../debugger/media/dbg_execution_newbreakpoint.png "nouveau point d’arrêt (fonction)")  
   
1. Sélectionnez **OK**. 

Si la fonction est surchargée ou dans plus d’un espace de noms, vous pouvez choisir celle qui vous intéresse dans la **des points d’arrêt** fenêtre.  

![Surchargé de points d’arrêt de la fonction](../debugger/media/dbg_execution_overloadedbreakpoints.png "surchargé de points d’arrêt (fonction)")  
  
**Pour sélectionner un point d’arrêt de la fonction à partir de la pile des appels** 
  
1. Pendant le débogage, ouvrez le **pile des appels** en sélectionnant **déboguer** > **Windows** > **pile des appels**. 
   
1. Dans le **pile des appels** fenêtre, cliquez sur une fonction et sélectionnez **exécuter jusqu’au curseur**, ou appuyez sur **Ctrl**+**F10**.  

Pour suivre visuellement la pile des appels, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="run-to-a-cursor-location"></a>Exécuter à un emplacement du curseur  

Pour exécuter à l’emplacement du curseur, dans le code source ou la **pile des appels** fenêtre, sélectionnez la ligne que vous souhaitez interrompre à, avec le bouton droit et sélectionnez **exécuter jusqu’au curseur**, ou appuyez sur **Ctrl** + **F10**. En sélectionnant **exécuter jusqu’au curseur** revient à définir un point d’arrêt temporaire.

### <a name="run-to-click"></a>Exécuter jusqu’au clic 

Pendant la suspension dans le débogueur, vous pouvez pointer sur une instruction dans le code source ou la **désassemblage** , puis sélectionnez le **exécuter l’exécution jusqu’ici** icône de flèche verte. À l’aide de **exécuter jusqu’au clic** élimine la nécessité de définir un point d’arrêt temporaire.

![Exécuter jusqu’au clic](../debugger/media/dbg-run-to-click.png "Exécuter jusqu’au clic") 

> [!NOTE]
> **Exécuter jusqu’au clic** est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].
  
### <a name="manually-break-into-code"></a>S'arrêter manuellement dans le code  
  
Pour vous arrêter dans la ligne de code dans une application en cours d’exécution disponible suivante, sélectionnez **déboguer** > **interrompre tout**, ou appuyez sur **Ctrl**+**Alt**  + **Rompre**. 
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Déplacez le pointeur pour modifier le flux d’exécution  

Bien que le débogueur est suspendu, une flèche jaune dans la marge du code source ou **désassemblage** fenêtre marque l’emplacement de la prochaine instruction à exécuter. Vous pouvez modifier l’instruction suivante à exécuter déplacer cette flèche. Vous pouvez ignorer une partie du code, ou revenir à une ligne précédente. Déplacer le pointeur est utile dans les situations telles que d’ignorer une section de code qui contient un bogue connu.  

 ![Déplacez le pointeur](../debugger/media/dbg_basics_example3.gif "déplacer le pointeur")
  
Pour modifier l’instruction suivante à exécuter, le débogueur doit être en mode arrêt. Dans le code source ou **désassemblage** fenêtre, faites glisser la flèche jaune à une autre ligne, ou cliquez sur la ligne que vous souhaitez exécuter ensuite et sélectionnez **définir l’instruction suivante**. 

Le compteur de programme accède directement au nouvel emplacement, les instructions entre l’exécution d’ancienne et nouvelle points ne sont pas exécutées. Toutefois, si vous déplacez le point d’exécution vers l’arrière, les instructions déjà traitées ne sont pas annulées.  

>[!CAUTION]
>- Le déplacement de l'instruction suivante vers une autre fonction ou portée entraîne généralement une altération de la pile des appels, provoquant une erreur ou exception d'exécution. Si vous tentez de déplacer l'instruction suivante vers une autre portée, le débogueur ouvre une boîte de dialogue avec un avertissement et vous donne une occasion d'annuler l'opération. 
>- En Visual Basic, vous ne pouvez pas déplacer l'instruction suivante à une autre portée ou fonction.  
>- En C++ natif, si les contrôles d'exécution sont activés, la définition de l'instruction suivante peut provoquer la levée d'une exception lorsque l'exécution atteint la fin de la méthode.  
>- Lorsque Modifier & Continuer est activé, la commande **Définir l'instruction suivante** échoue si vous avez apporté des modifications qui ne peuvent pas être remappées immédiatement par Modifier &amp;amp; Continuer. Par exemple, cela peut se produire si vous avez modifié le code contenu dans un bloc catch. Dans ce cas, un message d’erreur vous indique que l’opération n’est pas pris en charge.  
>- Dans le code managé, vous ne pouvez pas déplacer l’instruction suivante si :  
>   - L'instruction suivante se trouve dans une méthode différente de celle de l'instruction actuelle.  
>   - Le débogage a été démarré par juste-à-temps de débogage.  
>   - Un déroulement de pile d’appel est en cours.  
>   - Une exception System.StackOverflowException ou System.Threading.ThreadAbortException a été levée.  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Déboguer le code de non-utilisateur  

Par défaut, le débogueur essaie de déboguer uniquement le code de votre application en activant un paramètre appelé *uniquement mon Code*. Pour plus d’informations sur le fonctionne de cette fonctionnalité pour différents types de projets et langages, et comment vous pouvez la personnaliser, consultez [uniquement mon Code](../debugger/just-my-code.md). 

Pour examiner le code du framework, le code de bibliothèque tierce ou les appels système pendant le débogage, vous pouvez désactiver uniquement mon Code. Dans **outils** (ou **déboguer**) > **Options** > **débogage**, désactivez le **activer uniquement mon Code** case à cocher. Lorsque uniquement mon Code est désactivé, code de non-utilisateur s’affiche dans les fenêtres du débogueur et le débogueur peut accéder dans le code non-utilisateur.  

> [!NOTE]
> Uniquement mon code n'est pas pris en charge pour les projets Smart Device.  
  
### <a name="debug-system-code"></a>Déboguer le code système

Si vous avez chargé des symboles de débogage pour le code de système de Microsoft et désactivée uniquement mon Code, vous pouvez effectuer dans un appel système tout comme n’importe quel autre appel.  
  
Pour charger des symboles de Microsoft, consultez [configurer des emplacements de symboles et options de chargement](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).  
  
**Pour charger des symboles pour un composant système spécifique :**

1. Pendant que vous déboguez, ouvrez le **Modules** en sélectionnant **déboguer** > **Windows** > **Modules**, ou en appuyant sur **Ctrl**+**Alt**+**U**.  
  
1. Dans le **Modules** fenêtre, vous pouvez indiquer à qui les modules ont des symboles chargés dans le **état du symbole** colonne. Cliquez sur le module que vous souhaitez charger des symboles pour, puis sélectionnez **charger les symboles**.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Effectuer un pas à pas détaillé dans des propriétés et des opérateurs au sein du code managé  
 Par défaut, le débogueur effectue un pas à pas principal sur les propriétés et les opérateurs dans le code managé. Dans la plupart des cas, cela fournit une meilleure expérience de débogage. Pour activer l’exécution pas à pas détaillé des propriétés ou des opérateurs, choisissez **déboguer** > **Options**. Dans la page **Débogage** > **Général**, désactivez la case à cocher **Pas à pas principal dans les propriétés et les opérateurs (Managé uniquement)**.

## <a name="see-also"></a>Voir aussi
 [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)  
 [Corriger les bogues en écrivant un meilleur code C#](../debugger/write-better-code-with-visual-studio.md)  
 [Premier aperçu de débogage](../debugger/debugger-feature-tour.md) 
