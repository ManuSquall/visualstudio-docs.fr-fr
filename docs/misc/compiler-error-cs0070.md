---
title: "Erreur du compilateur CS0070 | Microsoft Docs"
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
  - "CS0070"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0070"
ms.assetid: bb0de7c6-c734-4a8f-ab62-0a50eac2a91f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0070
L’événement 'event' ne peut apparaître qu’à gauche de \+\= ou \-\= \(sauf en cas d’utilisation à partir du type 'type'\)  
  
 En dehors de la classe dans laquelle il est défini, un [événement](/dotnet/csharp/language-reference/keywords/event) peut uniquement ajouter ou soustraire des références. Pour plus d'informations, consultez [Événements](/dotnet/csharp/programming-guide/events/index).  
  
 L’exemple suivant génère l’erreur CS0070 :  
  
```  
// CS0070.cs using System; public delegate void EventHandler(); public class A { public event EventHandler Click; public static void OnClick() { EventHandler eh; A a = new A(); eh = a.Click; } public static void Main() { } } public class B { public int Foo () { EventHandler eh = new EventHandler(A.OnClick); A a = new A(); eh = a.Click;   // CS0070 // try the following line instead // a.Click += eh; return 1; } }  
```