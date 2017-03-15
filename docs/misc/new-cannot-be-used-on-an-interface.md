---
title: "Impossible d’utiliser &#39;New&#39; pour une interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30375"
  - "bc30375"
helpviewer_keywords: 
  - "BC30375"
ms.assetid: c1e06108-1b52-4cbe-8cae-e816a0dbac0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’utiliser &#39;New&#39; pour une interface
Une [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement) utilise une clause [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) lors de la déclaration d’une variable comme étant d’un type interface.  
  
 Bien qu’une interface soit un type référence, vous ne pouvez pas créer d’instance de celle\-ci. Vous pouvez uniquement utiliser `New` pour créer une instance d’une classe ou d’une structure.  
  
 **ID d’erreur :** BC30375  
  
### Pour corriger cette erreur  
  
1.  Si la variable doit être d’un type interface, supprimez le mot clé `New`.  
  
2.  Si la variable doit faire référence à une instance, déclarez\-la comme étant d’un type classe ou structure. Conservez le mot clé `New` pour créer une instance.  
  
## Voir aussi  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)