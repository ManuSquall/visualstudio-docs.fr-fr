---
title: "&#39;New&#39; ne peut pas &#234;tre utilis&#233; dans une classe d&#233;clar&#233;e &#39;MustInherit&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; ne peut pas &#234;tre utilis&#233; dans une classe d&#233;clar&#233;e &#39;MustInherit&#39;
Une classe `MustInherit` ne pouvant pas être instanciée directement, l’opérateur `New` ne peut donc pas être utilisé sur une classe `MustInherit`. Bien qu’il soit possible d’avoir des variables et des valeurs dont les types de compilation sont `MustInherit`, celles\-ci ont forcément une valeur null ou des références à des instances de classes normales dérivées des types `MustInherit`.  
  
 **ID d’erreur :** BC30569  
  
### Pour corriger cette erreur  
  
-   Supprimez l’opérateur `New`.  
  
## Voir aussi  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)