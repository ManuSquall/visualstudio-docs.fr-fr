---
title: "&#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seules les valeurs par d&#233;faut des param&#232;tres facultatifs les diff&#233;rencient | Microsoft Docs"
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
  - "vbc30305"
  - "bc30305"
helpviewer_keywords: 
  - "BC30305"
ms.assetid: f07f925e-9f95-4885-bdba-eaba2d0483d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seules les valeurs par d&#233;faut des param&#232;tres facultatifs les diff&#233;rencient
Vous avez tenté de surcharger une méthode avec une autre méthode qui se distingue de la première uniquement par ses paramètres facultatifs. Une méthode dotée d’un paramètre facultatif équivaut à deux méthodes surchargées, une avec le paramètre facultatif et l’autre sans. Par conséquent, vous ne pouvez pas surcharger une méthode avec une liste d’arguments correspondant aux deux.  
  
 **ID d’erreur :** BC30305  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les méthodes ne se distinguent pas uniquement par les paramètres facultatifs.  
  
## Voir aussi  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)