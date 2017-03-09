---
title: "Erreur du compilateur CS0170 | Microsoft Docs"
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
  - "CS0170"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0170"
ms.assetid: ba881e38-2abf-4a5f-b9e6-28d26a5bd235
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0170
Utilisation d’un champ potentiellement non assigné 'field'  
  
 Un champ dans une structure a été utilisé sans être au préalable initialisé. Pour résoudre ce problème, déterminez d’abord le champ qui a été initialisé, puis initialisez\-le avant d’essayer d’y accéder. Pour plus d’informations sur l’initialisation de structures, consultez [Structures](/dotnet/csharp/programming-guide/classes-and-structs/structs) et [Utilisation de structs](/dotnet/csharp/programming-guide/classes-and-structs/using-structs).  
  
 L’exemple suivant génère l’erreur CS0170 :  
  
```  
// CS0170.cs public struct error { public int i; } public class MyClass { public static void Main() { error e; // uncomment the next line to resolve this error // e.i = 0; System.Console.WriteLine( e.i );   // CS0170 because //e.i was never assigned } }  
```