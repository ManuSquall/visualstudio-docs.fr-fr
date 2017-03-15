---
title: "D&#233;pannage des exceptions&#160;: System.ArgumentException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ArgumentException (exception)"
  - "System.ArgumentException (exception)"
ms.assetid: d8052e62-bc73-4828-87e9-a84ef2a39a5b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.ArgumentException
Une exception <xref:System.ArgumentException> est levée lorsqu'au moins un des arguments fourni à une méthode ne répond pas aux spécifications des paramètres de cette méthode.  
  
 Dans l'exemple suivant, l'exception est levée lorsque l'argument envoyé à la méthode `DivideByTwo` n'est pas un nombre pair.  
  
```vb#  
Module Module1 Sub Main() ' ArgumentException is not thrown in DivideByTwo because 10 is ' an even number. Console.WriteLine("10 divided by 2 is {0}", DivideByTwo(10)) Try ' ArgumentException is thrown in DivideByTwo because 7 is ' not an even number. Console.WriteLine("7 divided by 2 is {0}", DivideByTwo(7)) Catch argEx As ArgumentException ' Tell the user which problem is encountered. Console.WriteLine("7 cannot be evenly divided by 2.") Console.WriteLine("Exception message: " & argEx.Message) End Try ' Uncomment the next statement to see what happens if you call ' DivideByTwo directly. 'Console.WriteLine(DivideByTwo(7)) End Sub Function DivideByTwo(ByVal num As Integer) As Integer ' If num is an odd number, throw an ArgumentException. The ' ArgumentException class provides a number of constructors ' that you can choose from. If num Mod 2 = 1 Then Throw New ArgumentException("Argument for num must be" & _ " an even number.") End If ' Value of num is even, so return half of its value. Return num / 2 End Function End Module  
```  
  
 Toutes les instances de la classe `ArgumentException` doivent comporter des informations qui spécifient l'argument qui n'est pas valide et la plage de valeurs acceptables. Si une exception plus précise, telle que <xref:System.ArgumentNullException> ou <xref:System.ArgumentOutOfRangeException>, décrit correctement la situation, elle doit être utilisée à la place d'`ArgumentException`.  
  
 Pour plus d'informations sur cette exception et obtenir des exemples dans d'autres langages, consultez <xref:System.ArgumentException>. Pour obtenir la liste d'autres constructeurs, consultez <xref:System.ArgumentException.%23ctor%2A>.  
  
## Voir aussi  
 <xref:System.ArgumentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)