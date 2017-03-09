---
title: "Erreur du compilateur CS0473 | Microsoft Docs"
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
  - "CS0473"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0473"
ms.assetid: 58eb141e-7da0-41c8-b868-7cd2a15f07f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0473
L’implémentation d’interface explicite 'method name' correspond à plusieurs membres d’interface. Le membre d’interface sélectionné dépend de l’implémentation. Si possible, utilisez plutôt une implémentation non explicite.  
  
 Dans certains cas, une méthode générique peut acquérir la même signature qu’une méthode non générique. Le problème est qu’il est impossible dans le système de métadonnées de l’infrastructure du langage commun \(CLI\) d’établir clairement quelle méthode est reliée à quel emplacement. Il appartient au CLI d’effectuer cette distinction.  
  
> [!NOTE]
>  Cette erreur est générée dans Visual Studio 2008 à des emplacements auxquels elle ne l’était pas dans Visual Studio 2005.  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’implémentation explicite et laissez l’implémentation implicite `public int TestMethod(int)` implémenter les deux méthodes d’interface.  
  
## Exemple  
 Le code suivant génère l’erreur CS0473 :  
  
```  
// cs0473.cs public interface ITest<T> { int TestMethod(int i); int TestMethod(T i); } public class ImplementingClass : ITest<int> { int ITest<int>.TestMethod(int i) // CS0473 { return i + 1; } public int TestMethod(int i) { return i - 1; } } class T { static int Main() { ImplementingClass a = new ImplementingClass(); if (a.TestMethod(0) != -1) return -1; ITest<int> i_a = a; System.Console.WriteLine(i_a.TestMethod(0).ToString()); if (i_a.TestMethod(0) != 1) return -1; return 0; } }  
  
```  
  
## Voir aussi  
 [Fabulous Adventures in Coding](http://blogs.msdn.com/ericlippert/archive/2006/04/06/570126.aspx)