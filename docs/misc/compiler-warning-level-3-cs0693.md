---
title: "Avertissement du compilateur (niveau&#160;3) CS0693 | Microsoft Docs"
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
  - "CS0693"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0693"
ms.assetid: a3902336-49db-4808-b41f-8f0936bff53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS0693
Le paramètre de type 'paramètre de type' a le même nom que le paramètre de type du type externe  
  
 Cette erreur se produit quand un membre générique, tel qu’une méthode, se trouve dans une classe générique. Étant donné que le paramètre de type de la méthode peut ne pas être le même que celui de la classe, vous ne pouvez pas leur donner le même nom. Pour plus d'informations, consultez [Méthodes génériques](/dotnet/csharp/programming-guide/generics/generic-methods).  
  
 Pour éviter ce cas de figure, utilisez un nom différent pour chaque paramètre de type.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0693 :  
  
```  
// CS0693.cs // compile with: /W:3 /target:library class Outer<T> { class Inner<T> {}   // CS0693 // try the following line instead // class Inner<U> {} }  
```