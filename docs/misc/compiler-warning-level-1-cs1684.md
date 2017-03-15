---
title: "Avertissement du compilateur (niveau&#160;1) CS1684 | Microsoft Docs"
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
  - "CS1684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1684"
ms.assetid: 620419bf-b6d5-4cda-a549-fcacf2f08920
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1684
Une référence au type 'nom\_type' déclare qu’il est défini dans 'espace\_de\_noms', mais il est introuvable  
  
 Cette erreur peut être due au fait qu’une référence à l’intérieur d’un espace de noms fait référence à un type déclaré comme existant à l’intérieur d’un deuxième espace de noms, alors que le type n’existe pas. Par exemple, mydll.dll déclare que le type `A` existe dans yourdll.dll, mais ce type n’existe pas dans yourdll.dll. L’une des causes possibles de cette erreur est que la version de yourdll.dll que vous utilisez est trop ancienne et que `A` n’a pas encore été défini.  
  
 L’exemple suivant génère l’erreur CS1684.  
  
## Exemple  
  
```  
// CS1684_a.cs // compile with: /target:library /keyfile:CS1684.key public class A { public void Test() {} } public class C2 {}  
```  
  
## Exemple  
  
```  
// CS1684_b.cs // compile with: /target:library /r:cs1684_a.dll // post-build command: del /f CS1684_a.dll using System; public class Ref { public static A GetA() { return new A(); } public static C2 GetC() { return new C2(); } }  
```  
  
## Exemple  
 Nous reconstruisons maintenant le premier assembly, la définition de la classe C2 n’étant plus définie dans la recompilation.  
  
```  
// CS1684_c.cs // compile with: /target:library /keyfile:CS1684.key /out:CS1684_a.dll public class A { public void Test() {} }  
```  
  
## Exemple  
 Ce module fait référence au deuxième module au moyen de l’identificateur `Ref`. Mais le deuxième module contient une référence à la classe `C2`, qui n’existe plus en raison de la compilation à l’étape précédente. Ainsi, le message d’erreur CS1684 est retourné par la compilation de ce module.  
  
```  
// CS1684_d.cs // compile with: /reference:cs1684_a.dll /reference:cs1684_b.dll // CS1684 expected class Tester { public static void Main() { Ref.GetA().Test(); } }  
```