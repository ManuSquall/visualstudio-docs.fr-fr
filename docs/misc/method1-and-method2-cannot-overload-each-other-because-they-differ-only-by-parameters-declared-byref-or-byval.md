---
title: "&#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres d&#233;clar&#233;s &#39;ByRef&#39; ou &#39;ByVal&#39; les diff&#233;rencient. | Microsoft Docs"
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
  - "bc30345"
  - "vbc30345"
helpviewer_keywords: 
  - "BC30345"
ms.assetid: 82af13b1-2641-4881-b25a-c782974bded1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres d&#233;clar&#233;s &#39;ByRef&#39; ou &#39;ByVal&#39; les diff&#233;rencient.
Vous avez tenté de surcharger une méthode avec une autre méthode qui diffère de la première uniquement par un paramètre déclaré `ByRef` ou `ByVal`.  
  
 **ID d’erreur :** BC30345  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les méthodes ne se distinguent pas uniquement par le nom du paramètre `ByRef` ou `ByVal`.  
  
## Voir aussi  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)