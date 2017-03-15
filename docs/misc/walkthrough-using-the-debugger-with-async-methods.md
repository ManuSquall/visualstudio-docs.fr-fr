---
title: "Proc&#233;dure pas &#224; pas&#160;: utilisation du d&#233;bogueur avec les m&#233;thodes Async | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "fonction asynchrone, utiliser le débogueur"
  - "await (opérateur), utiliser le débogueur"
  - "Pas à pas détaillé (commande), at await (opérateur)"
  - "Pas à pas sortant (commande), within async (méthode)"
  - "Pas à pas principal (commande), at await (opérateur)"
ms.assetid: 5adb2531-3f09-4b7e-8baa-29de80abee6e
caps.latest.revision: 23
caps.handback.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# Proc&#233;dure pas &#224; pas&#160;: utilisation du d&#233;bogueur avec les m&#233;thodes Async
La fonctionnalité Async vous permet d'appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre plusieurs méthodes ou expressions lambda.  Pour rendre le code synchrone asynchrone, appelez une méthode asynchrone au lieu d'une méthode synchrone et ajoutez quelques mots clés au code.  Pour plus d'informations, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Dans le débogueur Visual Studio, vous pouvez utiliser les commandes **Pas à pas détaillé**, **Pas à pas principal** et **Pas à pas sortant** avec la fonctionnalité `Async`.  Vous pouvez également continuer à utiliser des points d'arrêt, en particulier pour visualiser le flux de contrôle à une instruction contenant un opérateur await.  Dans cette procédure, vous effectuerez les tâches suivantes, que vous pouvez exécuter dans n'importe quel ordre.  
  
-   Montrer le flux de contrôle à une instruction await en utilisant des points d'arrêt.  
  
-   Comprendre le comportement des commandes **Pas à pas détaillé** et **Pas à pas principal** aux instructions qui contiennent un opérateur await.  
  
-   Comprendre le comportement de la commande **Pas à pas sortant** utilisé d'une méthode async.  
  
## Points d'arrêt permettant d'afficher le flux de contrôle  
 Si vous marquez une méthode avec le modificateur [Async](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) ou [async](/dotnet/csharp/language-reference/keywords/async) \(C\#\), vous pouvez utiliser l'opérateur [Await](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) ou [await](/dotnet/csharp/language-reference/keywords/await) \(C\#\) dans la méthode.  Pour créer une expression await, associez l'opérateur await à une tâche.  Lorsqu'une expression await est appelée pour la tâche, la méthode actuelle est immédiatement abandonnée et une autre tâche est retournée.  Lorsque la tâche associée à l'opérateur await est terminée, l'exécution se poursuit dans la même méthode.  Pour plus d'informations, consultez [Flux de contrôle dans les programmes Async](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
> [!NOTE]
>  Une méthode async retourne à l'appelant en cas de rencontre du premier objet await qui n'est pas encore terminé ou en cas d'atteinte de la fin de la méthode async, selon la première éventualité.  
  
> [!NOTE]
>  Les applications console dans ces exemples utilisent la méthode <xref:System.Threading.Tasks.Task.Wait%2A> pour empêcher l'application de se terminer dans `Main`.  Vous ne devez pas utiliser la méthode <xref:System.Threading.Tasks.Task.Wait%2A> en dehors des applications console car un interblocage peut se produire.  
  
 La procédure suivante définit des points d'arrêt pour illustrer ce qui se produit lorsque l'application atteint une instruction await.  Vous pouvez également montrer le flux de contrôle en ajoutant des instructions `Debug.WriteLine`.  
  
1.  Créez une application console et collez\-y le code suivant :  
  
     [!code-cs[csAsyncDebugging#1](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_1.cs)]
     [!code-vb[csAsyncDebugging#1](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_1.vb)]  
  
2.  Définissez des points d'arrêt de débogage sur les trois lignes qui se terminent par un commentaire « set breakpoint » \(définir un point d'arrêt\).  
  
3.  Sélectionnez la touche F5 ou **Déboguer**, **Démarrer le débogage** dans la barre de menus pour exécuter l'application.  
  
     L'application passe à la méthode `ProcessAsync` et s'arrête sur la ligne qui contient l'opérateur await.  
  
4.  Sélectionnez à nouveau la touche F5.  
  
     Parce que l'application s'est arrêtée sur une instruction qui contient un opérateur await, l'application quitte immédiatement la méthode async et retourne une tâche.  Par conséquent, l'application quitte la méthode `ProcessAsync` et s'arrête au point d'arrêt dans la méthode d'appel \(`Main`\).  
  
5.  Sélectionnez à nouveau la touche F5.  
  
     Lorsque la méthode `DoSomethingAsync` est terminée, le code reprend après l'instruction await dans la méthode d'appel.  Par conséquent, l'application s'arrête au point d'arrêt dans la méthode `ProcessAsync`.  
  
     Lorsque `DoSomethingAsync` a initialement fait l'objet d'une instruction await, la méthode `ProcessAsync` s'est arrêtée et a retourné une tâche.  Lorsque la méthode `DoSomethingAsync` ayant fait l'objet d'une instruction await est terminée, l'évaluation de l'instruction await a généré la valeur de retour `DoSomethingAsync`.  La méthode `DoSomethingAsync` est définie pour retourner `Task (Of Integer)` en Visual Basic ou `Task<int>` en C\#, donc la valeur dans son instruction Return est un entier.  Pour plus d'informations, consultez [Types de retour Async](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Obtention puis attente d'une tâche  
 Dans la méthode `ProcessAsync`, l'instruction `Dim result = Await DoSomethingAsync()` \(Visual Basic\) ou `var result = await DoSomethingAsync();` \(C\#\) est une contraction des deux instructions suivantes :  
  
 [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
 [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
 La première ligne de code appelle la méthode async et retourne une tâche.  Cette tâche est associée à l'opérateur await dans la ligne de code suivante.  L'instruction await quitte la méthode \(`ProcessAsync`\) et retourne une autre tâche.  Lorsque la tâche associée à l'opérateur await est terminée, le code reprend dans la méthode \(`ProcessAsync`\) après l'instruction await.  
  
 Lorsque l'instruction await retourne immédiatement une autre tâche, cette tâche est l'argument retourné par la méthode async qui contient l'opérateur await \(`ProcessAsync`\).  La tâche retournée par l'instruction await inclut l'exécution de code qui se produit après l'instruction await dans la même méthode, c'est pourquoi cette tâche est différente de la tâche associée à await.  
  
## Pas à pas détaillé et Pas à pas principal  
 La commande **Pas à pas détaillé** détaille une méthode, mais la commande **Pas à pas principal** exécute l'appel de méthode, puis s'arrête sur la ligne suivante de la méthode d'appel.  Pour plus d'informations, consultez [Effectuer un pas à pas détaillé, principal ou sortant](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Step_into__over__or_out_of_the_code).  
  
 La procédure suivante montre ce qui se passe lorsque vous sélectionnez les commandes **Pas à pas détaillé** ou **Pas à pas principal** sur une instruction await.  
  
1.  Remplacez le code dans l'application console par le code suivant.  
  
     [!code-cs[csAsyncDebugging#3](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_3.cs)]
     [!code-vb[csAsyncDebugging#3](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_3.vb)]  
  
2.  Sélectionnez la touche F11 ou choisissez **Déboguer**, **Pas à pas détaillé** dans la barre de menus pour démarrer une démonstration de la commande `Step Into` sur une instruction contenant un opérateur await.  
  
     L'application démarre et s'arrête sur la première ligne, qui est `Sub Main()` en Visual Basic ou l'accolade ouvrante de la méthode `Main` en C\#.  
  
3.  Choisissez la touche F11 encore trois fois.  
  
     L'application doit maintenant avoir atteint l'instruction await dans la méthode `ProcessAsync`.  
  
4.  Appuyez sur la touche F11.  
  
     L'application passe à la méthode `DoSomethingAsync` et s'arrête sur la première ligne.  Ce comportement se produit même si, à l'instruction `await`, l'application retourne immédiatement à la méthode appelante \(`Main`\).  
  
5.  Continuez à appuyer sur la touche F11 jusqu'à ce l'application revienne à l'instruction await dans la méthode `ProcessAsync`.  
  
6.  Appuyez sur la touche F11.  
  
     L'application s'arrête sur la ligne qui suit l'instruction await.  
  
7.  Dans la barre de menus, sélectionnez **Déboguer**, **Arrêter le débogage** pour arrêter l'exécution de l'application.  
  
     Les étapes suivantes montrent la commande **Pas à pas principal** à une instruction await.  
  
8.  Sélectionnez la touche F11 quatre fois, ou choisissez **Déboguer**, **Pas à pas détaillé** quatre fois dans la barre de menus.  
  
     L'application doit maintenant avoir atteint l'instruction await dans la méthode `ProcessAsync`.  
  
9. Choisissez la touche F10 ou **Déboguer**, **Pas à pas principal** dans la barre de menus.  
  
     L'exécution s'arrête à la ligne qui suit l'instruction await.  Ce comportement se produit même si l'application retourne immédiatement à la méthode appelante \(`Main`\) à l'instruction await.  La commande `Step Over` effectue également un pas à pas principal dans l'exécution de la méthode `DoSomethingAsync`, comme prévu.  
  
10. Dans la barre de menus, sélectionnez **Déboguer**, **Arrêter le débogage** pour arrêter l'exécution de l'application.  
  
     Au fil de la procédure, le comportement des commandes **Pas à pas détaillé** et **Pas à pas principal** diffère légèrement lorsque l'opérateur await se trouve sur une autre ligne entre l'appel et la méthode async.  
  
11. Dans la méthode `ProcessAsync`, remplacez l'instruction await par le code suivant :  L'instruction await d'origine est une contraction des deux instructions suivantes.  
  
     [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
     [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
12. Sélectionnez la touche F11 ou choisissez **Déboguer**, **Pas à pas détaillé** dans la barre de menus plusieurs fois pour commencer l'exécution et pour parcourir le code.  
  
     À l'appel de `DoSomethingAsync`, la commande **Pas à pas détaillé** s'arrête à la méthode `DoSomethingAsync`, alors que la commande **Pas à pas principal** accède à l'instruction suivante, comme prévu.  À l'instruction await, les deux commandes s'arrêtent à l'instruction qui suit await.  
  
## Pas à pas sortant  
 Dans les méthodes qui ne sont pas async, la commande **Pas à pas sortant** s'arrête dans la méthode d'appel sur le code qui suit l'appel de méthode.  Pour les méthodes async, la logique d'arrêt de l'exécution dans la méthode appelante est plus complexe, et cette logique varie selon que la commande **Pas à pas sortant** se trouve sur la première ligne de la méthode async ou non.  
  
1.  Remplacez le code dans l'application console par le code suivant.  
  
     [!code-cs[csAsyncDebugging#4](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_4.cs)]
     [!code-vb[csAsyncDebugging#4](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_4.vb)]  
  
2.  Définissez un point d'arrêt sur la ligne `Debug.WriteLine("before")` de la méthode `DoSomethingAsync`.  
  
     Ceci afin d'illustrer le comportement de la commande **Pas à pas sortant** d'une ligne dans une méthode async qui n'est pas la première ligne.  
  
3.  Sélectionnez la touche F5 ou **Déboguer**, **Démarrer le débogage** dans la barre de menus pour démarrer l'application.  
  
     Le code s'arrête sur `Debug.WriteLine("before")` dans la méthode `DoSomethingAsync`.  
  
4.  Choisissez les touches Maj\+F11, ou **Déboguer**, **Pas à pas sortant** dans la barre de menus.  
  
     L'application s'arrête dans la méthode appelante à l'instruction await de la tâche qui est associée à la méthode actuelle.  Par conséquent, l'application s'arrête sur l'instruction await dans la méthode `ProcessAsync`.  L'application ne s'arrête pas sur `Dim z = 0` \(Visual Basic\) ou `int z = 0;` \(C\#\), qui est le code qui suit l'appel à la méthode `DoSomethingAsync`.  
  
5.  Choisissez **Déboguer**, **Arrêter le débogage** dans la barre de menus pour arrêter l'exécution de l'application.  
  
     Les étapes suivantes illustrent ce qui se produit lorsque vous effectuez un **pas à pas sortant** dès la première ligne d'une méthode async.  
  
6.  Supprimez le point d'arrêt existant et ajoutez un point d'arrêt sur la première ligne de la méthode `DoSomethingAsync`.  
  
     En C\#, ajoutez le point d'arrêt sur l'accolade ouvrante de la méthode `DoSomethingAsync`.  En Visual Basic, ajoutez un point d'arrêt sur la ligne qui contient `Async Function DoSomethingAsync() As Task(Of Integer)`.  
  
7.  Appuyez sur la touche F5 pour démarrer l'application.  
  
     Le code s'arrête sur la première ligne de la méthode `DoSomethingAsync`.  
  
8.  Dans la barre de menus, sélectionnez **Déboguer**, **Fenêtres**, **Sortie**.  
  
     La fenêtre **Sortie** s'ouvre.  
  
9. Choisissez les touches Maj\+F11, ou **Déboguer**, **Pas à pas sortant** dans la barre de menus.  
  
     L'application reprend jusqu'à ce que la méthode async atteigne sa première instruction await, puis l'application s'arrête à l'instruction appelante.  Par conséquent, l'application s'arrête sur `Dim the Task = DoSomethingAsync()` \(Visual Basic\) ou `var theTask = DoSomethingAsync();` \(C\#\).  Le message « before » \(avant\) s'affiche dans la fenêtre Sortie, mais le message « after » \(après\) ne s'est pas encore affiché.  
  
10. Sélectionnez la touche F5 pour continuer à exécuter l'application.  
  
     L'application continue avec l'instruction qui suit l'instruction await dans la fonction async appelée \(`DoSomethingAsync`\).  Le message « after » \(après\) apparaît dans la fenêtre Sortie.  
  
## Voir aussi  
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)