---
title: "Erreur du compilateur CS0060 | Microsoft Docs"
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
  - "CS0060"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0060"
ms.assetid: ae6d4fb7-5ff9-4883-82c3-f55b190f439a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0060
Accessibilité incohérente : la classe de base 'classe1' est moins accessible que la classe 'classe2'  
  
 L’accessibilité de classe doit être cohérente entre la classe de base et la classe héritée.  
  
 L’exemple suivant génère l’erreur CS0060 :  
  
```  
// CS0060.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass2 : MyClass   // CS0060 { public static void Main() { } }  
```  
  
## Voir aussi  
 [Modificateurs d'accès](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)