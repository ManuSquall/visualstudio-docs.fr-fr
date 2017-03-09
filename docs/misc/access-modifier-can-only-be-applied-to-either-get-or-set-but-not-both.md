---
title: "Le modificateur d’acc&#232;s ne peut &#234;tre appliqu&#233; qu’&#224; &#39;Get&#39; ou &#39;Set&#39;, mais pas aux deux | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le modificateur d’acc&#232;s ne peut &#234;tre appliqu&#233; qu’&#224; &#39;Get&#39; ou &#39;Set&#39;, mais pas aux deux
Une déclaration de propriété spécifie les niveaux d’accès dans [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement), [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) et [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Vous pouvez toujours spécifier un niveau d’accès pour la propriété. De plus, vous pouvez spécifier un niveau d’accès différent pour l’une de ses procédures de propriété \(`Get` ou `Set`\), à condition qu’il soit plus restrictif que le niveau d’accès de la propriété. Vous ne pouvez pas spécifier de niveaux d’accès pour les deux procédures de propriété.  
  
 **ID d’erreur :** BC31101  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur d’accès de l’instruction `Get` ou `Set`.  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)