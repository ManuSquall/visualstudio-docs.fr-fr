---
title: "Erreur du compilateur CS0271 | Microsoft Docs"
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
  - "CS0271"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0271"
ms.assetid: eadc9fb5-7770-4ec4-94f6-3c7cf37eec06
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0271
La propriété ou l’indexeur 'property\/indexer' ne peut pas être utilisé dans ce contexte, car l’accesseur get n’est pas accessible  
  
 Cette erreur se produit quand vous essayez d’accéder à un accesseur `get` inaccessible. Pour résoudre cette erreur, augmentez l’accessibilité de l’accesseur ou modifiez l’emplacement d’appel. Pour plus d’informations, consultez [Accessibilité de l’accesseur](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility) et [Propriétés](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 L’exemple suivant génère l’erreur CS0271 :  
  
```  
// CS0271.cs public class MyClass { public int Property { private get { return 0; } set { } } public int Property2 { get { return 0; } set { } } } public class Test { public static void Main(string[] args) { MyClass c = new MyClass(); int a = c.Property;   // CS0271 int b = c.Property2;   // OK } }  
```