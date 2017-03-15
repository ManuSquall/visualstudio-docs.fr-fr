---
title: "&#39;MyBase&#39; doit &#234;tre suivi de &#39;.&#39; et d’un identificateur | Microsoft Docs"
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
  - "bc32027"
  - "vbc32027"
helpviewer_keywords: 
  - "BC32027"
ms.assetid: 39e5512c-ef1e-46a3-a96c-277ea24bfee2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyBase&#39; doit &#234;tre suivi de &#39;.&#39; et d’un identificateur
`MyBase` n’est pas une véritable variable objet et ne peut pas apparaître seule. Vous pouvez uniquement l’utiliser pour accéder à un membre de la classe de base de l’instance actuelle.  
  
 **ID d’erreur :** BC32027  
  
### Pour corriger cette erreur  
  
-   Si vous voulez accéder à un membre, spécifiez l’opérateur d’accès aux membres \(.\) et un membre de la classe de base après `MyBase`.  
  
-   Si vous ne voulez pas accéder à un membre, déclarez, puis initialisez une instance de la classe de base, ou supprimez la référence à `MyBase`.  
  
## Voir aussi  
 [MyBase \- supprimer](http://msdn.microsoft.com/fr-fr/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)