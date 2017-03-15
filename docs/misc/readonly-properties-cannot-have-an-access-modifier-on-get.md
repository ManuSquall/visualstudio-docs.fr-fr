---
title: "Les propri&#233;t&#233;s &#39;ReadOnly&#39; ne peuvent pas avoir un modificateur d’acc&#232;s pour &#39;Get&#39; | Microsoft Docs"
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
  - "vbc31105"
  - "bc31105"
helpviewer_keywords: 
  - "BC31105"
ms.assetid: 54066d8e-eb22-4b99-bb18-45afe61d3b33
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les propri&#233;t&#233;s &#39;ReadOnly&#39; ne peuvent pas avoir un modificateur d’acc&#232;s pour &#39;Get&#39;
Une déclaration de propriété `ReadOnly` spécifie les niveaux d’accès dans [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) et [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement).  
  
 Vous pouvez toujours spécifier un niveau d’accès pour la propriété. De plus, vous pouvez spécifier un niveau d’accès différent pour l’une de ses procédures de propriété \(`Get` ou `Set`\), à condition qu’il soit plus restrictif que le niveau d’accès de la propriété. Vous ne pouvez pas spécifier des niveaux d’accès pour les deux procédures de propriété.  
  
 **ID d’erreur :** BC31105  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur d’accès de l’instruction `Get`. Il représente l’intégralité de la propriété `ReadOnly` et vous ne pouvez pas avoir deux niveaux d’accès pour la propriété.  
  
## Voir aussi  
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)