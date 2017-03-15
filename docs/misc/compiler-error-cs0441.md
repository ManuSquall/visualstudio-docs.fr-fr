---
title: "Erreur du compilateur CS0441 | Microsoft Docs"
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
  - "CS0441"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0441"
ms.assetid: 3f07500a-d479-424c-a0f4-c219be1b5a45
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0441
'class' : une classe ne peut pas être à la fois static et sealed  
  
 Cette erreur se produit quand vous déclarez une classe qui est à la fois static et sealed. Les classes static sont par nature sealed. Le modificateur sealed n’est donc pas nécessaire. Pour résoudre ce problème, utilisez un seul modificateur.  
  
 L’exemple suivant génère l’erreur CS0441 :  
  
```  
// CS0441.cs sealed static class MyClass { }   // CS0441  
```