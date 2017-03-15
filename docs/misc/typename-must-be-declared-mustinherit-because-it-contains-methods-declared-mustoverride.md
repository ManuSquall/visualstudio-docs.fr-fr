---
title: "&#39;&lt;nom_type&gt;&#39; doit &#234;tre d&#233;clar&#233; &#39;MustInherit&#39;, car il contient des m&#233;thodes d&#233;clar&#233;es &#39;MustOverride&#39;. | Microsoft Docs"
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
  - "vbc31411"
  - "bc31411"
helpviewer_keywords: 
  - "BC31411"
ms.assetid: 5a9f4c57-a4b8-45f5-8273-b7caa689a170
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; doit &#234;tre d&#233;clar&#233; &#39;MustInherit&#39;, car il contient des m&#233;thodes d&#233;clar&#233;es &#39;MustOverride&#39;.
Les types qui contiennent des membres `MustOverride` doivent être déclarés `MustInherit`.  
  
 **ID d’erreur :** BC31411  
  
### Pour corriger cette erreur  
  
-   Ajoutez le modificateur `MustInherit` au type.  
  
## Voir aussi  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)