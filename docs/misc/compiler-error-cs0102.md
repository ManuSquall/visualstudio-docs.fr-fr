---
title: "Erreur du compilateur CS0102 | Microsoft Docs"
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
  - "CS0102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0102"
ms.assetid: c9419779-649f-4c24-b0f3-f0a1be46659e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0102
Le type 'typename' contient déjà une définition pour 'identifier'  
  
 Une classe contient plusieurs déclarations pour des identificateurs portant le même nom dans la même étendue. Pour corriger cette erreur, renommez les identificateurs en double.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0102.  
  
```  
// CS0102.cs // compile with: /target:library namespace MyApp { public class MyClass { string s = "Hello"; string s = "Goodbye";   // CS0102 public void GetString() { string s = "Hello again";   // method scope, no error } } }  
  
```