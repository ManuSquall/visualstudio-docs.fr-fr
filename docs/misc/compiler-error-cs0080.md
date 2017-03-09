---
title: "Erreur du compilateur CS0080 | Microsoft Docs"
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
  - "CS0080"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0080"
ms.assetid: 99035371-37d1-48b2-a8b9-e8a1ebd04f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0080
Les contraintes ne sont pas autorisées sur des déclarations non génériques  
  
 La syntaxe trouvée peut uniquement être utilisée dans une déclaration générique pour appliquer des contraintes au paramètre de type. Pour plus d'informations, consultez [Génériques](/dotnet/csharp/programming-guide/generics/index).  
  
 L’exemple suivant génère l’erreur CS0080 car MyClass n’est pas une classe générique et Foo n’est pas une méthode générique.  
  
```  
namespace MyNamespace { public class MyClass where MyClass : System.IDisposable // CS0080    //the following line shows an example of correct syntax //public class MyClass<T> where T : System.IDisposable { public void Foo() where Foo : new() // CS0080 //the following line shows an example of correct syntax //public void Foo<U>() where U : struct { } } public class Program { public static void Main() { } } }  
```