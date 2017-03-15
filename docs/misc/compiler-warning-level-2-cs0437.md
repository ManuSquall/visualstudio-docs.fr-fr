---
title: "Avertissement du compilateur (niveau&#160;2) CS0437 | Microsoft Docs"
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
  - "CS0437"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0437"
ms.assetid: cba5c9b6-a0bc-4f19-b1f0-c1f66436ee91
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0437
Le type 'type' dans 'assembly2' est en conflit avec l’espace de noms importé 'espace\_de\_noms' dans 'fassembly1'. Utilisation du type défini dans 'assembly'.  
  
 Cet avertissement est émis quand un type inclus dans un fichier source, fichier\_2, est en conflit avec un espace de noms importé dans fichier\_1. Le compilateur utilise le type dans le fichier source.  
  
## Exemple  
  
```  
// CS0437_a.cs // compile with: /target:library namespace Util { public class A { public void Test() { System.Console.WriteLine("CS0437_a.cs"); } } }  
```  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0437.  
  
```  
// CS0437_b.cs // compile with: /reference:CS0437_a.dll /W:2 // CS0437 expected class Util { public class A { public void Test() { System.Console.WriteLine("CS0437_b.cs"); } } } public class Test { public static void Main() { Util.A x = new Util.A(); x.Test(); } }  
```