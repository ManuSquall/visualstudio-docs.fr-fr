---
title: "&#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres d&#233;clar&#233;s &#39;ParamArray&#39; les diff&#233;rencient. | Microsoft Docs"
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
  - "bc30368"
  - "vbc30368"
helpviewer_keywords: 
  - "BC30368"
ms.assetid: 6111df0c-fc3e-40b2-b536-effbd132ef72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres d&#233;clar&#233;s &#39;ParamArray&#39; les diff&#233;rencient.
Vous avez tenté de surcharger deux méthodes qui diffèrent uniquement par un ou plusieurs paramètres `ParamArray`. Le compilateur considère qu’une procédure avec un paramètre `ParamArray` possède un nombre infini de surcharges différenciées par ce qui est passé au tableau de paramètres.  
  
 **ID d’erreur :** BC30368  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les méthodes ne sont pas différenciées uniquement par les paramètres `ParamArray`.  
  
## Voir aussi  
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)