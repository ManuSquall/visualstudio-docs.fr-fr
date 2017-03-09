---
title: "Erreur du compilateur CS0470 | Microsoft Docs"
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
  - "CS0470"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0470"
ms.assetid: b5a8e820-aa5c-4f69-b5c6-01c6a6bb82d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0470
La méthode 'méthode' ne peut pas implémenter l’accesseur d’interface 'accesseur' pour le type 'type'. Utilisez une implémentation d’interface explicite.  
  
 Cette erreur est générée lorsqu’un accesseur essaie d’implémenter une interface. Vous devez utiliser une implémentation d’interface explicite.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0470.  
  
```  
// CS0470.cs // compile with: /target:library interface I { int P { get; } } class MyClass : I { public int get_P() { return 0; }   // CS0470 public int P2 { get { return 0;} }   // OK }  
  
```