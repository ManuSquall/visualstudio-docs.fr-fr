---
title: "Erreur du compilateur CS0023 | Microsoft Docs"
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
  - "CS0023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0023"
ms.assetid: 7a30073c-99de-41fa-ac6d-4a0dfbb76de9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0023
Impossible d’appliquer l’opérateur 'opérateur' à un opérande de type 'type'  
  
 L’utilisateur a tenté d’appliquer un opérateur à une variable dont le type n’est pas compatible avec l’opérateur. Pour plus d’informations, consultez [Types](/dotnet/csharp/programming-guide/types/index) et [Opérateurs C\#](/dotnet/csharp/language-reference/operators/index).  
  
 L’exemple suivant génère l’erreur CS0023 :  
  
```  
// CS0023.cs namespace x { public class a { public static void Main() { string s = "hello"; s = -s;   // CS0023, minus operator not allowed on strings } } }  
```