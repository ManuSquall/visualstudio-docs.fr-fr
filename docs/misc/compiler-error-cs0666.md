---
title: "Erreur du compilateur CS0666 | Microsoft Docs"
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
  - "CS0666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0666"
ms.assetid: 44ad4574-b4a2-487b-8d05-0116762231ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0666
'membre' : nouveau membre protected déclaré dans struct  
  
 Un [struct](/dotnet/csharp/language-reference/keywords/struct) ne peut pas être [abstract](/dotnet/csharp/language-reference/keywords/abstract) et est toujours implicitement [sealed](/dotnet/csharp/language-reference/keywords/sealed). Les structs ne prenant pas en charge l’héritage, le concept de membre [protected](/dotnet/csharp/language-reference/keywords/protected) dans un struct n’a aucun sens. Pour plus d'informations, consultez [Héritage](/dotnet/csharp/programming-guide/classes-and-structs/inheritance).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0666 :  
  
```  
// CS0666.cs class M { static void Main() { } } struct S { protected int x;   // CS0666 }  
```