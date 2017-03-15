---
title: "Erreur du compilateur CS0198 | Microsoft Docs"
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
  - "CS0198"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0198"
ms.assetid: 222c20f6-3f7f-4750-9f99-b5e6ae6c1271
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0198
Les champs du champ readonly statique 'nom' ne peuvent pas être assignés \(sauf s’ils appartiennent à un constructeur statique ou un initialiseur de variable\)  
  
 Une variable [readonly](/dotnet/csharp/language-reference/keywords/readonly) doit avoir la même utilisation de [static](/dotnet/csharp/language-reference/keywords/static) que le constructeur dans lequel vous voulez l’initialiser. Pour plus d'informations, consultez [Constructeurs statiques](/dotnet/csharp/programming-guide/classes-and-structs/static-constructors).  
  
 L’exemple suivant génère l’erreur CS0198 :  
  
```  
// CS0198.cs class MyClass { public static readonly int TestInt = 6; MyClass() { TestInt = 11;   // CS0198, constructor is not static and readonly field is } public static void Main() { } }  
```