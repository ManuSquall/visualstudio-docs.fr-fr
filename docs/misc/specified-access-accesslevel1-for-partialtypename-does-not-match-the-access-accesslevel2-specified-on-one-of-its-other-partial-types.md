---
title: "L’acc&#232;s sp&#233;cifi&#233; &#39;&lt;niveau_acc&#232;s1&gt;&#39; pour &#39;&lt; nom_type_partiel&gt;&#39; ne correspond pas &#224; l’acc&#232;s &#39;&lt;niveau_acc&#232;s2&gt;&#39; sp&#233;cifi&#233; pour l’un de ses autres types partiels | Microsoft Docs"
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
  - "vbc30925"
  - "BC30925"
helpviewer_keywords: 
  - "BC30925"
ms.assetid: aabe0f4a-dc02-4828-a837-20cd47a7bd43
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’acc&#232;s sp&#233;cifi&#233; &#39;&lt;niveau_acc&#232;s1&gt;&#39; pour &#39;&lt; nom_type_partiel&gt;&#39; ne correspond pas &#224; l’acc&#232;s &#39;&lt;niveau_acc&#232;s2&gt;&#39; sp&#233;cifi&#233; pour l’un de ses autres types partiels
Une classe ou une structure est définie dans plusieurs déclarations partielles avec des spécifications de niveau d’accès incompatibles.  
  
 Quand vous divisez la définition d’une classe ou d’une structure en plusieurs déclarations partielles, le compilateur considère le type comme l’union de toutes ses déclarations partielles. Cela s’applique non seulement aux membres, mais aussi à l’implémentation, à l’héritage et au niveau d’accès.  
  
 Vous ne pouvez pas mélanger des niveaux d’accès dans la définition d’une classe ou d’une structure. Même la combinaison `Protected Friend` n’est autorisée que lorsque les mots clés sont contigus dans la même instruction de déclaration.  
  
 **ID d’erreur :** BC30925  
  
### Pour corriger cette erreur  
  
-   Décidez du niveau d’accès de la classe et supprimez les spécifications de niveau d’accès incompatibles.  
  
## Voir aussi  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [NOT IN BUILD : Classes : modèles d’objets](http://msdn.microsoft.com/fr-fr/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Structures](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)