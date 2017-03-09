---
title: "Impossible de convertir l’expression de type &#39;&lt;nom_type&gt;&#39; en &#39;Object&#39; ou &#39;ValueType&#39; | Microsoft Docs"
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
  - "bc31394"
  - "vbc31394"
helpviewer_keywords: 
  - "BC31394"
ms.assetid: e6f76257-65bb-4954-99f9-90f282648354
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de convertir l’expression de type &#39;&lt;nom_type&gt;&#39; en &#39;Object&#39; ou &#39;ValueType&#39;
Une expression est évaluée comme étant un type qui ne peut pas être converti \(« boxed »\) par le common language runtime \(CLR\).  
  
 Le *boxing* est le traitement nécessaire à la conversion d’un type en `Object` ou, à l’occasion, en <xref:System.ValueType>. Le common language runtime ne peut pas convertir certains types comme <xref:System.ArgIterator> ou <xref:System.TypedReference>.  
  
 Si vous n’avez pas utilisé `CType` ou `CObj` dans l’instruction contenant cette expression, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] a tenté une conversion implicite qui provoque cette erreur.  
  
 **ID d’erreur :** BC31394  
  
### Pour corriger cette erreur  
  
1.  Recherchez l’expression évaluée comme étant le type cité.  
  
2.  Recherchez la partie de votre instruction qui essaie de convertir le type cité.  
  
3.  Réécrivez l’instruction pour éviter la conversion boxing.  
  
## Voir aussi  
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)