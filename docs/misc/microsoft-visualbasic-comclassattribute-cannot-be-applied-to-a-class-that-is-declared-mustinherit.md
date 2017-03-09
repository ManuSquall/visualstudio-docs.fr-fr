---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une classe qui est d&#233;clar&#233;e &#39;MustInherit&#39;. | Microsoft Docs"
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
  - "BC32508"
  - "vbc32508"
helpviewer_keywords: 
  - "BC32508"
ms.assetid: c8af606d-f448-4703-98df-e594fd511f92
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une classe qui est d&#233;clar&#233;e &#39;MustInherit&#39;.
Une classe est déclarée avec <xref:Microsoft.VisualBasic.ComClassAttribute>, mais sa déclaration spécifie `MustInherit`.  
  
 Pour pouvoir être utilisée avec COM Interop2, une classe .NET Framework doit répondre aux exigences suivantes :  
  
-   Elle doit être `Public`, tous ses conteneurs doivent être `Public`, et elle doit exposer au moins un membre `Public`.  
  
-   Elle ne doit pas être *abstraite*, autrement dit, elle ne doit pas être déclarée avec `MustInherit`.  
  
-   Elle ne doit pas être générique ni déclarée dans un type de conteneur générique.  
  
 **ID d’erreur :** BC32508  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `MustInherit` de la déclaration de classe.  
  
     ou  
  
-   Si la classe ou son élément conteneur doivent être génériques, supprimez <xref:Microsoft.VisualBasic.ComClassAttribute> de la déclaration de classe. Vous ne pouvez pas l’exposer à COM.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)