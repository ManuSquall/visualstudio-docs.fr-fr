---
title: "Erreur du compilateur CS0171 | Microsoft Docs"
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
  - "CS0171"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0171"
ms.assetid: 8c1d76c9-1048-4579-9031-23e3566e6288
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0171
Le champ de stockage pour la propriété implémentée automatiquement 'nom' doit être entièrement assigné avant que le contrôle soit retourné à l’appelant. Appelez le constructeur par défaut à partir d’un initialiseur de constructeur.  
  
 Un constructeur dans un [struct](/dotnet/csharp/language-reference/keywords/struct) doit initialiser tous les champs du struct. Pour plus d'informations, consultez [Constructeurs](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 L’exemple suivant génère l’erreur CS0171 :  
  
```  
// CS0171.cs struct MyStruct { MyStruct(int initField)   // CS0171 { // i = initField;      // uncomment this line to resolve this error } public int i; } class MyClass { public static void Main() { MyStruct aStruct = new MyStruct(); } }  
```