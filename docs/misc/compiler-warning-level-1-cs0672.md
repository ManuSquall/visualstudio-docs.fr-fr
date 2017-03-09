---
title: "Avertissement du compilateur (niveau&#160;1) CS0672 | Microsoft Docs"
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
  - "CS0672"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0672"
ms.assetid: 140a8708-97d0-444b-980b-62e74328cafb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0672
Le membre 'membre1' se substitue au membre obsolète 'membre2'. Ajoutez l’attribut Obsolete à 'membre1'  
  
 Le compilateur a trouvé un `override` à une méthode marquée comme `obsolete`. Toutefois, la méthode de substitution n’était pas marquée comme obsolète. La méthode de substitution va générer l’erreur [CS0612](/dotnet/csharp/misc/cs0612) si elle est appelée.  
  
 Examinez vos déclarations de méthode et indiquez explicitement si une méthode \(et toutes ses substitutions\) doit être marquée `obsolete`.  
  
 L’exemple suivant génère l’erreur CS0672 :  
  
```  
// CS0672.cs // compile with: /W:1 class MyClass { [System.Obsolete] public virtual void ObsoleteMethod() { } } class MyClass2 : MyClass { public override void ObsoleteMethod()   // CS0672 { } } class MainClass { static public void Main() { } }  
```