---
title: "Erreur du compilateur CS1657 | Microsoft Docs"
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
  - "CS1657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1657"
ms.assetid: 6f0aeebe-5c90-4d5b-981c-1795d2e8fbb9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1657
Impossible de passer 'parameter' en tant qu’argument ref ou out car 'reason'  
  
 Cette erreur se produit quand une variable est passée en tant qu’argument [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out) dans un contexte dans lequel cette variable est en lecture seule. Les contextes en lecture seule incluent les variables d’itération [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), les variables [using](/dotnet/csharp/language-reference/keywords/using-statement) et les variables `fixed`. Pour résoudre cette erreur, n’appelez pas les fonctions qui acceptent la variable `foreach`, `using` ou `fixed` en tant que paramètre `ref` ou `out` dans des blocs `using`, des instructions `foreach` et des instructions `fixed`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1657 :  
  
```  
// CS1657.cs using System; class C : IDisposable { public int i; public void Dispose() {} } class CMain { static void f(ref C c) { } static void Main() { using (C c = new C()) { f(ref c);  // CS1657 } } }  
```  
  
## Exemple  
 Le code suivant illustre le même problème dans une instruction `fixed` :  
  
```  
// CS1657b.cs // compile with: /unsafe unsafe class C { static void F(ref int* p) { } static void Main() { int[] a = new int[5]; fixed(int* p = a) F(ref p); // CS1657 } }  
```