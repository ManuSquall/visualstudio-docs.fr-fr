---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une classe g&#233;n&#233;rique ou imbriqu&#233;e dans un type g&#233;n&#233;rique | Microsoft Docs"
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
  - "vbc31527"
  - "bc31527"
helpviewer_keywords: 
  - "BC31527"
ms.assetid: ea125bff-d020-4933-b277-6e24943eea88
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une classe g&#233;n&#233;rique ou imbriqu&#233;e dans un type g&#233;n&#233;rique
Une classe est déclarée avec <xref:Microsoft.VisualBasic.ComClassAttribute>, mais elle est générique ou contenue dans une classe ou une structure générique.  
  
 Pour pouvoir être utilisée avec COM Interop, une classe .NET Framework doit satisfaire les conditions suivantes :  
  
-   Elle doit être `Public`, tous ses conteneurs doivent être `Public`, et elle doit exposer au moins un membre `Public`.  
  
-   Elle ne doit pas être *abstraite*, autrement dit, elle ne doit pas être déclarée avec `MustInherit`.  
  
-   Elle ne doit pas être générique ni être déclarée dans un type de conteneur générique.  
  
 **ID d’erreur :** BC31527  
  
### Pour corriger cette erreur  
  
-   Modifiez la déclaration de la classe de sorte qu’elle ne soit pas générique et vérifiez que son élément conteneur n’est pas générique.  
  
     ou  
  
-   Si la classe ou son élément conteneur doit être générique, supprimez <xref:Microsoft.VisualBasic.ComClassAttribute> de la déclaration de classe. Vous ne pouvez pas l’exposer à COM.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)