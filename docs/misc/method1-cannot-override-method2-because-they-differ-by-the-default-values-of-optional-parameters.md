---
title: "&#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car seules les valeurs par d&#233;faut des param&#232;tres optionnels les diff&#233;rencient | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30307"
  - "bc30307"
helpviewer_keywords: 
  - "BC30307"
ms.assetid: c4cf6040-41c3-4650-8eb9-bff063756599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car seules les valeurs par d&#233;faut des param&#232;tres optionnels les diff&#233;rencient
Vous avez tenté de substituer une méthode par une autre méthode dont les valeurs par défaut des paramètres facultatifs la différencient de la première, ce qui signifie que leurs signatures sont différentes. Un type peut se substituer à une méthode substituable héritée en déclarant une méthode avec un nom et une signature identiques et en marquant la déclaration avec le modificateur `Overrides`.  
  
 **ID d’erreur :** BC30307  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les deux méthodes ont la même signature.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NOT IN BUILD : Substituer les modificateurs](http://msdn.microsoft.com/fr-fr/18e8ef02-e79b-470e-837a-46a8f4163d32)