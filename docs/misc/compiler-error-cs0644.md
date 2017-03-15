---
title: "Erreur du compilateur CS0644 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0644"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0644"
ms.assetid: 835f3ee2-f897-4ba2-ad13-af629a9ab7fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0644
'class1' ne peut pas dériver de la classe spéciale 'class2'  
  
 Les classes ne peuvent pas hériter explicitement des classes de base suivantes :  
  
-   **System.Enum**  
  
-   **System.ValueType**  
  
-   **System.Delegate**  
  
-   **System.Array**  
  
 Elles sont utilisées comme classes de base implicites par le compilateur. Par exemple, **System.ValueType** est la classe de base implicite des structures.  
  
 L’exemple suivant génère l’erreur CS0644 :  
  
```  
// CS0644.cs class MyClass : System.ValueType   // CS0644 { }  
```