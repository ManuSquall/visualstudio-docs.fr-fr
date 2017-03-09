---
title: "La premi&#232;re instruction de ce &#39;Sub New&#39; doit &#234;tre un appel &#224; &#39;MyBase.New&#39; ou &#39;MyClass.New&#39; (plusieurs constructeurs accessibles sans param&#232;tres) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32038"
  - "bc32038"
helpviewer_keywords: 
  - "BC32038"
ms.assetid: 52e4e9df-a85b-46ae-a0cc-7d8fa377fe95
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La premi&#232;re instruction de ce &#39;Sub New&#39; doit &#234;tre un appel &#224; &#39;MyBase.New&#39; ou &#39;MyClass.New&#39; (plusieurs constructeurs accessibles sans param&#232;tres)
La première instruction de ce 'Sub New' doit être un appel à 'MyBase.New' ou 'MyClass.New', car la classe de base '\<base\>' de '\<dérivé\>' a plusieurs 'Sub New' accessibles qu’il est possible d’appeler sans argument.  
  
 Un constructeur de classe ne fournit pas d’appel à un constructeur de classe de base, et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas fournir d’appel implicite, car il ne peut pas déterminer quel constructeur de classe de base appeler.  
  
 **ID d’erreur :** BC32038  
  
### Pour corriger cette erreur  
  
-   Ajoutez un appel à un constructeur de classe de base `MyBase.New()` ou à un autre constructeur de cette classe en utilisant `MyClass.New()` ou `Me.New()` comme première ligne de ce constructeur.  
  
## Voir aussi  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [MyBase \- delete](http://msdn.microsoft.com/fr-fr/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)