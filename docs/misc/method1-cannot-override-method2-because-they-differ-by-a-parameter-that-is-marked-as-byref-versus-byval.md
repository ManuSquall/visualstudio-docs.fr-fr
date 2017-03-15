---
title: "&#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car un param&#232;tre marqu&#233; comme ’ByRef’ pour l’une et ’ByVal’ pour l’autre les diff&#233;rencie | Microsoft Docs"
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
  - "vbc30398"
  - "bc30398"
helpviewer_keywords: 
  - "BC30398"
ms.assetid: 78d62276-4ad9-4876-8c35-a30c9c195638
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car un param&#232;tre marqu&#233; comme ’ByRef’ pour l’une et ’ByVal’ pour l’autre les diff&#233;rencie
Vous avez tenté de substituer une méthode par une autre méthode qui diffère par un paramètre marqué comme `ByRef` au lieu de `ByVal`. Les membres substitués doivent avoir les mêmes arguments que les membres hérités de la classe de base.  
  
 **ID d’erreur :** BC30398  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les paramètres sont tous les deux `ByRef` ou `ByVal`.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)