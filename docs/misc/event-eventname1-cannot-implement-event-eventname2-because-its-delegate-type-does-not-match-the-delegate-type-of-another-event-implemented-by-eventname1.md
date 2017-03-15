---
title: "L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement1&gt;&#39; ne peut pas impl&#233;menter l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement2&gt;&#39;, car son type d&#233;l&#233;gu&#233; ne correspond pas au type d&#233;l&#233;gu&#233; d’un autre &#233;v&#233;nement impl&#233;ment&#233; par &#39;&lt;nom_&#233;v&#233;nement1&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31407"
  - "vbc31407"
helpviewer_keywords: 
  - "BC31407"
ms.assetid: 0b9ffddb-4759-438b-b569-beac7062e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement1&gt;&#39; ne peut pas impl&#233;menter l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement2&gt;&#39;, car son type d&#233;l&#233;gu&#233; ne correspond pas au type d&#233;l&#233;gu&#233; d’un autre &#233;v&#233;nement impl&#233;ment&#233; par &#39;&lt;nom_&#233;v&#233;nement1&gt;&#39;.
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas implémenter un événement, car le type délégué de cet événement ne correspond pas au type délégué d’un autre événement. Cette erreur peut se produire quand vous définissez plusieurs événements dans une interface et essayez ensuite de les implémenter ensemble avec le même événement. Un événement peut implémenter deux événements ou plus seulement si tous les événements implémentés sont déclarés à l’aide de la syntaxe `As` et s’ils spécifient le même type délégué.  
  
 **ID d’erreur :** BC31407  
  
### Pour corriger cette erreur  
  
-   Implémentez les événements séparément.  
  
## Voir aussi  
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)