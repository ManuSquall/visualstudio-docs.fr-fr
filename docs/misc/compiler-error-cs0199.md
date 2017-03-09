---
title: "Erreur du compilateur CS0199 | Microsoft Docs"
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
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0199
Les champs d’un champ readonly statique 'name' ne peuvent pas être passés en ref ou out \(sauf s’ils appartiennent à un constructeur statique\)  
  
 Une variable [readonly](/dotnet/csharp/language-reference/keywords/readonly) doit avoir la même utilisation de [static](/dotnet/csharp/language-reference/keywords/static) que le constructeur dans lequel vous voulez la passer en tant que paramètre [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out). Pour plus d’informations, consultez [Passage de paramètres](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0199 :  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```