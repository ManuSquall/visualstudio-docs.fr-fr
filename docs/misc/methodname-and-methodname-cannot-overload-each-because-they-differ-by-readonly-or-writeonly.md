---
title: "&#39;&lt;nom_m&#233;thode&gt;&#39; et &#39;&lt;nom_m&#233;thode&gt;&#39; ne peuvent pas se surcharger mutuellement, car seul &#39;ReadOnly&#39; ou &#39;WriteOnly&#39; les diff&#233;rencie | Microsoft Docs"
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
  - "vbc30366"
  - "BC30366"
helpviewer_keywords: 
  - "BC30366"
ms.assetid: 2440fd29-e205-4004-b2ee-9d954d17b8d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_m&#233;thode&gt;&#39; et &#39;&lt;nom_m&#233;thode&gt;&#39; ne peuvent pas se surcharger mutuellement, car seul &#39;ReadOnly&#39; ou &#39;WriteOnly&#39; les diff&#233;rencie
Vous avez tenté de surcharger deux méthodes qui diffèrent uniquement dans leurs déclarations `ReadOnly` et `WriteOnly`. Vous ne pouvez utiliser que la liste d’arguments pour différencier des versions.  
  
 **ID d’erreur :** BC30366  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les méthodes ne sont pas différenciées uniquement par `ReadOnly` et `WriteOnly`.  
  
## Voir aussi  
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)