---
title: "Erreur du compilateur CS0012 | Microsoft Docs"
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
  - "CS0012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0012"
ms.assetid: 5523e349-22f4-4b0b-b4b0-c4bf26c461f4
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0012
Le type 'type' est défini dans un assembly qui n’est pas référencé. Vous devez ajouter une référence à l’assembly 'assembly'.  
  
 La définition d’un type référencé est introuvable. Cela peut se produire si un fichier .DLL nécessaire n’est pas inclus dans la compilation. Pour plus d’informations, consultez [Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) et [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
 La séquence suivante de compilations provoque une erreur CS0012 :  
  
```  
// cs0012a.cs // compile with: /target:library public class A {}  
```  
  
 Puis :  
  
```  
// cs0012b.cs // compile with: /target:library /reference:cs0012a.dll public class B { public static A f() { return new A(); } }  
```  
  
 Puis :  
  
```  
// cs0012c.cs // compile with: /reference:cs0012b.dll class C { public static void Main() { object o = B.f();   // CS0012 } }  
```  
  
 Vous pouvez résoudre cette erreur CS0012 en compilant avec `/reference:cs0012b.dll;cs0012a.dll` ou, dans Visual Studio, en utilisant [Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) pour ajouter une référence à cs0012a.dll en plus de cs0012b.dll.