---
title: "Les instructions &#39;Implements&#39; doivent suivre toute instruction &#39;Inherits&#39; et pr&#233;c&#233;der toutes les d&#233;clarations dans une classe | Microsoft Docs"
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
  - "bc31053"
  - "vbc31053"
helpviewer_keywords: 
  - "BC31053"
ms.assetid: 8036a1a1-7e31-4c49-b74b-01601a548f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;Implements&#39; doivent suivre toute instruction &#39;Inherits&#39; et pr&#233;c&#233;der toutes les d&#233;clarations dans une classe
Une instruction `Implements` a été détectée à un emplacement non valide.  
  
 **ID d’erreur :** BC31053  
  
### Pour corriger cette erreur  
  
-   Placez les instructions `Implements` immédiatement après les instructions `Inherits`, mais avant toute déclaration. Exemple :  
  
    ```  
    Class Derived Inherits Base Implements One Sub SubOne() Implements One.Method1 ' Add code to implement the method. End Sub End Class  
    ```  
  
## Voir aussi  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)