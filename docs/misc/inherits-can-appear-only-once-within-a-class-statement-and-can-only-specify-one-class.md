---
title: "&#39;Inherits&#39; ne peut appara&#238;tre qu’une seule fois dans une instruction &#39;Class&#39; et ne peut sp&#233;cifier qu’une classe | Microsoft Docs"
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
  - "vbc30121"
  - "bc30121"
helpviewer_keywords: 
  - "BC30121"
ms.assetid: 4ac5b018-5632-4661-8ac6-dbda2f8c4dfe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Inherits&#39; ne peut appara&#238;tre qu’une seule fois dans une instruction &#39;Class&#39; et ne peut sp&#233;cifier qu’une classe
Plusieurs instructions `Inherits` se trouvent dans la même classe ou une instruction `Inherits` spécifie plusieurs classes. Une classe ne peut hériter que d’une seule classe de base.  
  
 **ID d’erreur :** BC30121  
  
### Pour corriger cette erreur  
  
-   Supprimez les instructions `Inherits` supplémentaires et assurez\-vous que l’instruction `Inherits` restante ne spécifie qu’une seule classe de base.  
  
## Voir aussi  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)