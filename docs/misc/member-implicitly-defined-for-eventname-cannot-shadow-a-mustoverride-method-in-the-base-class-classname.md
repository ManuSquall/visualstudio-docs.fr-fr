---
title: "&#39;&lt;membre&gt;&#39;, implicitement d&#233;fini pour &#39;&lt;nom_&#233;v&#233;nement&gt;&#39;, ne peut pas masquer une m&#233;thode &#39;MustOverride&#39; dans la &lt;classe&gt; de base &#39;&lt;nom_classe&gt;&#39; | Microsoft Docs"
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
  - "vbc31413"
  - "bc31413"
helpviewer_keywords: 
  - "BC31413"
ms.assetid: 071706ce-a394-48b6-9afa-751cb50b2576
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membre&gt;&#39;, implicitement d&#233;fini pour &#39;&lt;nom_&#233;v&#233;nement&gt;&#39;, ne peut pas masquer une m&#233;thode &#39;MustOverride&#39; dans la &lt;classe&gt; de base &#39;&lt;nom_classe&gt;&#39;
L’événement spécifié déclare implicitement un membre avec le même nom qu’une méthode déclarée avec le modificateur `MustOverride`.  
  
 **ID d’erreur :** BC31413  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur `MustOverride` de la méthode dans la classe de base ou donnez à la propriété ou méthode un nom unique.  
  
## Voir aussi  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)