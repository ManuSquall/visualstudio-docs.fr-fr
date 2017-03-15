---
title: "&#39;MyClass&#39; doit &#234;tre suivi de &#39;.&#39; et d’un identificateur. | Microsoft Docs"
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
  - "bc32028"
  - "vbc32028"
helpviewer_keywords: 
  - "BC32028"
ms.assetid: a7e92b54-32b8-4072-9576-632942f05e0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyClass&#39; doit &#234;tre suivi de &#39;.&#39; et d’un identificateur.
`MyClass` n’est pas une véritable variable objet et ne peut pas apparaître seule. Vous pouvez uniquement l’utiliser pour accéder à un membre de l’instance actuelle comme si elle était `NotOverridable` dans la classe de base.  
  
 **ID d'erreur :** BC32028  
  
### Pour corriger cette erreur  
  
1.  Si vous voulez accéder à un membre de classe, spécifiez l’opérateur d’accès aux membres \(`.`\) et un membre de l’instance actuelle après `MyClass`.  
  
2.  Si vous ne voulez pas accéder à un membre de classe, utilisez le mot clé `Me`.  
  
## Voir aussi  
 [MyClass \- supprimer](http://msdn.microsoft.com/fr-fr/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Me](http://msdn.microsoft.com/fr-fr/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)