---
title: "Erreur du compilateur CS0011 | Microsoft Docs"
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
  - "CS0011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0011"
ms.assetid: 892553d7-a516-4631-84cd-94db5722c90d
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0011
La classe de base ou l’interface 'classe' dans l’assembly 'assembly' référencé par le type 'type' n’a pas pu être résolue  
  
 Une classe qui a été importée à partir d’un fichier avec **\/reference** est dérivée d’une classe ou implémente une interface qui est introuvable. Cela peut se produire si une DLL requise n’est pas également incluse dans la compilation avec **\/reference**.  
  
 Pour plus d’informations, consultez [Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) et [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
## Exemple  
  
```  
// CS0011_1.cs // compile with: /target:library public class Outer { public class B { } }  
```  
  
## Exemple  
 Le deuxième fichier crée une DLL qui définit une classe `C` dérivée de la classe `B` qui a été créée dans l’exemple précédent.  
  
```  
// CS0011_2.cs // compile with: /target:library /reference:CS0011_1.dll // post-build command: del /f CS0011_1.dll public class C : Outer.B {}  
```  
  
## Exemple  
 Le troisième fichier remplace la DLL créée par la première étape et omet la définition de la classe interne `B`.  
  
```  
// CS0011_3.cs // compile with: /target:library /out:cs0011_1.dll public class Outer {}  
```  
  
## Exemple  
 Pour finir, le quatrième fichier fait référence à la classe `C` définie dans le deuxième exemple, qui est dérivée de la classe `B` et qui est maintenant manquante.  
  
 L’exemple suivant génère l’erreur CS0011.  
  
```  
// CS0011_4.cs // compile with: /reference:CS0011_1.dll /reference:CS0011_2.dll // CS0011 expected class M { public static void Main() { C c = new C(); } }  
```  
  
## Voir aussi  
 [Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)   
 [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)