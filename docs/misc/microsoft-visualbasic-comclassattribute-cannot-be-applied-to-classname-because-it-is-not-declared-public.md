---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; &#39;&lt;nom_classe&gt;&#39;, car il n’est pas d&#233;clar&#233; &#39;Public&#39; | Microsoft Docs"
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
  - "bc32509"
  - "vbc32509"
helpviewer_keywords: 
  - "BC32509"
ms.assetid: ac46851f-53ab-4ce6-87b1-4c4d29508527
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; &#39;&lt;nom_classe&gt;&#39;, car il n’est pas d&#233;clar&#233; &#39;Public&#39;
Une classe est déclarée avec <xref:Microsoft.VisualBasic.ComClassAttribute>, mais sa déclaration ne spécifie pas `Public`.  
  
 Pour pouvoir être utilisée avec COM Interop, une classe .NET Framework doit satisfaire les conditions suivantes :  
  
-   Elle doit être `Public`, tous ses conteneurs doivent être `Public`, et elle doit exposer au moins un membre `Public`.  
  
-   Elle ne doit pas être *abstraite*, autrement dit, elle ne doit pas être déclarée avec `MustInherit`.  
  
-   Elle ne doit pas être générique ni être déclarée dans un type de conteneur générique.  
  
 **ID d’erreur :** BC32509  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Public` à la déclaration de classe.  
  
     ou  
  
-   Si la classe ou son élément conteneur ne peut pas être `Public`, supprimez <xref:Microsoft.VisualBasic.ComClassAttribute> de la déclaration de classe. Vous ne pouvez pas l’exposer à COM.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)