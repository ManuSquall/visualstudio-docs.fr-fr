---
title: "&#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les types de retour les diff&#233;rencient. | Microsoft Docs"
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
  - "bc30301"
  - "vbc30301"
helpviewer_keywords: 
  - "BC30301"
ms.assetid: 5adc442b-9671-4d93-add8-42929b1a09b9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les types de retour les diff&#233;rencient.
Vous avez tenté de surcharger une méthode avec une autre méthode qui se distingue de la première uniquement par son type de retour. Dans une surcharge, vous devez distinguer deux versions quelconques d’une méthode par leurs listes d’arguments ; vous ne pouvez pas utiliser d’autres éléments que ces listes d’arguments pour différencier les méthodes.  
  
 **ID d’erreur :** BC30301  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les méthodes se distinguent par leurs listes d’arguments.  
  
## Voir aussi  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)