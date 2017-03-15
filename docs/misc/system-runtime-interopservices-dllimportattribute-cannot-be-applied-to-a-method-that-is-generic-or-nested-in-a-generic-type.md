---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une m&#233;thode g&#233;n&#233;rique ou imbriqu&#233;e dans un type g&#233;n&#233;rique | Microsoft Docs"
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
  - "vbc31526"
  - "bc31526"
helpviewer_keywords: 
  - "BC31526"
ms.assetid: 6f153808-1945-4c99-85ae-8bd3b35ee5a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une m&#233;thode g&#233;n&#233;rique ou imbriqu&#233;e dans un type g&#233;n&#233;rique
Une procédure est déclarée avec <xref:System.Runtime.InteropServices.DllImportAttribute>, mais la procédure est générique ou elle est contenue dans une classe ou structure générique.  
  
 Le Common Language Runtime \(CLR\) reconnaît cet attribut et sa propriété <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> comme désignant une procédure de remplacement définie dans une bibliothèque de liens dynamiques \(DLL\) non gérée en dehors du .NET Framework. Quand le code appelle la procédure à laquelle <xref:System.Runtime.InteropServices.DllImportAttribute> est appliqué, le Common Language Runtime appelle plutôt la procédure non gérée désignée.  
  
 Étant donné que les plateformes non gérées en dehors du .NET Framework ne reconnaissent pas les types génériques, vous ne pouvez pas interagir avec elles à l’aide de types génériques.  
  
 **ID d’erreur :** BC31526  
  
### Pour corriger cette erreur  
  
-   Si la procédure et son conteneur n’ont pas besoin d’être génériques, supprimez les clauses `Of` pour qu’ils ne soient pas génériques.  
  
-   Si la procédure ou son conteneur ont besoin d’être génériques, supprimez <xref:System.Runtime.InteropServices.DllImportAttribute> de la déclaration de cette procédure.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)