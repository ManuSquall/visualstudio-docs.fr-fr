---
title: "Erreur du compilateur CS0191 | Microsoft Docs"
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
  - "CS0191"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0191"
ms.assetid: 512479e4-656e-4dcb-8d71-801541d72dcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0191
La propriété ou l’indexeur 'nom' ne peut pas être assigné à \-\- il est en lecture seule  
  
 Un champ [readonly](/dotnet/csharp/language-reference/keywords/readonly) ne peut prendre une assignation que dans un constructeur ou au niveau d’une déclaration. Pour plus d'informations, consultez [Constructeurs](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 L’erreur CS0191 se produit aussi si le champ `readonly` est [static](/dotnet/csharp/language-reference/keywords/static) et que le constructeur n’est pas marqué `static`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0191.  
  
```  
// CS0191.cs class MyClass { public readonly int TestInt = 6;  // OK to assign to readonly field in declaration MyClass() { TestInt = 11; // OK to assign to readonly field in constructor } public void TestReadOnly() { TestInt = 19;                  // CS0191 } public static void Main() { } }  
```