---
title: "&#39;StrConv.LinguisticCasing&#39; n&#233;cessite &#39;StrConv.LowerCase&#39; ou &#39;StrConv.UpperCase&#39; | Microsoft Docs"
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
  - "vbrLinguisticRequirements"
ms.assetid: 99cdb11d-9488-460b-84fb-a27f43da8be4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;StrConv.LinguisticCasing&#39; n&#233;cessite &#39;StrConv.LowerCase&#39; ou &#39;StrConv.UpperCase&#39;
Vous avez tenté d’utiliser `StrConv.LinguisticCasing`, qui est uniquement valide en combinaison avec `StrConv.LowerCase` ou `StrConv.UpperCase`.  
  
### Pour corriger cette erreur  
  
1.  Utilisez `StrConv.LowerCase` ou `StrConv.UpperCase` conjointement à `StrConv.LinguisticCasing`.  
  
## Voir aussi  
 [NOT IN BUILD : Fonction StrConv](http://msdn.microsoft.com/fr-fr/31ceb44b-005b-455f-b344-9dd06efbf660)   
 [StrConv Constant Changes in Visual Basic .NET](http://msdn.microsoft.com/fr-fr/7a8c2781-2716-40dd-90c1-96c1548516e2)