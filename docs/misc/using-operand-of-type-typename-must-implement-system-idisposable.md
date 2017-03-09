---
title: "L’op&#233;rande &#39;Using&#39; de type &#39;&lt;nom_type&gt;&#39; doit impl&#233;menter &#39;System.IDisposable&#39; | Microsoft Docs"
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
  - "vbc36010"
  - "bc36010"
helpviewer_keywords: 
  - "BC36010"
ms.assetid: ae9ed5d5-68ba-4950-bb7a-61327fa0e7d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rande &#39;Using&#39; de type &#39;&lt;nom_type&gt;&#39; doit impl&#233;menter &#39;System.IDisposable&#39;
Une instruction `Using` spécifie une ressource d’un type qui n’implémente pas l’interface <xref:System.IDisposable>.  
  
 Le but d’un bloc `Using` est de garantir la suppression d’une ressource système dès la sortie du bloc. Pour atteindre ce but, la ressource doit exposer la méthode <xref:System.IDisposable.Dispose%2A> implémentée dans <xref:System.IDisposable>.  
  
 **ID d’erreur :** BC36010  
  
### Pour corriger cette erreur  
  
-   Supprimez la ressource de la liste des ressources de l’instruction `Using` ou remplacez\-la par une ressource qui implémente <xref:System.IDisposable>.  
  
## Voir aussi  
 <xref:System.IDisposable>   
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)