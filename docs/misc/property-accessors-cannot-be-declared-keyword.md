---
title: "Les accesseurs de propri&#233;t&#233; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;mot_cl&#233;&gt;&#39;. | Microsoft Docs"
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
  - "vbc31099"
  - "bc31099"
helpviewer_keywords: 
  - "BC31099"
ms.assetid: d6f3b989-39b9-4c47-995a-bd83ec03d7b8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les accesseurs de propri&#233;t&#233; ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;mot_cl&#233;&gt;&#39;.
Une déclaration de procédure `Get` ou `Set` comprend un mot clé qui n’est pas valide sur une procédure de propriété.  
  
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) et [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) autorisent uniquement un modificateur d’accès \(`Public`, `Protected`, `Friend`, `Protected Friend`, `Private`\).  
  
 **ID d’erreur :** BC31099  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé non valide de l’instruction `Get` ou `Set`.  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)