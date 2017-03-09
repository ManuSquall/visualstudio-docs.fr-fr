---
title: "Les m&#233;thodes d&#233;clar&#233;es &#39;Overrides&#39; ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;Overridable&#39;, car elles sont implicitement substituables | Microsoft Docs"
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
  - "bc30730"
  - "vbc30730"
helpviewer_keywords: 
  - "BC30730"
ms.assetid: cc892f81-eb1f-42a9-8f54-eff352adb5dd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes d&#233;clar&#233;es &#39;Overrides&#39; ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;Overridable&#39;, car elles sont implicitement substituables
Contrairement à la plupart des méthodes, les méthodes marquées avec le modificateur `Overrides` sont substituables par défaut.  
  
 **ID d’erreur :** BC30730  
  
### Pour corriger cette erreur  
  
-   Omettez le modificateur `Overridable` dans les méthodes marquées avec le modificateur `Overrides`.  
  
## Voir aussi  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)