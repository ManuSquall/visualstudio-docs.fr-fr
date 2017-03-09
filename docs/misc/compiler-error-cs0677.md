---
title: "Erreur du compilateur CS0677 | Microsoft Docs"
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
  - "CS0677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0677"
ms.assetid: 6a4a3703-9b44-4c4f-a564-8b437b1cb6b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0677
'variable' : un champ volatile ne peut pas être de type 'type'  
  
 Les champs déclarés avec le mot clé `volatile` doivent être de l’un des types suivants :  
  
-   tout type référence ;  
  
-   tout type pointeur \(dans un contexte `unsafe`\) ;  
  
-   les types `sbyte`, **byte**, **short**, `ushort`, `int`, `uint`, `char`, **float**, `bool` ;  
  
-   les types enum basés sur l’un des types ci\-dessus.  
  
 L’exemple suivant génère l’erreur CS0677 :  
  
```  
// CS0677.cs class TestClass { private volatile long i;   // CS0677 public static void Main() { } }  
```