---
title: "Erreur du compilateur CS0150 | Microsoft Docs"
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
  - "CS0150"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0150"
ms.assetid: 1fd08ca5-e1a9-42f5-93de-2916a3bdcad1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0150
Une valeur de constante est attendue  
  
 Une variable a été trouvée là où une constante était attendue. Pour plus d'informations, consultez [switch](/dotnet/csharp/language-reference/keywords/switch).  
  
 L’exemple suivant génère l’erreur CS0150 :  
  
```  
// CS0150.cs namespace MyNamespace { public class MyClass { public static void Main() { int i = 0; int j = 0; switch(i) { case j:   // CS0150, j is a variable int, not a constant int // try the following line instead // case 1: } } } }  
```  
  
 Cette erreur est également générée quand une taille de tableau est spécifiée avec une valeur de variable et initialisée avec un initialiseur de tableau. Pour supprimer l’erreur, initialisez le tableau dans une ou plusieurs instructions distinctes.  
  
```  
// CS0150.cs namespace MyNamespace { public class MyClass { public static void Main() { int size = 2; double[] nums = new double[size] { 46.9, 89.4 }; //CS0150 // Try the following lines instead // double[] nums = new double[size]; // nums[0] = 46.9; // nums[1] = 89.4; } } }  
  
```