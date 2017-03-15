---
title: "Impossible de convertir l’expression &#39;AddressOf&#39; en &#39;&lt;nom_type&gt;&#39;, car le type &#39;&lt;nom_type&gt;&#39; est d&#233;clar&#233; &#39;MustInherit&#39; et ne peut pas &#234;tre cr&#233;&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30939"
  - "bc30939"
helpviewer_keywords: 
  - "BC30939"
ms.assetid: e8edef15-0df5-46d7-aba6-89e26a2aa506
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de convertir l’expression &#39;AddressOf&#39; en &#39;&lt;nom_type&gt;&#39;, car le type &#39;&lt;nom_type&gt;&#39; est d&#233;clar&#233; &#39;MustInherit&#39; et ne peut pas &#234;tre cr&#233;&#233;
Une instruction tente de convertir une expression `AddressOf` en type qui ne peut être qu’une classe de base et ne peut pas être utilisé pour créer une instance.  
  
 L’opérateur `AddressOf` crée une instance de délégué de procédure qui fait référence à une procédure spécifique.  
  
 **ID d’erreur :** BC30939  
  
### Pour corriger cette erreur  
  
-   Assignez l’expression `AddressOf` à un type délégué spécifique.  
  
## Voir aussi  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)