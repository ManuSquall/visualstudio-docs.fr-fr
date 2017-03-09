---
title: "&#39;&lt;mot_cl&#233;&gt;&#39; n’est pas valide dans une structure | Microsoft Docs"
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
  - "bc30044"
  - "vbc30044"
helpviewer_keywords: 
  - "BC30044"
ms.assetid: 252510cf-e084-47e4-9592-4aa8f94fabe4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;mot_cl&#233;&gt;&#39; n’est pas valide dans une structure
Les structures sont des types valeur, et non des types référence. Les mots clés `Me`, `MyClass` et `MyBase` n’ont pas de sens dans une structure, car celle\-ci n’est pas une instance créée à partir d’une classe.  
  
 **ID d’erreur :** BC30044  
  
### Pour corriger cette erreur  
  
-   Remplacez la structure par une classe ou supprimez le mot clé de la procédure.  
  
## Voir aussi  
 [Me](http://msdn.microsoft.com/fr-fr/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass \- supprimer](http://msdn.microsoft.com/fr-fr/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [MyBase \- supprimer](http://msdn.microsoft.com/fr-fr/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)