---
title: "Avertissement du compilateur&#160;(niveau&#160;4) CS0109 | Microsoft Docs"
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
  - "CS0109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0109"
ms.assetid: 42ac72e5-5081-4e8b-b2cf-5e10c1606676
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;4) CS0109
Le membre 'membre' ne masque pas un membre hérité. Le mot clé new n’est pas requis  
  
 Une déclaration de classe comprend le mot clé [new](/dotnet/csharp/language-reference/keywords/new) alors qu’elle ne remplace pas une déclaration existante dans une classe de base. Vous pouvez supprimer le mot clé **new**.  
  
 L’exemple suivant génère l’avertissement CS0109 :  
  
```  
// CS0109.cs // compile with: /W:4 namespace x { public class a { public int i; } public class b : a { public new int i; public new int j;   // CS0109 public static void Main() { } } }  
```