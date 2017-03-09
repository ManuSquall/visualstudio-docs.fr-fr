---
title: "L’op&#233;rateur &#39;&lt;nom_op&#233;rateur&gt;&#39; n’est pas d&#233;fini pour les types &#39;&lt;nom_type1&gt;&#39; et &#39;&lt;nom_type2&gt;&#39; | Microsoft Docs"
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
  - "vbc31080"
  - "bc31080"
helpviewer_keywords: 
  - "BC31080"
ms.assetid: d2f77450-2bf2-4b1e-b95f-dbc7878f2777
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rateur &#39;&lt;nom_op&#233;rateur&gt;&#39; n’est pas d&#233;fini pour les types &#39;&lt;nom_type1&gt;&#39; et &#39;&lt;nom_type2&gt;&#39;
L’opérateur '\<nom\_opérateur\>' n’est pas défini pour les types '\<nom\_type1\>' et '\<nom\_type2\>' Utilisez 'Is' pour comparer deux types référence.  
  
 L’utilisateur a tenté d’utiliser un opérateur d’une manière qui ne convient pas aux types spécifiés. Cette erreur peut être due à l’utilisation de l’opérateur « \= » à la place de l’opérateur `Is` pour comparer deux objets.  
  
 **ID d’erreur :** BC31080  
  
### Pour corriger cette erreur  
  
1.  Utilisez l’opérateur `Is` pour comparer deux types référence.  
  
2.  Utilisez l’opérateur `Not` conjointement à l’opérateur `Is` pour montrer l’inégalité. Exemple :  
  
     [!code-vb[VbVbalrOOP#89](../misc/codesnippet/VisualBasic/operator-operatorname-is-not-defined-for-types-typename1-and-typename2_1.vb)]  
  
## Voir aussi  
 [Is Operator](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [\= Operator](/dotnet/visual-basic/language-reference/operators/assignment-operator)   
 [Not Operator](/dotnet/visual-basic/language-reference/operators/not-operator)