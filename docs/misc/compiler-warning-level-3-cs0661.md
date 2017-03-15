---
title: "Avertissement du compilateur (niveau&#160;3) CS0661 | Microsoft Docs"
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
  - "CS0661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0661"
ms.assetid: c218665e-5947-40bb-b633-d268483e6522
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS0661
'class' définit l’opérateur \=\= ou l’opérateur \!\= mais ne se substitue pas à Object.GetHashCode\(\)  
  
 Le compilateur a détecté l’opérateur d’égalité ou d’inégalité défini par l’utilisateur, mais n’a détecté aucune substitution pour la fonction **GetHashCode**. Un opérateur d’égalité ou d’inégalité défini par l’utilisateur sous\-entend que vous souhaitez également substituer la fonction **GetHashCode**.  
  
 L’exemple suivant génère l’avertissement CS0661 :  
  
```  
// CS0661.cs // compile with: /W:3 class Test   // CS0661 { public static bool operator == (object o, Test t) { return true; } public static bool operator != (object o, Test t) { return true; } public override bool Equals(object o) { return true; } // uncomment the GetHashCode function to resolve // public override int GetHashCode() // { //    return 0; // } public static void Main() { } }  
```