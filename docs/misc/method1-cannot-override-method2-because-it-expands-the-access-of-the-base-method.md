---
title: "&#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car elle &#233;tend l’accessibilit&#233; de la m&#233;thode de base | Microsoft Docs"
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
  - "vbc32203"
  - "bc32203"
helpviewer_keywords: 
  - "BC32203"
ms.assetid: ef7816a4-5f57-4346-80fc-9311bc150b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car elle &#233;tend l’accessibilit&#233; de la m&#233;thode de base
Une procédure spécifie `Overrides`, mais déclare une accessibilité moins restrictive que celle de la méthode à substituer. Vous ne pouvez pas étendre l’accessibilité, ce qui signifie que vous ne pouvez pas rendre la méthode de substitution plus accessible que la méthode à laquelle elle se substitue. Par exemple, si la méthode de la classe de base est `Protected`, vous ne pouvez pas la substituer avec une méthode `Public`.  
  
 **ID d’erreur :** BC32203  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Overrides` ou modifiez l’accessibilité de sorte qu’elle ait au moins le même niveau de restriction que celle de la méthode de la classe de base.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)