---
title: "&#39;&lt;nom_m&#233;thode&gt;&#39; ne peut pas masquer une m&#233;thode d&#233;clar&#233;e &#39;MustOverride&#39; | Microsoft Docs"
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
  - "vbc31404"
  - "bc31404"
helpviewer_keywords: 
  - "BC31404"
ms.assetid: 3e7bb4a0-14af-46ba-bc62-2234c16f1827
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_m&#233;thode&gt;&#39; ne peut pas masquer une m&#233;thode d&#233;clar&#233;e &#39;MustOverride&#39;
Une propriété ou une méthode du même nom avec le modificateur `MustOverride` est déclarée dans une classe dérivée.  
  
 **ID d’erreur :** BC31404  
  
### Pour corriger cette erreur  
  
1.  Ajoutez le modificateur `Overrides` à la propriété ou à la méthode de substitution de la classe dérivée.  
  
2.  Supprimez le modificateur `MustOverride` de la méthode ou de la propriété de la classe de base.  
  
## Voir aussi  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)