---
title: "Erreur du compilateur CS0056 | Microsoft Docs"
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
  - "CS0056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0056"
ms.assetid: 8878b09c-5b7b-40e0-be0d-61ef5b36c151
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0056
Accessibilité incohérente : le type de retour 'type' est moins accessible que l’opérateur 'opérateur'  
  
 Une construction publique doit retourner un objet accessible publiquement. Pour plus d'informations, consultez [Modificateurs d'accès](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 L’exemple suivant génère l’erreur CS0056 :  
  
```  
// CS0056.cs class MyClass // try the following line instead // public class MyClass { } public class A { public static implicit operator MyClass(A a)   // CS0056 { return new MyClass(); } public static void Main() { } }  
```