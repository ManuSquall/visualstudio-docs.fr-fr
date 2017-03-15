---
title: "Les classes qui sont g&#233;n&#233;riques ou contenues dans un type g&#233;n&#233;rique ne peuvent pas h&#233;riter d’une classe d’attributs | Microsoft Docs"
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
  - "vbc32074"
  - "BC32074"
helpviewer_keywords: 
  - "BC32074"
ms.assetid: 3552ac98-d86a-4962-9d51-b9a8acc38ea1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les classes qui sont g&#233;n&#233;riques ou contenues dans un type g&#233;n&#233;rique ne peuvent pas h&#233;riter d’une classe d’attributs
Une classe générique ou imbriquée dans un type générique spécifie qu’elle hérite d’une classe d’attributs.  
  
 Visual Basic et .NET Framework ne prennent actuellement pas en charge toute combinaison d’attributs et de types génériques. Cela signifie que les limitations suivantes s’appliquent :  
  
-   Un attribut ne peut pas être un type générique ou être déclaré dans un type générique.  
  
-   Un attribut ne peut pas hériter d’une classe générique et une classe générique ne peut pas non plus hériter d’un attribut.  
  
-   Quand vous appliquez un attribut, vous ne pouvez pas fournir un argument qui correspond à l’un des éléments suivants :  
  
    -   Un type générique.  
  
    -   Un type construit à partir d’un type générique.  
  
    -   Un paramètre de type d’un type conteneur.  
  
    -   Un type construit à partir d’un paramètre de type d’un type conteneur.  
  
 **ID d’erreur :** BC32074  
  
### Pour corriger cette erreur  
  
-   Modifiez la classe de base pour en faire autre chose qu’une classe d’attributs, ou supprimez entièrement l’instruction `Inherits`.  
  
## Voir aussi  
 <xref:System.Attribute>   
 [NOT IN BUILD : Vue d’ensemble des attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)