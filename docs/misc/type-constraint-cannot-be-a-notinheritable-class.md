---
title: "La contrainte de type ne peut pas &#234;tre une classe &#39;NotInheritable&#39; | Microsoft Docs"
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
  - "vbc32060"
  - "bc32060"
helpviewer_keywords: 
  - "BC32060"
ms.assetid: f45cc0b6-7df1-462a-b3df-c526c143e16a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte de type ne peut pas &#234;tre une classe &#39;NotInheritable&#39;
Une liste de contraintes comprend une classe qui est marquée comme [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable).  
  
 Une liste de contraintes sur un paramètre de type ne peut accepter qu’une seule classe. Un argument de type fourni pour ce paramètre de type doit hériter de cette classe. Ainsi, le paramètre de type ne peut pas accepter de classe *sealed*, ou `NotInheritable`, comme contrainte.  
  
 **ID d’erreur :** BC32060  
  
### Pour corriger cette erreur  
  
-   Si le paramètre de type doit pouvoir hériter de la classe et que vous contrôlez la définition de la classe, supprimez la déclaration `NotInheritable` de la classe.  
  
-   Si la classe doit rester `NotInheritable`, vous ne pouvez pas l’utiliser comme contrainte. Supprimez le nom de la classe de la liste des contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)