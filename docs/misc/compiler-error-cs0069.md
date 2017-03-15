---
title: "Erreur du compilateur CS0069 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0069"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0069"
ms.assetid: a1b32906-7773-47c6-8515-162a201a9be5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0069
Un événement dans une interface ne peut pas avoir d’accesseurs add ou remove  
  
 Vous ne pouvez pas définir les fonctions d’accesseur d’un événement dans une [interface](/dotnet/csharp/language-reference/keywords/interface). Pour plus d’informations, consultez [Événements](/dotnet/csharp/programming-guide/events/index) et [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 L’exemple suivant génère l’erreur CS0069 :  
  
```  
// CS0069.cs // compile with: /target:library public delegate void EventHandler(); public interface a { event EventHandler Click { remove {} }   // CS0069 event EventHandler Click2;   // OK }  
```