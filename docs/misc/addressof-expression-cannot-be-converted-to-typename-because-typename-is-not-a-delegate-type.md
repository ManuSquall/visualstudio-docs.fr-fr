---
title: "Impossible de convertir l’expression &#39;AddressOf&#39; en &#39;&lt;nom_type&gt;&#39;, car &#39;&lt;nom_type&gt;&#39; n’est pas un type d&#233;l&#233;gu&#233; | Microsoft Docs"
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
  - "vbc30581"
  - "bc30581"
helpviewer_keywords: 
  - "BC30581"
ms.assetid: 5db7589a-5456-4b3a-9d6b-93d9157f0484
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de convertir l’expression &#39;AddressOf&#39; en &#39;&lt;nom_type&gt;&#39;, car &#39;&lt;nom_type&gt;&#39; n’est pas un type d&#233;l&#233;gu&#233;
Une instruction tente de convertir une expression `AddressOf` en un type qui n’est pas un type délégué.  
  
 L’opérateur `AddressOf` crée une instance de délégué de procédure qui fait référence à une procédure spécifique. Vous pouvez utiliser `AddressOf` comme opérande d’un constructeur délégué, ou dans un contexte où le type du délégué peut être déterminé par le compilateur.  
  
 **ID d’erreur :** BC30581  
  
### Pour corriger cette erreur  
  
-   Modifiez le type cible en un type délégué.  
  
## Voir aussi  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)