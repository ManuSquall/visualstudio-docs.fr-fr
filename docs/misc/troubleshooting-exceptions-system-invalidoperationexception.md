---
title: "D&#233;pannage des exceptions&#160;: System.InvalidOperationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidOperationException (classe)"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.InvalidOperationException
Une exception <xref:System.InvalidOperationException?displayProperty=fullName> est levée si une méthode d'un objet est appelée quand l'état de l'objet ne peut pas prendre en charge l'appel de méthode. L'exception est également levée quand une méthode tente de manipuler l'interface utilisateur à partir d'un autre thread que le thread principal ou le thread d'interface utilisateur.  
  
> [!IMPORTANT]
>  Dans la mesure où des exceptions <xref:System.InvalidOperationException> peuvent être levées dans un grand nombre de situations différentes, il est important de lire et de comprendre le <xref:System.Exception.Message%2A> affiché dans l'Assistant Exception.  
  
##  <a name="BKMK_In_this_article"></a> Dans cet article  
 [Une méthode qui s'exécute sur un autre thread qu'un thread d'interface utilisateur met à jour l'interface utilisateur](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [Une instruction d'un bloc foreach (For Each en Visual Basic) change la collection dans laquelle elle itère](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [Un Nullable&lt;T&gt; qui a la valeur Null fait l'objet d'un transtypage en T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [Une méthode System.Linq.Enumerable est appelée sur une collection vide](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [Articles connexes](#BKMK_Related_articles)  
  
 Les exemples de code de cet article vous montrent comment certaines exceptions <xref:System.InvalidOperationException> communes peuvent se produire dans votre application. La façon dont vous gérez ces problèmes dépend de chaque situation. Si l’exception est irrécupérable quant au fonctionnement de votre application, il peut être souhaitable d’utiliser une construction [try... catch](/dotnet/csharp/language-reference/keywords/exception-handling-statements) \([Try... Catch](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) en Visual Basic\) pour capturer l’exception et nettoyer l’état de l’application avant de quitter. Toutefois, d'autres exceptions <xref:System.InvalidOperationException> peuvent être anticipées et évitées. Les exemples de méthode modifiée illustrent certaines de ces techniques.  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> Une méthode qui s'exécute sur un autre thread qu'un thread d'interface utilisateur met à jour l'interface utilisateur  
 [Levée d'une exception InvalidOperationException avec une mise à jour de l'interface utilisateur à partir d'un autre thread qu'un thread d'interface utilisateur](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [Éviter les exceptions InvalidOperationException sur les autres threads que les threads d'interface utilisateur](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 La plupart des infrastructures d'application d'interface graphique utilisateur .NET, par exemple Windows Forms et Windows Presentation Foundation \(WPF\), vous permettent d'accéder aux objets d'interface graphique utilisateur uniquement à partir du thread qui crée et gère l'interface utilisateur \(le thread **principal** ou le thread d'**interface utilisateur**\). Une exception <xref:System.InvalidOperationException> est levée quand vous essayez d'accéder à un élément d'interface utilisateur à partir d'un thread qui n'est pas le thread d'interface utilisateur.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> Levée d'une exception InvalidOperationException avec une mise à jour de l'interface utilisateur à partir d'un autre thread qu'un thread d'interface utilisateur  
  
> [!NOTE]
>  Les exemples suivants utilisent le [Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md) pour créer d’autres threads que des threads d’interface utilisateur. Toutefois, ces exemples sont également pertinents pour tous les [Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md) .NET.  
  
 Dans ces exemples, le gestionnaire d'événements `ThreadsExampleBtn_Click` appelle deux fois la méthode `DoSomeWork`. Le premier appel à la méthode \(`DoSomeWork(20);`\) s'exécute de manière synchrone et réussit. Mais le deuxième appel \(`Task.Run( () => { DoSomeWork(1000);});`\) s’exécute sur un thread du [pool de threads](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx) de l’application. Dans la mesure où cet appel tente de mettre à jour l'interface utilisateur à partir d'un autre thread qu'un thread d'interface utilisateur, l'instruction lève une exception <xref:System.InvalidOperationException>.  
  
 **Applications WPF et applications de Store**  
  
> [!NOTE]
>  Dans les applications téléphoniques de Store, une exception <xref:System.Exception> est levée à la place de l'exception plus spécifique <xref:System.InvalidOperationException>.  
  
 **Messages d'exception :**  
  
|||  
|-|-|  
|Applications WPF|Informations supplémentaires : le thread appelant ne peut pas accéder à cet objet parce qu'un autre thread en est propriétaire.|  
|Applications de Store|Informations supplémentaires : l'application a appelé une interface qui était maintenue en ordre pour un thread différent. \(Exception de HRESULT : 0x8001010E \(RPC\_E\_WRONG\_THREAD\)\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Applications Windows Forms**  
  
 **Message d'exception :**  
  
-   Informations supplémentaires : opération inter\-threads non valide : le contrôle 'TextBox1' a fait l'objet d'un accès à partir d'un thread autre que celui sur lequel il a été créé.  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Une méthode qui s'exécute sur un autre thread qu'un thread d'interface utilisateur met à jour l'interface utilisateur](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> Éviter les exceptions InvalidOperationException sur les autres threads que les threads d'interface utilisateur  
 Les infrastructures d'interface utilisateur Windows implémentent un modèle de *répartiteur* qui inclut une méthode permettant de vérifier si l'appel d'un membre d'élément d'interface utilisateur est en cours d'exécution sur le thread d'interface utilisateur, ainsi que d'autres méthodes permettant de planifier l'appel sur le thread d'interface utilisateur.  
  
 **Applications WPF**  
  
 Dans les applications WPF, utilisez l'une des méthodes <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> pour exécuter un délégué sur le thread d'interface utilisateur. Si nécessaire, utilisez la méthode <xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName> pour déterminer si une méthode est en cours d'exécution sur un autre thread qu'un thread d'interface utilisateur.  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Applications Windows Forms**  
  
 Dans les applications Windows Forms, utilisez la méthode <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> pour exécuter un délégué qui met à jour le thread d'interface utilisateur. Si nécessaire, utilisez la propriété <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> pour déterminer si une méthode est en cours d'exécution sur un autre thread qu'un thread d'interface utilisateur.  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **Applications de Store**  
  
 Dans les applications de Store, utilisez la méthode <xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName> pour exécuter un délégué qui met à jour le thread d'interface utilisateur. Si nécessaire, utilisez la propriété <xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A> pour déterminer si une méthode est en cours d'exécution sur un autre thread qu'un thread d'interface utilisateur.  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Une méthode qui s'exécute sur un autre thread qu'un thread d'interface utilisateur met à jour l'interface utilisateur](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> Une instruction d'un bloc foreach \(For Each en Visual Basic\) change la collection dans laquelle elle itère  
 [Levée d'une exception InvalidOperationException avec foreach](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [Éviter les exceptions InvalidOperationException dans les boucles](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 Une instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) \([For Each](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) en Visual Basic\) répète un groupe d'instructions intégrées pour chaque élément d'un tableau ou d'une collection qui implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>. La déclaration `foreach` sert à itérer la collection pour lire et modifier les éléments. Toutefois, elle ne peut pas être utilisée pour ajouter ou supprimer des éléments dans la collection. Une exception <xref:System.InvalidOperationException> est levée si vous ajoutez ou supprimez des éléments dans la collection source d'une instruction foreach.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> Levée d'une exception InvalidOperationException avec foreach  
 Dans cet exemple, une exception <xref:System.InvalidOperationException> est levée quand l'instruction `numList.Add(5);` tente de changer la liste dans le bloc foreach.  
  
 **Message d'exception :**  
  
-   Informations supplémentaires : la collection a été modifiée ; l'opération d'énumération peut ne pas s'exécuter.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Une instruction d'un bloc foreach (For Each en Visual Basic) change la collection dans laquelle elle itère](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> Éviter les exceptions InvalidOperationException dans les boucles  
  
> [!IMPORTANT]
>  L'ajout ou la suppression d'éléments dans une liste durant une itération dans la collection peut avoir des conséquences non souhaitées et difficiles à prévoir. Si possible, évitez d'effectuer l'opération durant l'itération.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 Si vous êtes obligé d'ajouter ou de supprimer des éléments dans une liste durant une itération dans une collection, utilisez une boucle [for](/dotnet/csharp/language-reference/keywords/for) \([For](/dotnet/visual-basic/language-reference/statements/for-next-statement) en Visual Basic\) :  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Une instruction d'un bloc foreach (For Each en Visual Basic) change la collection dans laquelle elle itère](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> Un Nullable\<T\> qui a la valeur Null fait l'objet d'un transtypage en T  
 [Levée d'une exception InvalidOperationException avec un transtypage non valide](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [Éviter l'exception InvalidOperationException à partir d'un transtypage incorrect](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 Si vous effectuez le transtypage d'une structure <xref:System.Nullable%601> qui a la valeur `null` \(`Nothing` en Visual Basic\) vers son type sous\-jacent, une exception <xref:System.InvalidOperationException> est levée.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> Levée d'une exception InvalidOperationException avec un transtypage non valide  
 Dans cette méthode, une exception <xref:System.InvalidOperationException> est levée quand la méthode Select effectue le transtypage d'un élément Null de dbQueryResults vers un type int.  
  
 **Message d'exception :**  
  
-   Informations supplémentaires : un objet qui autorise la valeur Null doit posséder une valeur.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Un Nullable&lt;T&gt; qui a la valeur Null fait l'objet d'un transtypage en T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> Éviter l'exception InvalidOperationException à partir d'un transtypage incorrect  
 Pour éviter <xref:System.InvalidOperationException> :  
  
-   Utilisez la propriété <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName> pour sélectionner uniquement les éléments qui n'ont pas la valeur Null.  
  
-   Utilisez l'une des méthodes <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> surchargées pour fournir une valeur par défaut pour un élément Null.  
  
 **Exemple Nullable\<T\>.HasValue**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Exemple Nullable\<T\>.GetValueOrDefault**  
  
 Dans cet exemple, nous utilisons <xref:System.Nullable%601.GetValueOrDefault%28%600%29> pour spécifier une valeur par défaut située en dehors des valeurs attendues retournées par `dbQueryResults`.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Un Nullable&lt;T&gt; qui a la valeur Null fait l'objet d'un transtypage en T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> Une méthode System.Linq.Enumerable est appelée sur une collection vide  
 Les méthodes <xref:System.Linq.Enumerable><xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.First%2A>, <xref:System.Linq.Enumerable.Single%2A> et <xref:System.Linq.Enumerable.SingleOrDefault%2A> effectuent des opérations sur une séquence et ne retournent qu'un seul résultat.  
  
 Certaines surcharges de ces méthodes lèvent une exception <xref:System.InvalidOperationException> quand la séquence est vide \(d'autres surcharges retournent `null` \(`Nothing` en Visual Basic\).<xref:System.Linq.Enumerable.SingleOrDefault%2A> lève également <xref:System.InvalidOperationException> quand la séquence contient plusieurs éléments.  
  
> [!TIP]
>  La plupart des méthodes <xref:System.Linq.Enumerable> décrites dans cette section sont surchargées. Vous devez bien comprendre le comportement de la surcharge que vous choisissez.  
  
 **Messages d'exception :**  
  
 [Méthodes Aggregate, Average, Last, Max et Min](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [Méthodes First et FirstOrDefault](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Méthodes Single et SingleOrDefault](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Méthodes Aggregate, Average, Last, Max et Min  
  
-   Informations supplémentaires : la séquence ne contient aucun élément.  
  
 **Levée d'une exception InvalidOperationException avec Average**  
  
 Dans cet exemple, la méthode suivante lève une exception <xref:System.InvalidOperationException> quand elle appelle la méthode <xref:System.Linq.Enumerable.Average%2A>, car l'expression Linq retourne une séquence qui ne contient aucun élément supérieur à 4.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 Quand vous utilisez l'une de ces méthodes sans rechercher la présence d'une séquence vide, vous supposez implicitement que la séquence n'est pas vide et qu'une séquence vide est un événement inattendu. L'interception ou la levée d'une exception est appropriée quand vous supposez que la séquence n'est pas vide.  
  
 **Éviter une exception InvalidOperationException causée par une séquence vide**  
  
 Utilisez l'une des méthodes <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName> pour vérifier si la séquence est vide.  
  
> [!TIP]
>  L'utilisation de <xref:System.Linq.Enumerable.Any%2A> peut améliorer les performances de la vérification si la séquence dont la moyenne est à calculer peut contenir un grand nombre d'éléments, ou si l'opération qui génère la séquence est coûteuse.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Une méthode System.Linq.Enumerable est appelée sur une collection vide](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> Méthodes First et FirstOrDefault  
 <xref:System.Linq.Enumerable.First%2A> retourne le premier élément d'une séquence ou lève une exception <xref:System.InvalidOperationException> si la séquence est vide.  Vous pouvez appeler la méthode <xref:System.Linq.Enumerable.FirstOrDefault%2A> à la place de <xref:System.Linq.Enumerable.First%2A> pour retourner une valeur spécifique ou par défaut au lieu de lever l'exception.  
  
> [!NOTE]
>  Dans le .NET Framework, les types possèdent un concept de valeurs par défaut. Ainsi, la valeur par défaut d'un type référence est Null, et celle d'un type entier est zéro. Voir [Tableau des valeurs par défaut](/dotnet/csharp/language-reference/keywords/default-values-table)  
  
 **Levée d'une exception InvalidOperationException avec First**  
  
 <xref:System.Linq.Enumerable.First%2A> est une méthode d'optimisation qui retourne le premier élément d'une séquence qui répond à une condition spécifique. Si aucun élément répondant à la condition n'est trouvé, les méthodes lèvent une exception <xref:System.InvalidOperationException>.  
  
 Dans cet exemple, la méthode `First` lève l'exception, car `dbQueryResults` ne contient aucun élément supérieur à 4.  
  
 **Message d'exception :**  
  
-   Informations supplémentaires : la séquence ne contient aucun élément correspondant.  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **Éviter une exception avec FirstOrDefault**  
  
 Vous pouvez utiliser l'une des méthodes <xref:System.Linq.Enumerable.FirstOrDefault%2A> à la place de <xref:System.Linq.Enumerable.First%2A> pour vérifier que la séquence `firstNum` contient au moins un élément. Si la requête ne trouve aucun élément répondant à la condition, elle retourne une valeur spécifique ou par défaut. Vous pouvez vérifier la valeur retournée pour déterminer si des éléments ont été trouvés.  
  
> [!NOTE]
>  L'utilisation de <xref:System.Linq.Enumerable.FirstOrDefault%2A> peut être plus compliquée à mettre en œuvre si la valeur par défaut du type est un élément valide dans la séquence.  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Une méthode System.Linq.Enumerable est appelée sur une collection vide](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Méthodes Single et SingleOrDefault  
 Les méthodes <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName> retournent le seul élément d'une séquence, ou le seul élément d'une séquence qui répond au test spécifié.  
  
 S'il n'y a aucun élément dans la séquence, ou s'il existe plusieurs éléments dans cette dernière, la méthode lève une exception <xref:System.InvalidOperationException>.  
  
 Vous pouvez utiliser <xref:System.Linq.Enumerable.SingleOrDefault%2A> pour retourner une valeur spécifique ou par défaut au lieu de lever l'exception quand la séquence ne contient aucun élément. Toutefois, <xref:System.Linq.Enumerable.SingleOrDefault%2A> lève toujours une exception <xref:System.InvalidOperationException> quand la séquence contient plusieurs éléments qui correspondent au prédicat de sélection.  
  
> [!NOTE]
>  Dans le .NET Framework, les types possèdent un concept de valeurs par défaut. Ainsi, la valeur par défaut d'un type référence est Null, et celle d'un type entier est zéro. Voir [Tableau des valeurs par défaut](/dotnet/csharp/language-reference/keywords/default-values-table)  
  
 **Levée d'exceptions InvalidOperationException avec Single**  
  
 Dans cet exemple, `singleObject` lève une exception <xref:System.InvalidOperationException>, car `dbQueryResults` ne contient aucun élément supérieur à 4.  
  
 **Message d'exception :**  
  
-   Informations supplémentaires : la séquence ne contient aucun élément correspondant.  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **Levée d'exceptions InvalidOperationException avec Single ou SingleOrDefault**  
  
 Dans cet exemple, `singleObject` lève une exception <xref:System.InvalidOperationException>, car `dbQueryResults` contient plusieurs éléments supérieurs à 2.  
  
 **Message d'exception :**  
  
-   Informations supplémentaires : la séquence contient plusieurs éléments correspondants.  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **Éviter les exceptions InvalidOperationException avec Single**  
  
 <xref:System.Linq.Enumerable.Single%2A> et <xref:System.Linq.Enumerable.SingleOrDefault%2A> représentent également une documentation de vos intentions.<xref:System.Linq.Enumerable.Single%2A> implique clairement que vous vous attendez à ce que la condition ne retourne qu'un et un seul résultat.<xref:System.Linq.Enumerable.SingleOrDefault%2A> indique que vous vous attendez à un seul résultat, voire aucun, mais rien d'autre. Quand ces conditions ne sont pas valides, la levée ou l'interception de l'exception <xref:System.InvalidOperationException> est appropriée. Toutefois, si vous vous attendez à ce que des conditions non valides se produisent à une certaine fréquence, utilisez d'autres méthodes <xref:System.Linq.Enumerable>, telles que <xref:System.Linq.Enumerable.First%2A> ou <xref:System.Linq.Enumerable.Where%2A>, pour générer vos résultats.  
  
 Durant le développement, vous pouvez utiliser l'une des méthodes <xref:System.Diagnostics.Debug.Assert%2A> pour vérifier vos hypothèses. Dans cet exemple, le code en surbrillance provoque l'arrêt du débogueur et l'affichage d'une boîte de dialogue d'assertion durant le développement. L'assertion est supprimée du code de version. Par ailleurs, <xref:System.Linq.Enumerable.Single%2A> est levé si les résultats ne sont pas valides.  
  
> [!NOTE]
>  L'utilisation de <xref:System.Linq.Enumerable.Take%2A> et l'affectation de la valeur 2 à son paramètre `count` limite la séquence retournée à deux éléments au maximum. Cette séquence inclut tous les cas que vous devez vérifier \(0, 1 et plus de 1 élément\). En outre, elle peut améliorer les performances de la vérification quand la séquence contient parfois un grand nombre d'éléments ou quand l'opération qui génère la séquence est coûteuse.  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 Si vous souhaitez éviter l'exception tout en gérant les états non valides dans le code de version, changez la technique décrite ci\-dessus. Dans cet exemple, la méthode répond au nombre d'éléments retournés par `moreThan2` dans l'instruction switch.  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Une méthode System.Linq.Enumerable est appelée sur une collection vide](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> Articles connexes  
 [Instructions de conception pour les exceptions \(Instructions de conception du .NET Framework\)](http://msdn.microsoft.com/library/ms229014)  
  
 [Gestion et levée des exceptions \(Notions de base des applications .NET Framework\)](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [Procédure : réception de notifications des exceptions de première chance \(Guide de développement .NET Framework\)](http://msdn.microsoft.com/library/Dd997368)  
  
 [Procédure : gestion des exceptions dans une requête PLINQ \(Guide de développement .NET Framework\)](http://msdn.microsoft.com/library/Dd460712)  
  
 [Exceptions dans les threads managés \(Guide de développement .NET Framework\)](http://msdn.microsoft.com/library/ms228965)  
  
 [Exceptions et gestion des exceptions \(Guide de programmation C\#\)](http://msdn.microsoft.com/library/ms173160)  
  
 [Instructions de gestion des exceptions \(Référence C\#\)](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Try...Catch...Finally, instruction \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [Gestion des exceptions \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [Exceptions dans C\+\+\/CLI](http://msdn.microsoft.com/library/Hh875008)  
  
 [Gestion des exceptions \(bibliothèque parallèle de tâches\)](http://msdn.microsoft.com/library/Dd997415)  
  
 [Gestion des exceptions \(débogage\)](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [Procédure pas à pas : gestion d’une exception d’accès concurrentiel \(Accès aux données dans Visual Studio\)](http://msdn.microsoft.com/library/ms171936)  
  
 [Procédure : gestion des erreurs et des exceptions qui se produisent avec Databinding \(Windows Forms\)](http://msdn.microsoft.com/library/k26k86tb)  
  
 [Gestion des exceptions dans les applications réseau \(XAML\) \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Dans cet article](#BKMK_In_this_article)