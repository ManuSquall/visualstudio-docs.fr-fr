---
title: "Le nom du membre de type anonyme doit &#234;tre pr&#233;c&#233;d&#233; d’un point | Microsoft Docs"
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
  - "vbc36575"
  - "bc36575"
helpviewer_keywords: 
  - "BC36575"
ms.assetid: b87be29e-39f0-4830-9969-608d71137e3e
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le nom du membre de type anonyme doit &#234;tre pr&#233;c&#233;d&#233; d’un point
Dans la liste d’initialiseurs d’objet d’une déclaration de type anonyme, un nouveau nom de membre auquel une valeur est assignée doit être précédé d’un point. L’exemple suivant montre deux déclarations, l’une valide et l’autre non valide :  
  
```vb#  
' Valid.  
Dim instanceName1 = New With {.memberName = 10}  
' Invalid declaration that causes this error.  
' Dim instanceName2 = New With {memberName = 10}  
```  
  
 **ID d’erreur :** BC36575  
  
### Pour corriger cette erreur  
  
-   Ajoutez un point avant le nom du membre.  
  
## Voir aussi  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)