---
title: "&#39;#End Region&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#Region&#39; correspondant | Microsoft Docs"
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
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End Region&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#Region&#39; correspondant
`#Region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de la fonctionnalité mode Plan de l’éditeur de code [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le début et la fin des instructions `#Region` doivent figurer dans le même bloc de code.  
  
 **ID d’erreur :** BC30680  
  
### Pour corriger cette erreur  
  
-   Insérez `#Region` à l’emplacement approprié avant l’instruction `#End` `Region` correspondante.  
  
## Voir aussi  
 [\#Region Directive](/dotnet/visual-basic/language-reference/directives/region-directive)