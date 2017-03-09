---
title: "Le type de variable de ressource &#39;Using&#39; ne peut pas &#234;tre de type tableau | Microsoft Docs"
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
  - "vbc36012"
  - "bc36012"
helpviewer_keywords: 
  - "BC36012"
ms.assetid: f98c54b0-6ede-48b6-aa31-438664c219f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type de variable de ressource &#39;Using&#39; ne peut pas &#234;tre de type tableau
Une instruction `Using` spécifie une variable de tableau pour une ressource.  
  
 La classe <xref:System.Array> n’implémente pas l’interface <xref:System.IDisposable>. Le bloc `Using` ne peut donc pas appeler la méthode <xref:System.IDisposable.Dispose%2A> sur une ressource de tableau.  
  
 **ID d’erreur :** BC36012  
  
### Pour corriger cette erreur  
  
-   Utilisez un autre type de ressource système dans le bloc `Using`.  
  
## Voir aussi  
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)   
 [NOTINBUILD Vue d’ensemble des tableaux en Visual Basic](http://msdn.microsoft.com/fr-fr/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)