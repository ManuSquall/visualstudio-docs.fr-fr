---
title: "Le caract&#232;re de continuation de ligne &#39;_&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’au moins un espace blanc et doit &#234;tre le dernier caract&#232;re de la ligne | Microsoft Docs"
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
  - "vbc30999"
  - "bc30999"
helpviewer_keywords: 
  - "BC30999"
ms.assetid: 32caf62f-52e4-4acd-b40f-5af65e42e643
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le caract&#232;re de continuation de ligne &#39;_&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’au moins un espace blanc et doit &#234;tre le dernier caract&#232;re de la ligne
Vous pouvez utiliser le caractère de continuation de ligne, qui est un trait de soulignement \(\_\), pour répartir une longue ligne de code sur plusieurs lignes dans votre fichier. Le trait de soulignement doit être immédiatement précédé d’un espace et immédiatement suivi d’un terminateur de ligne \(retour chariot\). Exemple :  
  
```  
Dim books As XDocument = _ XDocument.Load(My.Application.Info.DirectoryPath & _ "\..\..\Data\books.xml")  
```  
  
 **ID d’erreur :** BC30999  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous que le caractère de continuation de ligne \(\_\) est le dernier caractère d’une ligne de code.  
  
2.  Assurez\-vous qu’il existe un espace avant le caractère de continuation de ligne, qui le sépare de tout autre code sur la ligne.  
  
## Voir aussi  
 [Procédure : diviser et combiner des instructions dans le code](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)