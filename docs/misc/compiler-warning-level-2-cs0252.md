---
title: "Avertissement du compilateur (niveau&#160;2) CS0252 | Microsoft Docs"
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
  - "CS0252"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0252"
ms.assetid: ff82fbac-01cf-4ae9-b6a0-3aa990096b46
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0252
Possibilité d’une comparaison de références involontaire ; pour obtenir une comparaison de valeurs, effectuez un cast de la partie gauche en type 'type'  
  
 Le compilateur effectue une comparaison de références. Si vous souhaitez comparer la valeur de chaînes, effectuez un cast de la partie gauche de l’expression en `type`.  
  
 L’exemple suivant génère l’avertissement CS0252 :  
  
```  
// CS0252.cs // compile with: /W:2 using System; class MyClass { public static void Main() { string s = "11"; object o = s + s; bool b = o == s;   // CS0252 // try the following line instead // bool b = (string)o == s; } }  
```