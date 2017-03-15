---
title: "L’argument nomm&#233; ne peut pas correspondre &#224; un param&#232;tre ParamArray | Microsoft Docs"
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
  - "bc30587"
  - "vbc30587"
helpviewer_keywords: 
  - "BC30587"
ms.assetid: aff179af-96f2-4157-971e-881d8e08f5f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’argument nomm&#233; ne peut pas correspondre &#224; un param&#232;tre ParamArray
Vous avez fourni un argument nommé \(spécifié avec le nom déclaré de l’argument suivi de deux\-points et d’un signe égal, puis de la valeur de l’argument\) ; cependant, vous ne pouvez pas passer un tableau de paramètres par nom. Quand vous appelez la procédure, vous indiquez un nombre indéfini d’arguments séparés par des virgules pour le tableau de paramètres, et le compilateur ne peut pas associer plusieurs arguments à un seul nom.  
  
 **ID d’erreur :** BC30587  
  
### Pour corriger cette erreur  
  
-   Passez l’argument par position, plutôt que par nom.  
  
## Voir aussi  
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)