---
title: "Avertissement du compilateur (niveau&#160;4) CS0649 | Microsoft Docs"
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
  - "CS0649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0649"
ms.assetid: 37137b18-12ed-4a0f-92e6-ee5fb0532ef3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;4) CS0649
Le champ 'field' n’est jamais assigné et aura toujours sa valeur par défaut 'value'  
  
 Le compilateur a détecté une déclaration de champ privé ou interne non initialisée à laquelle une valeur n’est jamais assignée.  
  
 L’exemple suivant génère l’avertissement CS0649 :  
  
```  
// CS0649.cs // compile with: /W:4 using System.Collections; class MyClass { Hashtable table;  // CS0649 // You may have intended to initialize the variable to null // Hashtable table = null; // Or you may have meant to create an object here // Hashtable table = new Hashtable(); public void Func(object o, string p) { // Or here // table = new Hashtable(); table[p] = o; } public static void Main() { } }  
```