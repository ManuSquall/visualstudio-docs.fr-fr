---
title: "Aucun &#39;&lt;nom_proc&#233;dure&gt;&#39; accessible n’est plus sp&#233;cifique&#160;: &lt;liste_signatures&gt; | Microsoft Docs"
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
  - "vbc30794"
  - "BC30794"
helpviewer_keywords: 
  - "BC30794"
ms.assetid: 51d54cbb-b530-4661-9952-5ccc17e4220b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aucun &#39;&lt;nom_proc&#233;dure&gt;&#39; accessible n’est plus sp&#233;cifique&#160;: &lt;liste_signatures&gt;
Une instruction d’assignation assigne l’adresse d’une procédure surchargée à une variable de délégué, mais le compilateur ne peut trancher entre les versions surchargées.  
  
 Quand le code utilise l’adresse d’une procédure définie dans plusieurs versions surchargées, le compilateur doit déterminer quelle surcharge utiliser. Il essaie de trouver une seule version à partir d’une liste de paramètres qui correspond à la liste de paramètres délégués. Pour plus d'informations, consultez [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Si le compilateur identifie plusieurs versions de la procédure avec une signature correspondante, il génère cette erreur. Cela peut se produire si, par exemple, l’une des surcharges est générique et que l’argument de type qui lui est passé lui attribue une signature identique à celle d’une autre surcharge.  
  
 **ID d’erreur :** BC30794  
  
### Pour corriger cette erreur  
  
-   Si le conflit est dû au fait qu’une surcharge générique a la même signature qu’une autre surcharge, modifiez l’argument de type passé à cette surcharge générique.  
  
## Voir aussi  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)