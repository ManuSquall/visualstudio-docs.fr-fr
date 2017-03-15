---
title: "Erreur du compilateur CS0074 | Microsoft Docs"
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
  - "CS0074"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0074"
ms.assetid: 9395c532-3934-4553-8e41-042bfe3399ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0074
'event' : un événement abstract ne peut pas avoir un initialiseur  
  
 Si un [événement](/dotnet/csharp/language-reference/keywords/event) est marqué comme étant **abstract**, il ne peut pas être initialisé. Pour plus d'informations, consultez [Événements](/dotnet/csharp/programming-guide/events/index).  
  
 L’exemple suivant génère l’erreur CS0074 :  
  
```  
// CS0074.cs delegate void D(); abstract class Test { public abstract event D e = null;   // CS0074 // try the following line instead // public abstract event D e; public static void Main() { } }  
```