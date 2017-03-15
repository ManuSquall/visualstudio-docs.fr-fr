---
title: "Avertissement du compilateur (niveau&#160;1) CS0197 | Microsoft Docs"
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
  - "CS0197"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0197"
ms.assetid: 2b5b1b8d-ce13-4bd7-b80a-abb80e9f79ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0197
Le passage de 'argument' comme ref ou out ou la prise de son adresse peut provoquer une exception runtime, car il s’agit d’un champ d’une classe marshalée par référence  
  
 Toute classe qui dérive directement ou indirectement de <xref:System.MarshalByRefObject> est une classe marshalée par référence. Une telle classe peut être marshalée par référence au\-delà des limites du processus et de l’ordinateur. Par conséquent, les instances de cette classe peut être des proxys vers des objets distants. Vous ne pouvez pas passer un champ d’un objet proxy en tant que [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out). Vous ne pouvez donc pas passer les champs d’une telle classe en tant que `ref` ou `out`, sauf si l’instance est [this](/dotnet/csharp/language-reference/keywords/this), qui ne peut pas être un objet proxy.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0197.  
  
```  
// CS0197.cs // compile with: /W:1 class X : System.MarshalByRefObject { public int i; } class M { public int i; static void AddSeventeen(ref int i) { i += 17; } static void Main() { X x = new X(); x.i = 12; AddSeventeen(ref x.i);   // CS0197 // OK M m = new M(); m.i = 12; AddSeventeen(ref m.i); } }  
```