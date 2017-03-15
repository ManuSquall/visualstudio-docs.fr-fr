---
title: "Erreur du compilateur CS1689 | Microsoft Docs"
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
  - "CS1689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1689"
ms.assetid: 5fa6e845-40ef-4451-81ee-acbe2665527a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1689
L’attribut 'nom\_attribut' n’est valide que sur les méthodes ou les classes d’attributs  
  
 Cette erreur se produit uniquement avec l’attribut **ConditionalAttribute**. Comme l’indique le message, cet attribut peut être utilisé uniquement sur des méthodes ou des classes d’attributs. Cette erreur est par exemple générée si vous essayez d’appliquer cet attribut à une classe.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1689.  
  
```  
// CS1689.cs // compile with: /target:library [System.Diagnostics.Conditional("A")]   // CS1689 class MyClass {}  
```