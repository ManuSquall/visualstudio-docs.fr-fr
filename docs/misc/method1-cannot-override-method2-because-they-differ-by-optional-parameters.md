---
title: "&#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car seuls les param&#232;tres facultatifs les diff&#233;rencient | Microsoft Docs"
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
  - "vbc30308"
  - "bc30308"
helpviewer_keywords: 
  - "BC30308"
ms.assetid: 591dc351-4b87-4e92-81e1-2c1ff51da295
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car seuls les param&#232;tres facultatifs les diff&#233;rencient
Vous avez tenté de substituer une méthode par une autre méthode dont les valeurs des paramètres facultatifs la différencient de la première, ce qui signifie que leurs signatures sont différentes. Un type peut se substituer à une méthode substituable héritée en déclarant celle\-ci avec les mêmes nom et signature, et en marquant la déclaration avec le modificateur `Overrides`.  
  
 **ID d’erreur :** BC30308  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les deux méthodes ont la même signature.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)