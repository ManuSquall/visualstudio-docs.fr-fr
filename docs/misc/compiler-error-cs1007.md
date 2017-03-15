---
title: "Erreur du compilateur CS1007 | Microsoft Docs"
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
  - "CS1007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1007"
ms.assetid: b56ee2c6-8e79-4b9b-8c59-194bdb22bc3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1007
Accesseur de propriété déjà défini  
  
 Lorsque vous déclarez une [propriété](/dotnet/csharp/programming-guide/classes-and-structs/using-properties), vous devez également déclarer ses méthodes d’accesseur. Toutefois, une propriété ne peut pas avoir plusieurs méthodes d’accesseur `get` ni plusieurs méthodes d’accesseur `set`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1007 :  
  
```  
// CS1007.cs public class clx { public int MyProperty { get { return 0; } get   // CS1007, this is the second get method { return 0; } } public static void Main() {} }  
```