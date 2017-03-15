---
title: "Avertissement du compilateur (niveau&#160;4) CS1573 | Microsoft Docs"
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
  - "CS1573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1573"
ms.assetid: 1b68cb1a-9bfd-4343-b9b6-8ce195af5e23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;4) CS1573
Le paramètre 'parameter' n’a pas de balise param correspondante dans le commentaire XML pour 'parameter' \(contrairement à d’autres paramètres\)  
  
 Lors de l’utilisation de l’option [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) du compilateur, un commentaire a été spécifié pour certains, mais pas pour tous les paramètres d’une méthode. Vous avez peut\-être oublié d’entrer un commentaire pour ces paramètres.  
  
 L’exemple suivant génère l’erreur CS1573 :  
  
```  
// CS1573.cs // compile with: /W:4 public class MyClass { /// <param name='Int1'>Used to indicate status.</param> // enter a comment for Char1? public static void MyMethod(int Int1, char Char1) { } public static void Main () { } }  
```