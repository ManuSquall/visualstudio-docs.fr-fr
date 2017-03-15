---
title: "Erreur du compilateur CS0308 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0308"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0308"
ms.assetid: b52ef9d2-f5b3-4baf-9a7e-bb1371e79463
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0308
Le type ou la méthode non générique 'identificateur' ne peut pas être utilisé avec des arguments de type.  
  
 Le type ou la méthode n’est pas générique, mais il ou elle a été utilisé\(e\) avec des arguments de type. Pour éviter cette erreur, supprimez les crochets et les arguments de type, ou redéclarez la méthode ou le type comme méthode ou type générique.  
  
 L’exemple suivant génère l’erreur CS0308 :  
  
```  
// CS0308a.cs class MyClass { public void F() {} public static void Main() { F<int>();  // CS0308 – F is not generic. // Try this instead: // F(); } }  
```  
  
 L’exemple suivant génère également l’erreur CS0308. Pour résoudre l’erreur, utilisez la directive « using System.Collections.Generic ».  
  
```  
// CS0308b.cs // compile with: /t:library using System.Collections; // To resolve, uncomment the following line: // using System.Collections.Generic; public class MyStack<T> { // Store the elements of the stack: private T[] items = new T[100]; private int stack_counter = 0; // Define the iterator block: public IEnumerator<T> GetEnumerator()   // CS0308 { for (int i = stack_counter - 1 ; i >= 0; i--) yield return items[i]; } }  
  
```