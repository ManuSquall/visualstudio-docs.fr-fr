---
title: "D&#233;pannage des exceptions&#160;: System.IndexOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "IndexOutOfRangeException (classe)"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IndexOutOfRangeException
Une exception <xref:System.IndexOutOfRangeException> est levée lors d'une tentative d'accès à un élément d'un tableau ou d'une collection ayant un index en dehors des limites du tableau ou inférieur à zéro.  
  
## Conseils associés  
 **Assurez\-vous que la taille maximale de l'index sur une liste est inférieure à la taille de la liste.**  
 L'index maximal sur une liste doit être inférieur à la taille de la liste.  
  
 **Assurez\-vous que l'index n'est pas un nombre négatif.**  
 Cette exception est levée si l'index est inférieur à zéro.  
  
 **Assurez\-vous que les noms des colonnes de données sont corrects.**  
 Cette exception peut être levée si le nom de la colonne de données fourni à la propriété <xref:System.Data.DataView.Sort%2A?displayProperty=fullName> n'est pas valide. Pour plus d'informations, consultez la classe <xref:System.Data.DataView>.  
  
## Exemple  
  
### Description  
 L'exemple suivant utilise un bloc `Try…Catch` pour intercepter l'exception `IndexOutOfRangeException` lorsque l'index `i` se trouve en dehors des limites d'index de tableau, 0 à 3. L'exemple affiche les éléments suivants :  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### Code  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## Voir aussi  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index)