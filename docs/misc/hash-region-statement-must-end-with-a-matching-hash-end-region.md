---
title: "L’instruction &#39;#Region&#39; doit se terminer par un &#39;#End&#160;Region&#39; correspondant | Microsoft Docs"
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
  - "bc30681"
  - "vbc30681"
helpviewer_keywords: 
  - "BC30681"
ms.assetid: 05a0402b-da68-4ab8-b6d6-940379bc5973
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction &#39;#Region&#39; doit se terminer par un &#39;#End&#160;Region&#39; correspondant
Utilisez la directive `#Region` pour spécifier un bloc de code que vous pouvez développer ou réduire en mode Plan de l’éditeur de code [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le début et la fin des instructions `#Region` doivent se trouver dans le même bloc de code.  
  
 **ID d’erreur :** BC30681  
  
### Pour corriger cette erreur  
  
1.  Insérez `#End Region` à l’emplacement approprié dans le code après l’instruction `#Region`.  
  
## Voir aussi  
 [\#Region Directive](/dotnet/visual-basic/language-reference/directives/region-directive)