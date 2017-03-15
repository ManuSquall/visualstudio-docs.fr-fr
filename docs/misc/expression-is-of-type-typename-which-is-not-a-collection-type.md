---
title: "L’expression est du type &#39;&lt;nom_type&gt;&#39;, qui n’est pas un type de collection. | Microsoft Docs"
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
  - "bc32023"
  - "vbc32023"
helpviewer_keywords: 
  - "BC32023"
ms.assetid: d0f151be-6b65-498b-b571-03faf24df0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’expression est du type &#39;&lt;nom_type&gt;&#39;, qui n’est pas un type de collection.
La variable de groupe spécifiée dans une instruction `For Each` n’est pas un objet de collection ni un tableau, et son type n’implémente pas l’interface <xref:System.Collections.IEnumerable>. Le type doit prendre en charge le modèle de conception de collection [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]ou implémenter <xref:System.Collections.IEnumerable>.  
  
 **ID d’erreur :** BC32023  
  
### Pour corriger cette erreur  
  
-   Déclarez la variable de groupe de sorte que son type de classe prenne en charge la conception de collection [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou qu’il implémente <xref:System.Collections.IEnumerable>.  
  
## Voir aussi  
 <xref:System.Collections.IEnumerable>   
 [For Each...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Classe de la collection Visual Basic](http://msdn.microsoft.com/fr-fr/0cb2d1ad-c58d-42c0-8e69-d81f5a15e532)