---
title: "Les propri&#233;t&#233;s &#39;WriteOnly&#39; ne peuvent pas avoir un modificateur d’acc&#232;s pour &#39;Set&#39;. | Microsoft Docs"
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
  - "bc31104"
  - "vbc31104"
helpviewer_keywords: 
  - "BC31104"
ms.assetid: d1ac04a8-e436-4f3e-8d71-fc4569b35fcd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les propri&#233;t&#233;s &#39;WriteOnly&#39; ne peuvent pas avoir un modificateur d’acc&#232;s pour &#39;Set&#39;.
Une déclaration de propriété `WriteOnly` spécifie les niveaux d’accès dans [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) et dans [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Vous pouvez toujours spécifier un niveau d’accès pour la propriété. De plus, vous pouvez spécifier un niveau d’accès différent pour l’une de ses procédures de propriété \(`Get` ou `Set`\), à condition qu’il soit plus restrictif que le niveau d’accès de la propriété. Vous ne pouvez pas spécifier des niveaux d’accès pour les deux procédures de propriété.  
  
 **ID d’erreur :** BC31104  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur d’accès dans l’instruction `Set`. Il représente l’intégralité de la propriété `WriteOnly` et vous ne pouvez pas avoir deux niveaux d’accès pour la propriété.  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)