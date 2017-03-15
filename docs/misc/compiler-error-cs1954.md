---
title: "Erreur du compilateur CS1954 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1954"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1954"
ms.assetid: bdec399e-c43d-46d3-a01b-ef3572786fe5
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1954
La méthode surchargée 'method' correspondant le mieux à l’élément de l’initialiseur de collection ne peut pas être utilisée. Les méthodes 'Add' de l’initialiseur de collection ne peuvent pas avoir de paramètres ref ou out.  
  
 Pour qu’une classe de collection soit initialisée à l’aide d’un initialiseur de collection, la classe doit avoir une méthode `Add``public` qui n’est pas un paramètre`ref` ou `out`.  
  
### Pour corriger cette erreur  
  
-   Si vous pouvez modifier le code source de la classe de collection, fournissez une méthode `Add` qui n’accepte pas un paramètre `ref` ou `out`.  
  
-   Si vous ne pouvez pas modifier la classe de collection, initialisez\-la avec les constructeurs qu’elle fournit. Vous ne pouvez pas utiliser un initialiseur de collection avec cette classe.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1954, car la seule surcharge disponible de la liste `Add` dans `MyList` possède un paramètre `ref`.  
  
```  
// cs1954.cs using System.Collections.Generic; class MyList<T> : IEnumerable<T> { List<T> _list; public void Add(ref T item) { _list.Add(item); } public System.Collections.Generic.IEnumerator<T> GetEnumerator() { int index = 0; T current = _list[index]; while (current != null) { yield return _list[index++]; } } System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator() { return GetEnumerator(); } } public class MyClass { public string tree { get; set; } } class Program { static void Main(string[] args) { MyList<MyClass> myList = new MyList<MyClass> { new MyClass { tree = "maple" } }; // CS1954 } }  
  
```  
  
## Voir aussi  
 [Initialiseurs d'objets et de collections](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)